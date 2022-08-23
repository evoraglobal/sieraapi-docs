# Waste Destinations

Waste destinations are the waste equivalent of [meters](#meters). They represent the final destination for waste disposed of at an asset. Destinations can be places like a landfill, a recycling point or a [materials recovery facility](https://en.wikipedia.org/wiki/Materials_recovery_facility). Just as meters have consumption records, waste destinations have [waste records](#waste-records), which in turn have both a summary and a record version.

## Get all waste destinations

```shell
```

> GET /api/v1/wastedestinations

```shell
curl https://api.sieraglobal.com/api/v1/wastedestinations \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

[
    {
      "assetId": 2,
      "wasteDestinationId": 2,
      "wasteDestinationDescription": "Mixed Recycleables",
      "comments": "Recycling for Chelsea House, London",
      "contractor": "Veolia",
      "reference": "Reference 1000022",
      "wasteDestination": "Recycled"
    },
    {
      "assetId": 2,
      "wasteDestinationId": 3,
      "wasteDestinationDescription": "General Waste",
      "comments": "General Waste for Chelsea House, London",
      "contractor": "Veolia",
      "reference": "Reference 1000023",
      "wasteDestination": "Landfill"
    }
]
```

**Summary:** Provides a list of all the waste destinations

### HTTP Request 
`GET /api/v1/wastedestination` 

**Response Body**

The response body will be a list of waste destimations.

| Attribute                     | Type and description                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------------------------------------- |
| `assetId`                     | **integer**<br/>The id of the asset                                                                       |
| `wasteDestinationId`          | **integer**<br/>The SIERA-generated id of the waste destination                                           |
| `wasteDestinationDescription` | **string**<br/>A description of the waste destination                                                     |
| `comments`                    | **string**<br/>Comments relating to the waste destination                                                 |
| `contractor`                  | **string**<br/>The name of the contractor providing the waste service                                     |
| `reference`                   | **string**<br/>A reference for the waste destination on the asset                                         |
| `wasteDestination`            | **enumeration**<br/>A valid destination type from the [waste destination](#waste-destination) enumeration |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, no waste destinations were found          |
| 500  | Server error                                         |


## Get a waste destination

```shell
```

> GET /api/v1/wastedestinations/{wasteDestinationId}

```shell
curl https://api.sieraglobal.com/api/v1/wastedestinations/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

{
  "assetId": 2,
  "wasteDestinationId": 2,
  "wasteDestinationDescription": "Mixed Recycleables",
  "comments": "Recycling for Chelsea House, London",
  "contractor": "Veolia",
  "reference": "Reference 1000022",
  "wasteDestination": "Recycled"
}

```

**Summary:** Provides a waste destination

### HTTP Request 
`GET /api/v1/wastedestinations/{wasteDestinationId}` 

**Parameters**

| Name               | Located in | Description                                       | Required | Type        |
| ------------------ | ---------- | ------------------------------------------------- | -------- | ----------- |
| wasteDestinationId | path       | A valid id of a waste destination stored in SIERA | Yes      | **integer** |

**Response Body**

The response body will be a waste destimation.

| Attribute                     | Type and description                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------------------------------------- |
| `assetId`                     | **integer**<br/>The id of the associated asset                                                            |
| `wasteDestinationId`          | **integer**<br/>The SIERA-generated id of the waste destination                                           |
| `wasteDestinationDescription` | **string**<br/>A description of the waste destination                                                     |
| `comments`                    | **string**<br/>Comments relating to the waste destination                                                 |
| `contractor`                  | **string**<br/>The name of the contractor providing the waste service                                     |
| `reference`                   | **string**<br/>A reference for the waste destination on the asset                                         |
| `wasteDestination`            | **enumeration**<br/>A valid destination type from the [waste destination](#enumerations-waste-destination) enumeration |


**Responses**


| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the waste destination was not found       |
| 500  | Server error                                         |


## Upload a new waste destination

```shell
```

> POST /api/v1/wastedestinations

```shell
curl POST https://api.sieraglobal.com/api/v1/wastedestinations \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {
    "assetId": 2,    
    "wasteDestinationDescription": "Glass Recycling",
    "comments": "Glass recycling for Chelsea House, London",
    "contractor": "Veolia",
    "reference": "Reference 1000024",
    "wasteDestination": "Recycled"
  }
```

> Response (201)

```json
{
  "wasteDestinationId": 6
}
```

**Summary:** Upload a new waste destination

### HTTP Request 
`POST /api/v1/wastedestinations` 

**Request body**

| Attribute                     | Type and description                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------------------------------------- |
| `assetId`                     | **integer**<br/>The id of a valid asset in the API caller's SIERA instance                                |
| `wasteDestinationDescription` | **string**<br/>A description of the waste destination                                                     |
| `comments`                    | **string**<br/>Comments relating to the waste destination                                                 |
| `contractor`                  | **string**<br/>The name of the contractor providing the waste service                                     |
| `reference`                   | **string**<br/>A reference for the waste destination on the asset                                         |
| `wasteDestination`            | **enumeration**<br/>A valid destination type from the [waste destination](#enumerations-waste-destination) enumeration |

**Response Body**

The response body will a new waste destination ID relating to the uploaded waste destination

| Attribute            | Type and description                                                |
| -------------------- | ------------------------------------------------------------------- |
| `wasteDestinationId` | **integer**<br/>The SIERA-generated id of the new waste destination |

**Responses**

| Code | Description                                     |
| ---- | ----------------------------------------------- |
| 201  | Created                                         |
| 400  | Validation failure                              |
| 401  | Not found, the specified asset id was not found |
| 500  | Server error                                    |



## Update a waste destination

```shell
```

> PUT /api/v1/wastedestinations/{wasteDestinationId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/wastedestinations/ \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
  {
    "assetId": 2,    
    "wasteDestinationId": 4,  
    "wasteDestinationDescription": "Plastic Recycling",
    "comments": "Plastic recycling for Chelsea House, London",
    "contractor": "Veolia",
    "reference": "Reference 1000025",
    "wasteDestination": "Recycled"
  }
```

> Response (200)

**Summary:** Updates an existing waste destination by ID

### HTTP Request 
`PUT /api/v1/wastedestinations/{wasteDestinationId}` 

**Parameters**

| Name               | Located in | Description                                       | Required | Type        |
| ------------------ | ---------- | ------------------------------------------------- | -------- | ----------- |
| wasteDestinationId | path       | A valid id of a waste destination stored in SIERA | Yes      | **integer** |

**Request body**

| Attribute                     | Type and description                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------------------------------------- |
| `assetId`                     | **integer**<br/>The id of the asset                                                                       |
| `wasteDestinationId`          | **integer**<br/>The SIERA-generated id of the waste destination                                           |
| `wasteDestinationDescription` | **string**<br/>A description of the waste destination                                                     |
| `comments`                    | **string**<br/>Comments relating to the waste destination                                                 |
| `contractor`                  | **string**<br/>The name of the contractor providing the waste service                                     |
| `reference`                   | **string**<br/>A reference for the waste destination on the asset                                         |
| `wasteDestination`            | **enumeration**<br/>A valid destination type from the [waste destination](#enumerations-waste-destination) enumeration |


**Responses**

| Code | Description                                                 |
| ---- | ----------------------------------------------------------- |
| 200  | OK                                                          |
| 400  | Validation failure                                          |
| 401  | Not found, the specified waste destination id was not found |
| 500  | Server error                                                |

## Delete a waste destination 

```shell
```

> DELETE /api/v1/wastedestinations/{wasteDestinationId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/wastedestinations/4 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing waste destination by ID

### HTTP Request 
`DELETE /api/v1/wastedestinations/{wasteDestinationId}` 

**Parameters**

| Name               | Located in | Description                                            | Required | Type        |
| ------------------ | ---------- | ------------------------------------------------------ | -------- | ----------- |
| wasteDestinationId | path       | The id of the waste destination to be deleted in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                                 |
| ---- | ----------------------------------------------------------- |
| 200  | OK                                                          |
| 401  | Unauthorised, the header token expired or is missing        |
| 401  | Not found, the specified waste destination id was not found |
| 500  | Server error                                                |

## Validation rules

When uploading new waste destinations or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for waste destinations are:

1. When uploading a new waste destination, the **wasteDestinationId** must be 0 or null. 
2. When updating a waste destination, the **wasteDestinationId** must be of an existing waste destination in SIERA.
3. The **assetId** must exist in SIERA.
4. The **wasteReference** must be unique. Validation will fail if any other waste destination has the same reference.