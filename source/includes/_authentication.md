
# Authentication 

<aside class="notice">
Authentication for the SIERA API will be adding an <a href="https://auth0.com/docs/authorization/flows/authorization-code-flow">authorization code flow</a> in the future, and the <a href="https://oauth.net/2/grant-types/password/">password grant type</a> (Bearer token) deprecated. Users of this login mechanism will be informed with notice before the change occurs.
</aside>

There are 2 options for authentication when using the SIERA API: 

1. Use [Basic Authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) and insert encoded credentials in the header of the request.
2. Use the [login endpoint](#authentication-login) to obtain a Bearer token which is then inserted into the header of the request.

## Basic Authentication

To use [Basic Authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) simply take the username and password and form a string joined by a single colon (:). This string is then encoded into Base64, and inserted into the **Authorization** header with the word Basic before it.

As an example, if the user **testuser@companyabc.com** with password **SekaiFleur@PalomaSchnee** combines these credentials (testuser@companyabc.com:SekaiFleur@PalomaSchnee), and then encodes that into [Base64](https://en.wikipedia.org/wiki/Base64) we get the string **dGVzdHVzZXJAY29tcGFueWFiYy5jb206U2VrYWlGbGV1ckBQYWxvbWFTY2huZWU=**. This can then be inserted into the header to authenticate each request as 

`Authorization: Basic dGVzdHVzZXJAY29tcGFueWFiYy5jb206U2VrYWlGbGV1ckBQYWxvbWFTY2huZWU=`

[Basic Authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) is required for access to the API via Excel and Power BI, and secured primarily using [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security). [Owasp Security guidelines](https://cheatsheetseries.owasp.org/cheatsheets/Web_Service_Security_Cheat_Sheet.html#user-authentication) recognise it discloses secrets in plain text (base64 encoded) and recommends against its use where possible, but accepts that where necessary [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security) must be used.

## Get bearer token
```shell
```

> POST /api/v1/authentication/login

```shell
curl POST https://api.sieraglobal.com/api/v1/authentication/login \
  -H 'accept: */*' \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {
    "email": "testuser@companyabc.com",
    "password": "SekaiFleur@PalomaSchnee"
  }
```

> Response (200)

```json
{
  "token": "eyJhbGciOiJBMTI4S1ciLCJlbmMiOiJBMTI4Q0J1LUhTMjU2IiwidHlwIjoiSldUIn0.Fb5jEJb9zokguyPFyha4YFwguTMe8zChZ9isrCgI5r8o1Lfk0q_few.c02C5x7NTPEzerSoc8Rghw.lRWHsUJSm5W-NR8sfg8756MVDyA66dy_Ymet78bmNarFXEbvUYmOjCg1maDrUDmUWvWvi7_OYjAz7CgiHs7btIStaBklGX1nxIh60c_8DpA3ustSTYjmnrdSlPDJ9gENeewDIHWCjTgz1MjKhE42mdeZ6xFrxu7JFcc23m4J31kcbR8wL92MZChb_issdqhXc8CnZzYwP-PZ3wCWgsn63gc_-yQ5Y5cz9a1Sqtcbx7P2fw7PDkQi1SvVRcL7XQXhGvNbuyB21sxYYTjdcatoY6wAAGGF_UcTMmhoDV6dziELEq7pGKkwmFXZP38rZs_CBM7vtBKtWY_ESX1_C7SmrucQJRa4sdrsbHA98-q1lQkoK-ZJnl3wZRoJ6xslEicxj9bpuRL20ZRd-kmXwPBSY0ldTcvkLHhKGrN7vMBmbmQDcnps2iH64BOWi-O-YKupGK70eO-YmYLZ3T85nlbttg.Mo9LyvjYVYzN6cl258MXrQ",
  "expiration": "2021-11-27T15:20:47Z",
  "lockoutTimeRemaining": null,
  "maxRetriesExceeded": 0,
  "previousAccessFailedCount": 0
}
```

> Response (401)

```json
{
  "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
  "title": "Unauthorized",
  "status": 401,
  "traceId": "00-67cb3e28086d1b4198cf96e8d37b495a-e76f80e2f9c51f4b-00"
}
```

> Response (403) - Locked

```json
{
  "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
  "title": "Locked",
  "detail": 45,
  "status": 403,
  "traceId": "00-67cb3e28086d1b4198cf96e8d37b495a-e76f80e2f9c51f4b-00"
}
```

> Response (403) - Password Expiry

```json
{
  "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
  "title": "Expired",
  "detail": "eyJhbGciOiJBMTI4S1ciLCJlbmMiOiJBMTI4Q0J1LUhTMjU2IiwidHlwIjoiSldUIn0.Fb5jEJb9zokguyPFyha4YFwguTMe8zChZ9isrCgI5r8o1Lfk0q_few.c02C5x7NTPEzerSoc8Rghw.lRWHsUJSm5W-NR8sfg8756MVDyA66dy_Ymet78bmNarFXEbvUYmOjCg1maDrUDmUWvWvi7_OYjAz7CgiHs7btIStaBklGX1nxIh60c_8DpA3ustSTYjmnrdSlPDJ9gENeewDIHWCjTgz1MjKhE42mdeZ6xFrxu7JFcc23m4J31kcbR8wL92MZChb_issdqhXc8CnZzYwP-PZ3wCWgsn63gc_-yQ5Y5cz9a1Sqtcbx7P2fw7PDkQi1SvVRcL7XQXhGvNbuyB21sxYYTjdcatoY6wAAGGF_UcTMmhoDV6dziELEq7pGKkwmFXZP38rZs_CBM7vtBKtWY_ESX1_C7SmrucQJRa4sdrsbHA98-q1lQkoK-ZJnl3wZRoJ6xslEicxj9bpuRL20ZRd-kmXwPBSY0ldTcvkLHhKGrN7vMBmbmQDcnps2iH64BOWi-O-YKupGK70eO-YmYLZ3T85nlbttg.Mo9LyvjYVYzN6cl258MXrQ",
  "status": 403,
  "traceId": "00-67cb3e28086d1b4198cf96e8d37b495a-e76f80e2f9c51f4b-00"
}
```

**Summary:** Obtain a bearer token via password grant type login

### HTTP Request 
`POST /api/v1/authentication/login`

**Request body**

| Attribute  | Type and description                                                                     |
| ---------- | ---------------------------------------------------------------------------------------- |
| `email`    | **string**<br/>The username associated with a valid user account in SIERA                |
| `password` | **string**<br/>The valid password associated with the username of the SIERA user account |


**Response Body**

The response body will be either a token with expiration and lockout information, or error details of the failed attempt.

| Attribute                   | Type and description                                                                                              |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `token`                     | **integer**<br/>A valid generated token which can be used in place of $ACCESS_TOKEN$ and passed as a bearer token |
| `expiration`                | **datetime**<br/>The datetime which the token will expire                                                         |
| `lockoutTimeRemaining`      | **integer**<br/>The amount of time in seconds before which a locked account can attempt a further login           |
| `maxRetriesExceeded`        | **integer**<br/>The number of times which have been attempted which caused the account to be temporarily locked   |
| `previousAccessFailedCount` | **integer**<br/>On successful login, this will contain the number of previous failed attempts                     |
| `type`                      | **integer**<br/>The type of validation failure which occured                                                      |
| `title`                     | **string**<br/>The title of the failure                                                                           |
| `status`                    | **integer**<br/>The error code associated with the failure                                                        |
| `detail`                    | **string**<br/>A description of the failure or further associated information                                     |

**Responses**

| Code | Description                                              |
| ---- | -------------------------------------------------------- |
| 200  | OK |
| 401  | Unauthorised, the header token expired or is missing        |
| 401  | Unauthorized                                             |
| 403  | User account has been locked or the password has expired |
| 500  | Server error                                             |