## User identify

This API identifies if user exists in system with WhatsApp banking enable.


```plaintext
POST /api/v1/user/details/identify
```

Supported attributes:

| Attribute                | Type     | Required | Description           |
|--------------------------|----------|----------|-----------------------|
| `mobileNo`              | string | Y      | Registered 10-digit mobile number |
| `dob`              | date | C       | Format `dd-MM-YYYY`. Optional is `pan` present |
| `pan`              | string | C       | Format `ABCDE1234Z`. Optional is `dob` present |

### Request Json
```json
{
  "mobileNo": "9876543210",
  "dob": "31-12-2000"
}
```
OR
```json
{
  "mobileNo": "9876543210",
  "pan": "ABCDE1234Z"
}
```

If successful, returns [`200`](rest/troubleshooting.md#status-codes) and the following
response attributes:

| Attribute                | Type     | Description           |
|--------------------------|----------|-----------------------|
| `userExists`              | boolean | Indicates whether user exists|
| `hasWhatsAppEnabled`              | boolean | Indicates whether WhatsApp Banking is enabled |
`authRequestId`              | string | Unique authentication request identifier for this login attempt |


Example request:

```shell
curl --location --request POST 'http://localhost:8080/api/v1/user/identify' \
--header 'Content-Type: application/json' \
--data-raw '{
  "mobileNo": "9876543210",
  "pan": "ABCDE1234Z"
}'
```

Example response:

```json
{
 "userExists": true,
"hasWhatsAppEnabled": true,
 "authRequestId": "AUTH-REQ-4567"
}
```