# Funds

The Funds endpoints allow you to create and manage funds to associated with assets in SIERA. You can upload new funds, update funds or delete them from a given instance in SIERA. Note that a fund must be associated with an [organisation](#organisations) and can't exist on its own.

## Get all funds

```shell
```

> GET /api/v1/funds

```shell
curl https://api.sieraglobal.com/api/v1/funds \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

[
  {
    "fundId": 1,
    "fundName": "TG Pension Fund",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "M2",
    "yearStart": 4,
    "organisationId": 3
  },
  {
    "fundId": 2,
    "fundName": "TF Sustainable Fund",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "M2",
    "yearStart": 4,
    "organisationId": 3
  }
]
```

**Summary:** Provides a list of all the funds in SIERA

### HTTP Request 
`GET /api/v1/funds` 


**Response Body**

The response body will be a list of funds.

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fundId`                   | **integer**<br/>The SIERA-generated id of the fund                                                                                                                                                      |
| `fundName`                 | **string**<br/>The name of the fund                                                                                                                                                                     |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the fund                                                                                                                         |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the fund, 1 for a calendar start (January), 4 for financial year start (April)                                                           |
| `organisationId`           | **integer**<br/>The id of the associated [organisation](#organisations)                                                                                                                                 |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the fund was not found                    |
| 500  | Server error                                         |


## Get a fund

```shell
```

> GET /api/v1/funds/{fundId}

```shell
curl https://api.sieraglobal.com/api/v1/funds/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

{
  "fundId": 2,
  "fundName": "TF Sustainable Fund",
  "reportingCurrency": "GBP",
  "reportingMeasurementUnit": "M2",
  "yearStart": 1,
  "organisationId": 3
}
```

**Summary:** Provides a single fund given an ID

### HTTP Request 
`GET /api/v1/funds/{fundId}` 

**Parameters**

| Name   | Located in | Description                          | Required | Type        |
| ------ | ---------- | ------------------------------------ | -------- | ----------- |
| fundId | path       | A valid id of a fund stored in SIERA | Yes      | **integer** |

**Response Body**

The response body will the specified fund which matches the fundId given as a parameter.


| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fundId`                   | **integer**<br/>The SIERA-generated id of the fund                                                                                                                                                      |
| `fundName`                 | **string**<br/>The name of the fund                                                                                                                                                                     |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the fund                                                                                                                         |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the fund, 1 for a calendar start (January), 4 for financial year start (April)                                                           |
| `organisationId`           | **integer**<br/>The id of the associated [organisation](#organisations)                                                                                                                                 |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the fund was not found                    |
| 500  | Server error                                         |


## Upload a new fund

```shell
```

> POST /api/v1/funds

```shell
curl POST https://api.sieraglobal.com/api/v1/assets \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {
    "fundName": "PL Green Fund",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "M2",
    "yearStart": 1,
    "organisationId": 3
  }
```

> Response (201)

```json
{
  "fundId": 6
}
```

**Summary:** Upload a new fund

### HTTP Request 
`POST /api/v1/funds` 


**Request body**

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fundId`                   | **integer**<br/>The SIERA-generated id of the fund                                                                                                                                                      |
| `fundName`                 | **string**<br/>The name of the fund                                                                                                                                                                     |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the fund                                                                                                                         |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the fund, 1 for a calendar start (January), 4 for financial year start (April)                                                           |
| `organisationId`           | **integer**<br/>The id of the associated [organisation](#organisations)                                                                                                                                 |

**Response Body**

The response body will a new fund ID relating to the uploaded fund

| Attribute | Type and description                                   |
| --------- | ------------------------------------------------------ |
| `fundId`  | **integer**<br/>The SIERA-generated id of the new fund |

**Responses**

| Code | Description                                            |
| ---- | ------------------------------------------------------ |
| 201  | Created                                                |
| 400  | Validation failure                                     |
| 401  | Not found, the specified organisation id was not found |
| 500  | Server error                                           |

## Update a fund

```shell
```

> PUT /api/v1/funds/{fundId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/funds/11 \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON 
  {
    "fundId": 2
    "fundName": "TF Sustainable Green Fund",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "FT2",
    "yearStart": 1,
    "organisationId": 3
  }
```

> Response (200)

**Summary:** Updates an existing fund by ID

### HTTP Request 
`PUT /api/v1/funds/{fundId}` 

**Parameters**

| Name   | Located in | Description                               | Required | Type        |
| ------ | ---------- | ----------------------------------------- | -------- | ----------- |
| fundId | path       | The id of the fund to be updated in SIERA | Yes      | **integer** |

**Request body**

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fundId`                   | **integer**<br/>The SIERA-generated id of the fund                                                                                                                                                      |
| `fundName`                 | **string**<br/>The name of the fund                                                                                                                                                                     |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the fund                                                                                                                         |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the fund, 1 for a calendar start (January), 4 for financial year start (April)                                                           |
| `organisationId`           | **integer**<br/>The id of the associated [organisation](#organisations)                                                                                                                                 |


**Responses**

| Code | Description                                                                       |
| ---- | --------------------------------------------------------------------------------- |
| 201  | Created                                                                           |
| 400  | Validation failure, one or more of the enumerations were not correctly identified |
| 401  | Unauthorised, the header token expired or is missing                              |
| 404  | Not found, the fund or specified organisationId was not found                     |
| 500  | Server error                                                                      |

## Delete a fund 

```shell
```

> DELETE /api/v1/funds/{fundId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/funds/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing fund by ID

### HTTP Request 
`DELETE /api/v1/funds/{fundId}` 

**Parameters**

| Name   | Located in | Description                               | Required | Type        |
| ------ | ---------- | ----------------------------------------- | -------- | ----------- |
| fundId | path       | The id of the fund to be deleted in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the fund was not found                    |
| 500  | Server error                                         |

## Validation rules

When uploading new funds or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for funds are:

1. When uploading a new fund, the **fundId** must be 0 or null. 
2. When updating a fund, the **fundId** must be of an existing fund in SIERA.
3. The **organisationId** must be provided and be for a valid organisation in SIERA.