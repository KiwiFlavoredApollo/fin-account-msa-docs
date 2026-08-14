# Account Service

## `POST /api/accounts`

계좌 개설

### Request Body

```json
{
    "ownerName": 1,
    "password": "1234"
}
```

### Response Body

201 Created

```json
{
    "accountId": 10,
    "accountNumber": "110123456789",
    "ownerName": 1,
    "balance": 0,
    "status": "ACTIVE"
}
```

- `accountId` (integer)
- `accountNumber` (string)
- `ownerName` (integer)
- `balance` (long)
- `status` (string) 
  - `Active`
  - `CLOSED`
  - `FROZEN`

## `GET /api/accounts/{accountId}`

계좌 상세 조회

### Request Body

없음

### Response Body

200 OK

```json
{
    "accountId": 10,
    "accountNumber": "110123456789",
    "ownerName": 1,
    "balance": 100000,
    "status": "ACTIVE"
}

