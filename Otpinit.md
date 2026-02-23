## OTP Authentication Init

This API initiates OTP-based authentication for users who are not eligible for WhatsApp authentication or who choose OTP as a fallback option. It generates and sends a One-Time Password (OTP) to the user’s registered mobile number and sets the authentication state to OTP_SENT.


```plaintext
POST /api/v1/auth/otp/init
```

Supported attributes:

| Attribute                | Type     | Required | Description           |
|--------------------------|----------|----------|-----------------------|
| `authRequestId`              | string | Y      | Unique authentication request identifier generated during identity verification |
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
| `authStatus`              | string | Authentication state (OTP_SENT) |
`expiryTime`              | integer | OTP validity duration in seconds |


Example request:

```shell
curl --location --request POST 'http://localhost:8080/api/v1/auth/otp/init' \
--header 'Content-Type: application/json' \
--data-raw '{
  "authRequestId": "AUTH-REQ-4567",
  "mobileNo": "9876543210"
}'
```

Example response: 

```json
{
{
  "status": "SUCCESS",
  "authStatus": "OTP_SENT",
  "expiryTime": 120
}
}
```
