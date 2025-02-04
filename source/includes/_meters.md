# Meters

The Meters endpoints allow you to manage utility meters associated with assets in SIERA. You can upload new meters, update meters or delete them from a given instance in SIERA. Note that a meter must be associated with an asset and can't exist on its own.

## Get all meters

```shell
```

> GET /api/v1/meters

```shell
curl https://api.sieraglobal.com/api/v1/meters \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

[
  {
    "meterId": 11,
    "assetId": 2,
    "unitId": 1,
    "mpan": "S018011012261305588165",
    "serialNumber": "1875258102",
    "comment": "",
    "supplier": "EON",
    "areaCovered": "SharedServices",
    "controlledBy": "Landlord",
    "floorAreaServed": 730,
    "meterType": "Electricity",
    "generationType": "NationalGrid",
    "measurementType": "M2",
    "locationCarbonFactorId": 0,
    "marketCarbonFactorId": 0,
    "unitRateId": 1,
    "isActive": true,
    "isAMR": false,
    "isSubmeter": false,
    "isValidated": true,
    "isROC": false,
    "isFIT": false,
    "isCCA": false,
    "isEUETS": false,
    "hasHalfHourData": false
  },
  {
    "meterId": 12,
    "assetId": 2,
    "unitId": 2,
    "mpan": "S018005012341305549165",
    "serialNumber": "1815248121",
    "comment": "",
    "supplier": "EON",
    "areaCovered": "WholeBuilding",
    "controlledBy": "Gas",
    "floorAreaServed": 1100,
    "meterType": "Gas",
    "generationType": "NationalGrid",
    "measurementType": "M2",
    "locationCarbonFactorId": 0,
    "marketCarbonFactorId": 0,
    "unitRateId": 2,
    "isActive": true,
    "isAMR": false,
    "isSubmeter": false,
    "isValidated": false,
    "isROC": false,
    "isFIT": false,
    "isCCA": false,
    "isEUETS": false,
    "hasHalfHourData": false
  },
  
  {
    "meterId": 13,
    "assetId": 3,
    "unitId": 0,
    "mpan": "S018012018913308149293",
    "serialNumber": "1913513513",
    "comment": "First Floor Electricity",
    "supplier": "EDF",
    "areaCovered": "TenantSpace",
    "controlledBy": "Electricity",
    "floorAreaServed": 130,
    "meterType": "Electricity",
    "generationType": "NationalGrid",
    "measurementType": "M2",
    "locationCarbonFactorId": 0,
    "marketCarbonFactorId": 0,
    "unitRateId": 0,
    "isActive": true,
    "isAMR": false,
    "isSubmeter": false,
    "isValidated": false,
    "isROC": false,
    "isFIT": false,
    "isCCA": false,
    "isEUETS": false,
    "hasHalfHourData": false
  }
]
```

**Summary:** Provides a list of all the meters

### HTTP Request 
`GET /api/v1/meters` 


**Response Body**

The response body will be a list of meters.

