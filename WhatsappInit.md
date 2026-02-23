## WhatsApp Initiate

This API initiates WhatsApp-based authentication for users who have WhatsApp banking enabled. It sends an approval request to the user’s registered WhatsApp number and sets the authentication status to WA_PENDING.


```plaintext
POST /api/v1/auth/wa/init
```

Supported attributes:

| Attribute                | Type     | Required | Description           |
|--------------------------|----------|----------|-----------------------|
| `authRequestId`              | string | Y      | Unique authentication request identifier generated during identity verification |
| `mobileNo`              | string | Y      | Registered 10-digit mobile number|


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
| `status`              | string | Indicates WhatsApp authentication has been initiated. Value: WA_INITIATED|
| `authStatus`              | string | Authentication state (WA_PENDING)|
`expiryTime` | integer | Validity duration (in seconds) for approval(e.g., 30). |


Example request:

```shell
curl --location --request POST 'http://localhost:8080/api/v1/auth/wa/init' \
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
  "authStatus": "WA_PENDING",
  "expiryTime": 60
}

```