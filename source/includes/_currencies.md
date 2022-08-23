# Currencies

The Currencies endpoints allow you to upload and manage currencies to associated with data in SIERA. You can upload new currencies, update currencies or delete them from a given instance in SIERA. Default currencies are provided for Great British Pounds (GBP, £), US Dollars (USD, $) and Euros (EUR, €). These defaults can not be deleted or updated. Currencies currently allow correct labelling of data in SIERA, and (at this time) offer no conversion functionality.

## Get all currencies

```shell
```

> GET /api/v1/currency

```shell
curl https://api.sieraglobal.com/api/v1/currency \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

[
  {
    "currencyCode": "GBP",
    "currencyName": "Great British Pounds",
    "currencySymbol": "£",
    "isDefault": true
  },
  {
    "currencyCode": "USD",
    "currencyName": "US Dollars",
    "currencySymbol": "$",
    "isDefault": true
  },
  {
    "currencyCode": "EUR",
    "currencyName": "Euros",
    "currencySymbol": "€",
    "isDefault": true
  }
]
```

**Summary:** Provides a list of all the currencies in SIERA

### HTTP Request 
`GET /api/v1/currency` 


**Response Body**

The response body will be a list of currencies.

| Attribute      | Type and description                                                 |
| -------------- | -------------------------------------------------------------------- |
| `currencyCode` | **string**<br/>The three-letter currency code of the currency        |
| `currencyCode` | **string**<br/>The full name of the currency                         |
| `currencyCode` | **string**<br/>The currency symbol of the currency                   |
| `isDefault`    | **bool**<br/>A flag indicating if the currency is a default in SIERA |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the currency was not found                |
| 500  | Server error                                         |

## Get all currencies

```shell
```

> GET /api/v1/currency/{currencyCode}

```shell
curl https://api.sieraglobal.com/api/v1/currency/GBP \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
{
  "currencyCode": "GBP",
  "currencyName": "Great British Pounds",
  "currencySymbol": "£",
  "isDefault": true
}
```

**Summary:** Provides a currency in SIERA

### HTTP Request 
`GET /api/v1/currency/GBP` 


**Response Body**

The response body will be a currency.

| Attribute      | Type and description                                                 |
| -------------- | -------------------------------------------------------------------- |
| `currencyCode` | **string**<br/>The three-letter currency code of the currency        |
| `currencyCode` | **string**<br/>The full name of the currency                         |
| `currencyCode` | **string**<br/>The currency symbol of the currency                   |
| `isDefault`    | **bool**<br/>A flag indicating if the currency is a default in SIERA |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the currency was not found                |
| 500  | Server error                                         |

## Upload a new currency

```shell
```

> POST /api/v1/currency

```shell
curl POST https://api.sieraglobal.com/api/v1/currency \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {
    "currencyCode": "JPY",
    "currencyName": "Japanese Yen",
    "currencySymbol": "¥"
  }
```

> Response (201)

```json
{
  "currencyCode": "JPY"
}
```

**Summary:** Upload a new currency

### HTTP Request 
`POST /api/v1/currency` 


**Request body**

| Attribute      | Type and description                                          |
| -------------- | ------------------------------------------------------------- |
| `currencyCode` | **string**<br/>The three-letter currency code of the currency |
| `currencyCode` | **string**<br/>The full name of the currency                  |
| `currencyCode` | **string**<br/>The currency symbol of the currency            |

**Response Body**

The response body will a new fund ID relating to the uploaded fund

| Attribute      | Type and description                                           |
| -------------- | -------------------------------------------------------------- |
| `currencyCode` | **integer**<br/>The three-letter currency code of the currency |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 201  | Created                                              |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 500  | Server error                                         |

## Update a currency

```shell
```

> PUT /api/v1/currency/{currencyCode}

```shell
curl PUT https://api.sieraglobal.com/api/v1/currency/JPY \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON 
  {
    "currencyCode": "JPY",
    "currencyName": "Japanese Yen Updated",
    "currencySymbol": "¥"
  }
```

> Response (200)

**Summary:** Updates an existing currency by code

### HTTP Request 
`PUT /api/v1/currency/{currencyCode}` 

**Parameter**

| Name         | Located in | Description                                     | Required | Type        |
| ------------ | ---------- | ----------------------------------------------- | -------- | ----------- |
| currencyCode | path       | The code of the currency to be updated in SIERA | Yes      | **integer** |

**Request body**

| Attribute      | Type and description                                          |
| -------------- | ------------------------------------------------------------- |
| `currencyCode` | **string**<br/>The three-letter currency code of the currency |
| `currencyCode` | **string**<br/>The full name of the currency                  |
| `currencyCode` | **string**<br/>The currency symbol of the currency            |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 201  | Created                                              |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the currency was not found                |
| 500  | Server error                                         |

## Delete a currency 

```shell
```

> DELETE /api/v1/currency/{currencyCode}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/currency/JPY \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing currency by code

### HTTP Request 
`DELETE /api/v1/currency/{currencyCode}` 

**Parameters**

| Name         | Located in | Description                                     | Required | Type        |
| ------------ | ---------- | ----------------------------------------------- | -------- | ----------- |
| currencyCode | path       | The code of the currency to be updated in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the currency was not found                |
| 500  | Server error                                         |

## Validation rules

When uploading new currencies or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for currencies are:

1. When updating a currency, the **currencyCode** must be of an existing currency in SIERA.
2. The **currencyCode** must not belong to a default currency. Default currencies cannot be updated or deleted.