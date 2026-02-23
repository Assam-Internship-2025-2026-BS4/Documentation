## User Details Fetch

This API fetches basic user details after successful authentication.
It is invoked only when the authentication status is APPROVED.


```plaintext
POST /api/v1/user/details/fetch
```

Supported attributes:

| Attribute                | Type     | Required | Description           |
|--------------------------|----------|----------|-----------------------|
| `authRequestId`              | string | Y      | Unique authentication request identifier with status APPROVED|
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
| `customerId`              | string | Unique customer identifier |
`customerName`              | string | Full name of the authenticated user |
`lastLoginTime`              | string | Timestamp of previous successful login |
`sessionId`              | string | Newly generated session ID for dashboard access |


Example request:

```shell
curl --location --request POST 'http://localhost:8080/api/v1/user/details/fetch' \
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
  "customerId": "CUST10231",
  "customerName": "Shubam Bonik",
  "lastLoginTime": "2025-02-20T10:15:30Z",
  "sessionId": "SESSION-892734"
}
}
```
