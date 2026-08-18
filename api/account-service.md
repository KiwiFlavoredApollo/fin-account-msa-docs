# Account Service

## `POST /api/accounts`

계좌 개설

### Request Body

```json
{
    "ownerName": "John Doe",
    "password": "1234"
}
```

### Response Body

201 Created

```json
{
    "accountId": 10,
    "accountNumber": "110123456789",
    "ownerName": "John Doe",
    "balance": 0,
    "status": "ACTIVE"
}
```

- `accountId` (integer)
- `accountNumber` (string)
- `ownerName` (string)
- `balance` (long)
- `status` (string)
  - `ACTIVE`
  - `CLOSED`
  - `FROZEN`

---

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
    "ownerName": "John Doe",
    "balance": 100000,
    "status": "ACTIVE"
}
```


---

## `POST /api/auth/login`

로그인

### Request Body

```json
{
    "accountNumber": "110123456789",
    "password": "1234"
}
```

### Response Body

200 OK

```json
{
    "accountId": 10,
    "accessToken": "eyJ..."
}
```

- `accountId` (integer)
- `accessToken` (string)
