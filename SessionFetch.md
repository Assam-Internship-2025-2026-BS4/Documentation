## Session fetch

This API fetches the current authentication status for a given authRequestId.
It is used for polling during WhatsApp and QR authentication flows to determine whether the session is PENDING, APPROVED, REJECTED, or EXPIRED.


```plaintext
GET /api/v1/auth/session/fetch
```

Supported attributes:

| Attribute                | Type     | Required | Description           |
|--------------------------|----------|----------|-----------------------|
| `authRequestId`              | string | Y      | Unique authentication request identifier |
| `mobileNo`              | string | Y       | Registered 10-digit mobile number|


### Request Json
```json
{
   "authRequestId": "AUTH-REQ-4567",
  "mobileNo": "9876543210"
}
```


If successful, returns [`200`](rest/troubleshooting.md#status-codes) and the following
response attributes:

| Attribute                | Type     | Description           |
|--------------------------|----------|-----------------------|
| `status`              | string | Indicates whether the request is SUCCESS or FAILED|
| `authStatus`              | string | Current authentication state (WA_PENDING / OTP_SENT / APPROVED / REJECTED / EXPIRED) |
`expiryTime`              | integer | Remaining validity time in seconds |


Example request:

```shell
curl --location --request POST 'http://localhost:8080/api/v2/auth/session/fetch' \
--header 'Content-Type: application/json' \
--data-raw '{
  "authRequestId": "AUTH-REQ-4567",
  "mobileNo": "9876543210"
}'
```

Example response (Pending):

```json
{
{
  "status": "SUCCESS",
  "authStatus": "WA_PENDING",
  "expiryTime": 45
}
}
```
Example response (Approved):
```json
{
{
  "status": "SUCCESS",
  "authStatus": "APPROVED",
  "expiryTime": 0
}
}
```