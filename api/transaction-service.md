# Transaction Service

## `POST /transactions/deposit`

입금

### Request Body

```json
{
    "accountId": 10,
    "amount": 50000
}
```

### Response Body

201 Created

```json
{
    "transactionId": 100,
    "type": "DEPOSIT",
    "fromAccountId": null,
    "toAccountId": 10,
    "amount": 50000,
    "status": "SUCCESS",
    "createdAt": "2026-08-13T17:00:00"
}
```

- `transactionId` (integer)
- `type` (string)
- `fromAccountId` (integer)
- `toAccountId` (integer)
- `amount` (long)
- `status` (string)
- `createdAt` (string)

## `POST /transactions/withdraw`

출금

### Request Body

```json
{
    "accountId": 10,
    "amount": 30000
}
```

### Response Body

201 Created

```json
{
    "transactionId": 101,
    "type": "WITHDRAW",
    "fromAccountId": 10,
    "toAccountId": null,
    "amount": 30000,
    "status": "SUCCESS",
    "createdAt": "2026-08-13T17:05:00"
}
```

## `POST /transactions/transfer`

이체

### Request Body

```json
{
    "fromAccountId": 10,
    "toAccountId": 20,
    "amount": 30000
}
```

### Response Body

201 Created

```json
{
    "transactionId": 102,
    "type": "TRANSFER",
    "fromAccountId": 10,
    "toAccountId": 20,
    "amount": 30000,
    "status": "SUCCESS",
    "createdAt": "2026-08-13T17:10:00"
}
```

## `GET /transactions/{transactionId}`

거래 상세 조회

### Request Body

없음

### Response Body

200 OK

```json
{
    "transactionId": 102,
    "type": "TRANSFER",
    "fromAccountId": 10,
    "toAccountId": 20,
    "amount": 30000,
    "status": "SUCCESS",
    "createdAt": "2026-08-13T17:10:00"
}
```

## `GET /transactions?accountId={accountId}`

계좌별 거래 내역

### Request Body

없음

### Response Body

200 OK

```json
[
    {
        "transactionId": 100,
        "type": "DEPOSIT",
        "fromAccountId": null,
        "toAccountId": 10,
        "amount": 50000,
        "status": "SUCCESS",
        "createdAt": "2026-08-13T17:00:00"
    },
    {
        "transactionId": 102,
        "type": "TRANSFER",
        "fromAccountId": 10,
        "toAccountId": 20,
        "amount": 30000,
        "status": "SUCCESS",
        "createdAt": "2026-08-13T17:10:00"
    }
]
```