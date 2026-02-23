## Session Approve

This API approves an authentication session after the user confirms login (used in QR authentication flow from the Mobile Banking App). It updates the authentication state from PENDING to APPROVED.


```plaintext
POST /api/v1/auth/session/approve
```

Supported attributes:

| Attribute                | Type     | Required | Description           |
|--------------------------|----------|----------|-----------------------|
| `authRequestId`              | string | Y      | Unique authentication request identifier |
| `mobileNo`              | string | Y       | Registered 10-digit mobile number |

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
| `status`              | string | Indicates whether the operation is SUCCESS or FAILED|
| `authStatus`              | string | Updated authentication state (APPROVED) |
`authRequestId`              | string | Authentication request identifier |


Example request:

```shell
curl --location --request POST 'http://localhost:8080/api/v1/auth/session/approve' \
--header 'Content-Type: application/json' \
--data-raw '{
  "authRequestId": "AUTH-REQ-4567",
  "mobileNo": "9876543210"
}'
```

Example response:

```json
{
  "status": "SUCCESS",
  "authStatus": "APPROVED",
  "authRequestId": "AUTH-REQ-4567"
}
```