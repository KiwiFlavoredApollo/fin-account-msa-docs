# Account Service

## `POST /accounts`

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

## `GET /accounts/{accountId}`

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

## `PATCH /accounts/{accountId}`

계좌 정보를 수정합니다. 현재 계좌 잔액만 변경할 수 있습니다.

### Request Body

```json
{
  "balance": 50000
}
```

### Response Body

```json
{
    "accountId": 10,
    "accountNumber": "110123456789",
    "ownerName": "John Doe",
    "balance": 50000,
    "status": "ACTIVE"
}
```

---

## `POST /auth/login`

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
