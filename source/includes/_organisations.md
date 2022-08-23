# Organisations

The Organisations endpoints allow you to create and manage organisations to associated with assets in SIERA. You can upload new organisations, update organisations or delete them from a given instance in SIERA.

<aside class="notice">
Be careful to not delete organisations which are associated with funds, as this may result in related funds being deleted.
</aside>

## Get all organisations

```shell
```

> GET /api/v1/organisations

```shell
curl https://api.sieraglobal.com/api/v1/organisations \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

[
  {
    "organisationId": 1,
    "organisationName": "TPG Financial Services",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "M2",
    "yearStart": 1
  },
  {
    "organisationId": 2,
    "organisationName": "Colias",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "FT2",
    "yearStart": 4
  },
  {
    "organisationId": 3,
    "organisationName": "Sakitai",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "M2",
    "yearStart": 1
  }
]
```

**Summary:** Provides a list of all the organisations in SIERA

### HTTP Request 
`GET /api/v1/organisations` 


**Response Body**

The response body will be a list of organisations.

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organisationId`           | **integer**<br/>The SIERA-generated id of the organisation                                                                                                                                              |
| `organisationName`         | **string**<br/>The name of the organisation                                                                                                                                                             |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the organisation                                                                                                                 |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the organisation, 1 for a calendar start (January), 4 for financial year start (April)                                                   |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the organisation was not found            |
| 500  | Server error                                         |

## Get an organisation

```shell
```

> GET /api/v1/organisations

```shell
curl https://api.sieraglobal.com/api/v1/organisations/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
{
  "organisationId": 2,
  "organisationName": "Colias",
  "reportingCurrency": "GBP",
  "reportingMeasurementUnit": "FT2",
  "yearStart": 4
}
```

**Summary:** Provides an organisation

### HTTP Request 
`GET /api/v1/organisations` 


**Response Body**

The response body will be an organisation.

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organisationId`           | **integer**<br/>The SIERA-generated id of the organisation                                                                                                                                              |
| `organisationName`         | **string**<br/>The name of the organisation                                                                                                                                                             |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the organisation                                                                                                                 |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the organisation, 1 for a calendar start (January), 4 for financial year start (April)                                                   |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the organisation was not found            |
| 500  | Server error                                         |


## Upload a new organisation

```shell
```

> POST /api/v1/organisations

```shell
curl POST https://api.sieraglobal.com/api/v1/organisations \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {
    "organisationName": "PL Green organisation",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "M2",
    "yearStart": 4,
  }
```

> Response (201)

```json
{
  "organisationId": 6
}
```

**Summary:** Upload a new organisation

### HTTP Request 
`POST /api/v1/organisations` 


**Request body**

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organisationName`         | **string**<br/>The name of the organisation                                                                                                                                                             |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the organisation                                                                                                                 |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the organisation, 1 for a calendar start (January), 4 for financial year start (April)                                                   |

**Response Body**

The response body will a new organisation ID relating to the uploaded organisation

| Attribute        | Type and description                                           |
| ---------------- | -------------------------------------------------------------- |
| `organisationId` | **integer**<br/>The SIERA-generated id of the new organisation |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 201  | Created                                              |
| 401  | Unauthorised, the header token expired or is missing |
| 500  | Server error                                         |

## Update an organisation

```shell
```

> PUT /api/v1/organisations/{organisationId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/organisations/3 \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON 
  {
    "organisationName": "PL Green organisation",
    "reportingCurrency": "GBP",
    "reportingMeasurementUnit": "FT2",
    "yearStart": 4
  }
```

> Response (200)

**Summary:** Updates an existing organisation by ID

### HTTP Request 
`PUT /api/v1/organisations/{organisationId}` 

**Paraorganisations**

| Name           | Located in | Description                                       | Required | Type        |
| -------------- | ---------- | ------------------------------------------------- | -------- | ----------- |
| organisationId | path       | The id of the organisation to be updated in SIERA | Yes      | **integer** |

**Request body**

| Attribute                  | Type and description                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organisationId`           | **integer**<br/>The SIERA-generated id of the organisation                                                                                                                                              |
| `organisationName`         | **string**<br/>The name of the organisation                                                                                                                                                             |
| `reportingCurrency`        | **string**<br/>The 3-letter code of the currency used for reporting in the organisation                                                                                                                 |
| `reportingMeasurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of the asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `yearStart`                | **integer**<br/>The month considered the start of the year for the organisation, 1 for a calendar start (January), 4 for financial year start (April)                                                   |


**Responses**

| Code | Description                                            |
| ---- | ------------------------------------------------------ |
| 201  | Created                                                |
| 401  | Unauthorised, the header token expired or is missing   |
| 404  | Not found, the specified organisation id was not found |
| 500  | Server error                                           |

## Delete an organisation 

```shell
```

> DELETE /api/v1/organisations/{organisationId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/organisations/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing organisation by ID

### HTTP Request 
`DELETE /api/v1/organisation/{organisationId}` 

**Paraorganisations**

| Name           | Located in | Description                                       | Required | Type        |
| -------------- | ---------- | ------------------------------------------------- | -------- | ----------- |
| organisationId | path       | The id of the organisation to be deleted in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the organisation was not found            |
| 500  | Server error                                         |

## Validation rules

When uploading new organisations or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for organisations are:

1. When uploading a new organisation, the **organisationId** must be 0 or null. 
2. When updating an organisation, the **organisationId** must be of an existing organisation in SIERA.