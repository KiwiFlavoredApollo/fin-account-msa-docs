# Notification Service

> Transaction Service가 발행하는 `TransactionEvent`(Avro, Kafka)를 소비하여 알림을 생성/저장한다. 아래 API는 저장된 알림의 조회/읽음 처리를 위한 REST 인터페이스.

## `GET /api/notifications?userId={userId}`

사용자별 알림 목록 조회

### Request Body

없음

### Response Body

200 OK

```json
[
    {
        "notificationId": 1,
        "userId": "user01",
        "transactionId": 100,
        "transactionType": "DEPOSIT",
        "fromAccountId": null,
        "toAccountId": 10,
        "amount": 50000,
        "status": "SENT",
        "isRead": false,
        "createdAt": "2026-08-13T17:00:05"
    },
    {
        "notificationId": 2,
        "userId": "user01",
        "transactionId": 102,
        "transactionType": "TRANSFER",
        "fromAccountId": 10,
        "toAccountId": 20,
        "amount": 30000,
        "status": "SENT",
        "isRead": true,
        "createdAt": "2026-08-13T17:10:03"
    }
]
```

- `notificationId` (integer)
- `userId` (string)
- `transactionId` (integer)
- `transactionType` (string)
- `fromAccountId` (integer)
- `toAccountId` (integer)
- `amount` (long)
- `status` (string)
  - `PENDING`
  - `SENT`
  - `FAILED`
- `isRead` (boolean)
- `createdAt` (string)

## `GET /api/notifications/{notificationId}`

알림 상세 조회

### Request Body

없음

### Response Body

200 OK

```json
{
    "notificationId": 2,
    "userId": "user01",
    "transactionId": 102,
    "transactionType": "TRANSFER",
    "fromAccountId": 10,
    "toAccountId": 20,
    "amount": 30000,
    "status": "SENT",
    "isRead": true,
    "createdAt": "2026-08-13T17:10:03"
}
```

## `PATCH /api/notifications/{notificationId}/read`

알림 읽음 처리

### Request Body

없음

### Response Body

200 OK

```json
{
    "notificationId": 2,
    "isRead": true
}
```
