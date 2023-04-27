# Introduction 

Welcome to the SIERA API. You can use the SIERA API to access and modify Assets, Meter and Consumption data. 

This page helps you to understand the requirements of the API, common errors, the format of data sent and received and other details related to security and operation of the API.

We provide [an OpenAPI specification description](https://api.sieraglobal.com/swagger/v1/swagger.json) which can be imported into programs such as [Postman](https://www.postman.com/) to help you get started with the API.

## Requirements 

To use the latest version of the REST API you will need a valid account with SIERA. This can be obtained by contacting [SIERA Support](mailto:support@sieraglobal.com).

## Request format

Request parameters should be provided using the `application/json` Content-Type. The only exception is the IDs of entities or assets which are part of the URLs.

Unless otherwise documented all responses are JSON-encoded `Content-Type: application/json`.

All endpoints require either a bearer token or basic token which must be specified in the header of the request. How to obtain a token is explained in [authentication](#authentication).

## Date format

All date formats should be sent as `dd/mm/yy`

## Response types

Most endpoints will return a standard HTTP status code to reflect the result of the API call. Where an endpoint produces a different response code, or has additional information about a response code it will be written against the endpoint's information.

| Code | Text              | Description                                                                                                        |
| ---- | ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| 200  | Ok                | Success, assets returned in the response body                                                                      |
| 201  | Created           | Success, the uploaded entity has been successfully created                                                         |
| 400  | Bad request       | Failed, the request failed validation                                                                              |
| 404  | Not found         | Failed, the item was not found                                                                                     |
| 429  | Too many requests | Failed, the request was refused due excessive use                                                                  |
| 5xx  | Server error      | Failed, an error has occurred on our servers. Wait a few minutes and try again or notify us if the errors continue |

## Rate limiting

The SIERA API enforces a rate limit on the number of requests allowed within certain time frames. The limits are:

| Time frame | Number of requests allowed |
| ---------- | -------------------------- |
| 1 second   | 100                        |
| 15 minutes | 1000                       |
| 12 hours   | 10,000                     |
| 7 days     | 100,000                    |

For every request that is made the number of further requests allowed in the largest available time frame will be returned in the headers of the response along with the datetime the limit will be reset, for example:

`x-rate-limit-limit: 7d`  
`x-rate-limit-remaining: 9991`  
`x-rate-limit-reset: 2021-12-29T15:21:09.3213831Z`  

If the limit is exceeded the caller will receive a HTTP status code of `429 Too Many Requests` along with a response body indicating the limit exceeded such as `API calls quota exceeded! maximum admitted 2 per 1s.`