| Attribute                | Type and description                                                                                                                                                                                                                                                    |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `meterId`                | **integer**<br/>The SIERA-generated id of the meter                                                                                                                                                                                                                     |
| `assetId`                | **integer**<br/>The SIERA-generated id of the associated asset                                                                                                                                                                                                          |
| `unitId`                 | **integer**<br/>The SIERA-generated id of any associated unit                                                                                                                                                                                                           |
| `mpan`                   | **string**<br/>The meter point administration number (MPAN) of the meter                                                                                                                                                                                                |
| `serialNumber`           | **string**<br/>The serial number of the meter                                                                                                                                                                                                                           |
| `comment`                | **string**<br/>A free-text description relating to the meter                                                                                                                                                                                                            |
| `supplier`               | **string**<br/>Any utilities supplier related to the meter                                                                                                                                                                                                              |
| `areaCovered`            | **enumeration**<br/>A valid area of the property which this meter covers, from the [area covered](#enumerations-area-covered) enumeration                                                                                                                                            |
| `controlledBy`           | **enumeration**<br/>A valid item from the [meter control](#enumerations-meter-control) enumeration showing who primarily pays for the energy from this meter, the landlord or the tenant                                                                                             |
| `floorAreaServed`        | **integer**<br/>The floor area covered by this meter                                                                                                                                                                                                                    |
| `meterType`              | **enumeration**<br/>A valid utility of the meter from the [meter type](#enumerations-meter-type) enumeration                                                                                                                                                                         |
| `generationType`         | **enumeration**<br/>A valid generation type of the meter from the [generation type](#enumeration-generation-type) enumeration                                                                                                                                                       |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>)                                                                |
| `locationCarbonFactorId` | **integer**<br/>The id value of an location-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                   |
| `marketCarbonFactorId`   | **integer**<br/>The id value of an market-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                     |
| `unitRateId`             | **integer**<br/>The id value of a cost unit rate Id which exists in the API-caller's SIERA instance, or one of the [default unit rates](#unit-rates) provided by Evora                                                                                          |
| `isActive`               | **boolean**<br/>A boolean flag indicating if this meter is considered active and currently in use or not.                                                                                                                                                               |
| `isAMR`                  | **boolean**<br/>A boolean flag indicating if this meter's readings are being retrieved by automatic meter reading or not.                                                                                                                                               |
| `isSubmeter`             | **boolean**<br/>A boolean flag indicating if this meter isa sub-meter or not                                                                                                                                                                                            |
| `isValidated`            | **boolean**<br/>A boolean flag indicating if this meter has been validated or not.                                                                                                                                                                                      |
| `isROC`                  | **boolean**<br/>A boolean flag indicating if this meter has an [Renewables Obligation Certificate](https://www.ofgem.gov.uk/environmental-and-social-schemes/renewables-obligation-ro) generation meter which measures total electricity produced by solar panel or not |
| `isFIT`                  | **boolean**<br/>A boolean flag indicating if this meter is a Feed-In-Time tariff (relating to solar panels) or not.                                                                                                                                                     |
| `isCCA`                  | **boolean**<br/>A boolean flag indicating if this meter is part of a [Community Choice Aggregation](https://en.wikipedia.org/wiki/Community_Choice_Aggregation) or not.                                                                                                 |
| `isEUETS`                | **boolean**<br/>A boolean flag indicating if this meter is part of the [EU Energy Trading System](https://ec.europa.eu/clima/policies/ets_en) or not.                                                                                                                   |
| `hasHalfHourData`        | **boolean**<br/>A boolean flag indicating if this meter has received half-hourly data or not.                                                                                                                                                                           |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 500  | Server error                                         |


## Get a meter

```shell
```

> GET /api/v1/meters/{meterId}

```shell
curl https://api.sieraglobal.com/api/v1/meters/11 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

{
  "meterId": 11,
  "assetId": 2,
  "unitId": 1,
  "mpan": "S018011012261305588165",
  "serialNumber": "1875258102",
  "comment": "",
  "supplier": "EON",
  "areaCovered": "SharedServices",
  "controlledBy": "Landlord",
  "floorAreaServed": 730,
  "meterType": "Electricity",
  "generationType": "NationalGrid",
  "measurementType": "M2",
  "locationCarbonFactorId": 0,
  "marketCarbonFactorId": 0,
  "unitRateId": 1,
  "isActive": true,
  "isAMR": false,
  "isSubmeter": false,
  "isValidated": true,
  "isROC": false,
  "isFIT": false,
  "isCCA": false,
  "isEUETS": false,
  "hasHalfHourData": false
}
```

**Summary:** Provides a single meter given an ID

### HTTP Request 
`GET /api/v1/meters/{meterId}` 

**Parameters**

| Name    | Located in | Description                           | Required | Type        |
| ------- | ---------- | ------------------------------------- | -------- | ----------- |
| meterId | path       | A valid id of a meter stored in SIERA | Yes      | **integer** |

**Response Body**

The response body will the specified meter which matches the meterId given as a parameter.

| Attribute                | Type and description                                                                                                                                                                                                                                                    |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `meterId`                | **integer**<br/>The SIERA-generated id of the meter                                                                                                                                                                                                                     |
| `assetId`                | **integer**<br/>The SIERA-generated id of the associated asset                                                                                                                                                                                                          |
| `unitId`                 | **integer**<br/>The SIERA-generated id of any associated unit                                                                                                                                                                                                           |
| `mpan`                   | **string**<br/>The meter point administration number (MPAN) of the meter                                                                                                                                                                                                |
| `serialNumber`           | **string**<br/>The serial number of the meter                                                                                                                                                                                                                           |
| `comment`                | **string**<br/>A free-text description relating to the meter                                                                                                                                                                                                            |
| `supplier`               | **string**<br/>Any utilities supplier related to the meter                                                                                                                                                                                                              |
| `areaCovered`            | **enumeration**<br/>A valid area of the property which this meter covers, from the [area covered](#enumerations-area-covered) enumeration                                                                                                                                            |
| `controlledBy`           | **enumeration**<br/>A valid item from the [meter control](#enumerations-meter-control) enumeration showing who primarily pays for the energy from this meter, the landlord or the tenant                                                                                             |
| `floorAreaServed`        | **integer**<br/>The floor area covered by this meter                                                                                                                                                                                                                    |
| `meterType`              | **enumeration**<br/>A valid utility of the meter from the [meter type](#enumerations-meter-type) enumeration                                                                                                                                                                         |
| `generationType`         | **enumeration**<br/>A valid generation type of the meter from the [generation type](#enumeration-generation-type) enumeration                                                                                                                                                       |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>)                                                                |
| `locationCarbonFactorId` | **integer**<br/>The id value of an location-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                   |
| `marketCarbonFactorId`   | **integer**<br/>The id value of an market-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                     |
| `unitRateId`             | **integer**<br/>The id value of a cost unit rate Id which exists in the API-caller's SIERA instance, or one of the [default unit rates](#unit-rates) provided by Evora                                                                                          |
| `isActive`               | **boolean**<br/>A boolean flag indicating if this meter is considered active and currently in use or not.                                                                                                                                                               |
| `isAMR`                  | **boolean**<br/>A boolean flag indicating if this meter's readings are being retrieved by automatic meter reading or not.                                                                                                                                               |
| `isSubmeter`             | **boolean**<br/>A boolean flag indicating if this meter isa sub-meter or not                                                                                                                                                                                            |
| `isValidated`            | **boolean**<br/>A boolean flag indicating if this meter has been validated or not.                                                                                                                                                                                      |
| `isROC`                  | **boolean**<br/>A boolean flag indicating if this meter has an [Renewables Obligation Certificate](https://www.ofgem.gov.uk/environmental-and-social-schemes/renewables-obligation-ro) generation meter which measures total electricity produced by solar panel or not |
| `isFIT`                  | **boolean**<br/>A boolean flag indicating if this meter is a Feed-In-Time tariff (relating to solar panels) or not.                                                                                                                                                     |
| `isCCA`                  | **boolean**<br/>A boolean flag indicating if this meter is part of a [Community Choice Aggregation](https://en.wikipedia.org/wiki/Community_Choice_Aggregation) or not.                                                                                                 |
| `isEUETS`                | **boolean**<br/>A boolean flag indicating if this meter is part of the [EU Energy Trading System](https://ec.europa.eu/clima/policies/ets_en) or not.                                                                                                                   |
| `hasHalfHourData`        | **boolean**<br/>A boolean flag indicating if this meter has received half-hourly data or not.                                                                                                                                                                           |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 401  | Not found, the specified meter was not found         |
| 500  | Server error                                         |

## Upload a new meter

```shell
```

> POST /api/v1/meters

```shell
curl POST https://api.sieraglobal.com/api/v1/meters \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {    
    "assetId": 2,
    "unitId": 1,
    "mpan": "S018011012261305588165",
    "serialNumber": "1875258102",
    "comment": "",
    "supplier": "EON",
    "areaCovered": "SharedServices",
    "controlledBy": "Landlord",
    "floorAreaServed": 730,
    "meterType": "Electricity",
    "generationType": "NationalGrid",
    "measurementType": "M2",
    "locationCarbonFactorId": 0,
    "marketCarbonFactorId": 0,
    "unitRateId": 1,
    "isActive": true,
    "isAMR": false,
    "isSubmeter": false,
    "isValidated": true,
    "isROC": false,
    "isFIT": false,
    "isCCA": false,
    "isEUETS": false,
    "hasHalfHourData": false
  }
```

> Response (201)

```json
{
  "meterId": 12
}
```

**Summary:** Upload a new meter

### HTTP Request 
`POST /api/v1/meters` 


**Request body**

| Attribute                | Type and description                                                                                                                                                                                                                                                    |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `assetId`                | **integer**<br/>A valid id of the associated asset                                                                                                                                                                                                                      |
| `unitId`                 | **integer**<br/>A valid id of an associated unit                                                                                                                                                                                                                        |
| `mpan`                   | **string**<br/>The meter point administration number (MPAN) of the meter                                                                                                                                                                                                |
| `serialNumber`           | **string**<br/>The serial number of the meter                                                                                                                                                                                                                           |
| `comment`                | **string**<br/>A free-text description relating to the meter                                                                                                                                                                                                            |
| `supplier`               | **string**<br/>Any utilities supplier related to the meter                                                                                                                                                                                                              |
| `areaCovered`            | **enumeration**<br/>A valid area of the property which this meter covers, from the [area covered](#enumerations-area-covered) enumeration                                                                                                                                            |
| `controlledBy`           | **enumeration**<br/>A valid item from the [meter control](#enumerations-meter-control) enumeration showing who primarily pays for the energy from this meter, the landlord or the tenant                                                                                             |
| `floorAreaServed`        | **integer**<br/>The floor area covered by this meter                                                                                                                                                                                                                    |
| `meterType`              | **enumeration**<br/>A valid utility of the meter from the [meter type](#enumerations-meter-type) enumeration                                                                                                                                                                         |
| `generationType`         | **enumeration**<br/>A valid generation type of the meter from the [generation type](#enumeration-generation-type) enumeration                                                                                                                                                       |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>)                                                                |
| `locationCarbonFactorId` | **integer**<br/>The id value of an location-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                   |
| `marketCarbonFactorId`   | **integer**<br/>The id value of an market-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                     |
| `unitRateId`             | **integer**<br/>The id value of a cost unit rate Id which exists in the API-caller's SIERA instance, or one of the [default unit rates](#unit-rates) provided by Evora                                                                                          |
| `isActive`               | **boolean**<br/>A boolean flag indicating if this meter is considered active and currently in use or not.                                                                                                                                                               |
| `isAMR`                  | **boolean**<br/>A boolean flag indicating if this meter's readings are being retrieved by automatic meter reading or not.                                                                                                                                               |
| `isSubmeter`             | **boolean**<br/>A boolean flag indicating if this meter isa sub-meter or not                                                                                                                                                                                            |
| `isValidated`            | **boolean**<br/>A boolean flag indicating if this meter has been validated or not.                                                                                                                                                                                      |
| `isROC`                  | **boolean**<br/>A boolean flag indicating if this meter has an [Renewables Obligation Certificate](https://www.ofgem.gov.uk/environmental-and-social-schemes/renewables-obligation-ro) generation meter which measures total electricity produced by solar panel or not |
| `isFIT`                  | **boolean**<br/>A boolean flag indicating if this meter is a Feed-In-Time tariff (relating to solar panels) or not.                                                                                                                                                     |
| `isCCA`                  | **boolean**<br/>A boolean flag indicating if this meter is part of a [Community Choice Aggregation](https://en.wikipedia.org/wiki/Community_Choice_Aggregation) or not.                                                                                                 |
| `isEUETS`                | **boolean**<br/>A boolean flag indicating if this meter is part of the [EU Energy Trading System](https://ec.europa.eu/clima/policies/ets_en) or not.                                                                                                                   |
| `hasHalfHourData`        | **boolean**<br/>A boolean flag indicating if this meter has received half-hourly data or not.                                                                                                                                                                           |

**Response Body**

The response body will a new meter ID relating to the uploaded meter

| Attribute | Type and description                                    |
| --------- | ------------------------------------------------------- |
| `meterId` | **integer**<br/>The SIERA-generated id of the new meter |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 201  | Created                                              |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 500  | Server error                                         |


## Update a meter

```shell
```

> PUT /api/v1/meters/{meterId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/meters/11 \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
  {
    "assetId": 2,
    "unitId": 1,
    "mpan": "S018011012261305588165",
    "serialNumber": "1875258102",
    "comment": "",
    "supplier": "EDF",
    "areaCovered": "WholeBuilding",
    "controlledBy": "Landlord",
    "floorAreaServed": 730,
    "meterType": "Electricity",
    "generationType": "NationalGrid",
    "measurementType": "M2",
    "locationCarbonFactorId": 0,
    "marketCarbonFactorId": 0,
    "unitRateId": 1,
    "isActive": true,
    "isAMR": false,
    "isSubmeter": false,
    "isValidated": true,
    "isROC": false,
    "isFIT": false,
    "isCCA": false,
    "isEUETS": false,
    "hasHalfHourData": false
  }
```

> Response (200)

**Summary:** Updates an existing meter by ID

### HTTP Request 
`PUT /api/v1/meters/{meterId}` 

**Parameters**

| Name    | Located in | Description                                | Required | Type        |
| ------- | ---------- | ------------------------------------------ | -------- | ----------- |
| meterId | path       | The id of the meter to be updated in SIERA | Yes      | **integer** |

**Request body**

| Attribute                | Type and description                                                                                                                                                                                                                                                    |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `meterId`                | **integer**<br/>The SIERA-generated id of the meter                                                                                                                                                                                                                     |
| `assetId`                | **integer**<br/>The SIERA-generated id of the associated asset                                                                                                                                                                                                          |
| `unitId`                 | **integer**<br/>The SIERA-generated id of any associated unit                                                                                                                                                                                                           |
| `mpan`                   | **string**<br/>The meter point administration number (MPAN) of the meter                                                                                                                                                                                                |
| `serialNumber`           | **string**<br/>The serial number of the meter                                                                                                                                                                                                                           |
| `comment`                | **string**<br/>A free-text description relating to the meter                                                                                                                                                                                                            |
| `supplier`               | **string**<br/>Any utilities supplier related to the meter                                                                                                                                                                                                              |
| `areaCovered`            | **enumeration**<br/>A valid area of the property which this meter covers, from the [area covered](#enumerations-area-covered) enumeration                                                                                                                                            |
| `controlledBy`           | **enumeration**<br/>A valid item from the [meter control](#enumerations-meter-control) enumeration showing who primarily pays for the energy from this meter, the landlord or the tenant                                                                                             |
| `floorAreaServed`        | **integer**<br/>The floor area covered by this meter                                                                                                                                                                                                                    |
| `meterType`              | **enumeration**<br/>A valid utility of the meter from the [meter type](#enumerations-meter-type) enumeration                                                                                                                                                                         |
| `generationType`         | **enumeration**<br/>A valid generation type of the meter from the [generation type](#enumeration-generation-type) enumeration                                                                                                                                                       |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>)                                                                |
| `locationCarbonFactorId` | **integer**<br/>The id value of an location-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                   |
| `marketCarbonFactorId`   | **integer**<br/>The id value of an market-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                     |
| `unitRateId`             | **integer**<br/>The id value of a cost unit rate Id which exists in the API-caller's SIERA instance, or one of the [default unit rates](#unit-rates) provided by Evora                                                                                          |
| `isActive`               | **boolean**<br/>A boolean flag indicating if this meter is considered active and currently in use or not.                                                                                                                                                               |
| `isAMR`                  | **boolean**<br/>A boolean flag indicating if this meter's readings are being retrieved by automatic meter reading or not.                                                                                                                                               |
| `isSubmeter`             | **boolean**<br/>A boolean flag indicating if this meter isa sub-meter or not                                                                                                                                                                                            |
| `isValidated`            | **boolean**<br/>A boolean flag indicating if this meter has been validated or not.                                                                                                                                                                                      |
| `isROC`                  | **boolean**<br/>A boolean flag indicating if this meter has an [Renewables Obligation Certificate](https://www.ofgem.gov.uk/environmental-and-social-schemes/renewables-obligation-ro) generation meter which measures total electricity produced by solar panel or not |
| `isFIT`                  | **boolean**<br/>A boolean flag indicating if this meter is a Feed-In-Time tariff (relating to solar panels) or not.                                                                                                                                                     |
| `isCCA`                  | **boolean**<br/>A boolean flag indicating if this meter is part of a [Community Choice Aggregation](https://en.wikipedia.org/wiki/Community_Choice_Aggregation) or not.                                                                                                 |
| `isEUETS`                | **boolean**<br/>A boolean flag indicating if this meter is part of the [EU Energy Trading System](https://ec.europa.eu/clima/policies/ets_en) or not.                                                                                                                   |
| `hasHalfHourData`        | **boolean**<br/>A boolean flag indicating if this meter has received half-hourly data or not.                                                                                                                                                                           |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified meter id was not found      |
| 500  | Server error                                         |

## Delete a meter 

```shell
```

> DELETE /api/v1/meters/{meterId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/meters/11 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing meter by ID

### HTTP Request 
`DELETE /api/v1/meters/{meterId}` 

**Parameters**

| Name    | Located in | Description                                | Required | Type        |
| ------- | ---------- | ------------------------------------------ | -------- | ----------- |
| meterId | path       | The id of the meter to be deleted in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified meter id was not found      |
| 500  | Server error                                         |

## Validation rules

When uploading new meters or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for meters are:

1. When uploading a new meter, the **meterId** must be 0 or null.
2. When updating an meter, the **meterId** must be of an existing meter in SIERA.
3. The **assetId** must be provided and be for a valid asset in SIERA.
4. The **locationCarbonFactorId** must be provided and be for a valid carbon factor in SIERA.
5. The **marketCarbonFactorId** must be provided and be for a valid carbon factor in SIERA.
6. The **unitRateId** must be provided and be for a valid unit rate in SIERA.
7. The carbon factors chosen for **locationCarbonFactorId** and **marketCarbonFactorId** must match on utility type. For example, an electricity meter must choose an electricity carbon factor.
