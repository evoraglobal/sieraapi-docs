# Assets

The Assets endpoints allow you to download asset data from SIERA. You can also upload new assets, update assets or delete them from a given instance in SIERA.

## Get all assets

```shell
```

> GET /api/v1/assets

```shell
curl https://api.sieraglobal.com/api/v1/assets \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
[
  {
    "assetId": 2,
    "assetName": "Chelsea House, London",
    "assetReference": "CHL-2",
    "country": "UnitedKingdom",
    "controlledBy": "Landlord",
    "sector": "Retail",
    "organisationId": 2,
    "fundId": 3,
    "gia": 1234,
    "nla": 1100,
    "cpa": 15,
    "ext": 100,
    "measurementType": "M2",
    "address": "1, The Way",
    "city": "Townington",
    "postcode": "AB12 3DC",
    "status": "MajorRefurbishment",
    "dateOfPurchase": "1999-01-01T00:00:00.000Z",
    "dateOfSale": "2021-03-14T00:00:00.000Z",
    "yearOfConstruction": 1985,
    "yearOfRefurbishment": 2006,
    "currentAssetValue": 1200000,
    "longitude": 51.507351,
    "latitude": -0.127758,
    "targetCarbon": 5,
    "targetEnergy": 1,
    "targetElectricity": 3,
    "targetFuelsAndThermals": 4,
    "targetWater": 6,
    "gresbSector": "Office",
    "carParkingSpaces": 14,
    "fri": true,
    "assetImageUri": "https://api.sieraglobal.com/api/v1/assets/2/assetimage"
  },
  {
    "assetId": 3,
    "assetName": "2-4 Sharwalk Building, Birmingham",
    "assetReference": "CHL-3",
    "country": "UnitedKingdom",
    "controlledBy": "Landlord",
    "sector": "Retail",
    "organisationId": 2,
    "fundId": 3,
    "gia": 1640,
    "nla": 1530,
    "cpa": 14,
    "ext": 121,
    "measurementType": "M2",
    "address": "2, The Way",
    "city": "Townington",
    "postcode": "AB12 3DC",
    "status": "MajorRefurbishment",
    "dateOfPurchase": "2000-01-01T00:00:00.000Z",
    "dateOfSale": "2021-03-19T00:00:00.000Z",
    "yearOfConstruction": 1985,
    "yearOfRefurbishment": 2007,
    "currentAssetValue": 1250000,
    "longitude": 51.507351,
    "latitude": -0.127758,
    "targetCarbon": 4,
    "targetEnergy": 3,
    "targetElectricity": 5,
    "targetFuelsAndThermals": 1,
    "targetWater": 6,
    "gresbSector": "Office",
    "carParkingSpaces": 18,
    "fri": false,
    "assetImageUri": "https://api.sieraglobal.com/api/v1/assets/3/assetimage"
  }
]
```

**Summary:** Provides a list of all assets in SIERA

### HTTP Request 
`GET /api/v1/assets` 


**Response Body**

The response body will include a list of all assets in SIERA.

| Attribute                | Type and description                                                                                                                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `assetId`                | **integer**<br/>The SIERA-generated id of the asset                                                                                                                                                      |
| `assetName`              | **string**<br/>The name of the asset                                                                                                                                                                     |
| `assetReference`         | **string**<br/>The user-specified asset reference, unique within the API caller's SIERA instance                                                                                                         |
| `country`                | **enumeration**<br/>A valid country from the [country](#enumerations-country) enumeration                                                                                                                             |
| `controlledBy`           | **enumeration**<br/>A valid item from the [asset control](#enumerations-asset-control) enumeration showing who primarily is responsible for the asset, the landlord or the tenant                                     |
| `sector`                 | **enumeration**<br/>A valid item from the [sector](#enumerations-sector) enumeration indicating the property sector this asset belongs to                                                                             |
| `organisationId`         | **integer**<br/>The id value of an organisation which exists in the API-caller's SIERA instance                                                                                                          |
| `fundId`                 | **integer**<br/>The id value of a fund which exists in the authorised user or API-caller's SIERA instance                                                                                                |
| `gia`                    | **integer**<br/>The *Gross Internal Area* (GIA) of the asset, measured in units indicated by the measurement type                                                                                        |
| `nla`                    | **integer**<br/>The *Net Lettable Area* (NLA) of the asset, measured in units indicated by the measurement type                                                                                          |
| `cpa`                    | **integer**<br/> The *Common Part Areas* (CPA) of the asset, measured in units indicated by the measurement type. For example, entrance lobbies, hallways and toilets                                    |
| `ext`                    | **integer**<br/> The external areas of the asset, measured in units indicated by the measurement type. For example, car parks, outside eating areas and greenspace                                       |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `address`                | **string**<br/> The address of the asset                                                                                                                                                                 |
| `city`                   | **string**<br/> The city of the asset                                                                                                                                                                    |
| `postcode`               | **string**<br/> The postcode of the asset                                                                                                                                                                |
| `status`                 | **enumeration**<br/> A valid item from the [asset status](#enumerations-asset-status) enumeration indicates the current state of the asset in relation to its ability to be commercially occupied.                    |
| `dateOfPurchase`         | **datetime**<br/> The date which the asset was purchased                                                                                                                                                 |
| `dateOfSale`             | **datetime**<br/> The date which the asset was sold                                                                                                                                                      |
| `yearOfConstruction`     | **integer**<br/> The year that the asset was built                                                                                                                                                       |
| `yearOfRefurbishment`    | **integer**<br/> The year that the asset was refurbished                                                                                                                                                 |
| `currentAssetValue`      | **integer**<br/> The current value of the asset in Great British Pounds (GBP)                                                                                                                            |
| `longitude`              | **decimal**<br/> The decimal longitude coordinates of the asset location (to 6 decimal places)                                                                                                           |
| `latitude`               | **decimal**<br/> The decimal latitude coordinates of the asset location (to 6 decimal places)                                                                                                            |
| `targetCarbon`           | **float**<br/> The target percentage for the annual reduction of carbon usage for all meters on the asset                                                                                                |
| `targetEnergy`           | **float**<br/> The target percentage for the annual reduction of energy usage for all meters on the asset                                                                                                |
| `targetElectricity`      | **float**<br/> The target percentage for the annual reduction of electricity usage for all meters on the asset                                                                                           |
| `targetFuelsAndThermals` | **float**<br/> The target percentage for the annual reduction of fuels & thermals usage for all meters on the asset                                                                                      |
| `targetWater`            | **float**<br/> The target percentage for the annual reduction of water usage for all meters on the asset                                                                                                 |
| `gresbSector`            | **enumeration**<br/> A valid item from the [GRESB sector](#enumerations-gresb-sector) enumeration indicating how the asset is classified for [GRESB](https://www.gresb.com) certification                             |
| `carParkingSpaces`       | **integer**<br/> The number of car parking spaces available at the asset                                                                                                                                 |
| `fri`                    | **boolean**<br/> A boolean flag indicating if the current lease is [Full Repairing and Insuring (FRI)](https://www.herrington-carmichael.com/full-repairing-and-insuring-lease/) or not                  |
| `assetImageUri`          | **string**<br/> A URI of a downloadable image for the asset                                                                                                                                              |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 500  | Server error                                         |

## Get an asset

```shell
```

> GET /api/v1/assets/{assetId}

```shell
curl https://api.sieraglobal.com/api/v1/assets/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
{
  "assetId": 2,
  "assetName": "Chelsea House, London",
  "assetReference": "CHL-2",
  "country": "UnitedKingdom",
  "controlledBy": "Landlord",
  "sector": "Retail",
  "organisationId": 2,
  "fundId": 3,
  "gia": 1234,
  "nla": 1100,
  "cpa": 15,
  "ext": 100,
  "measurementType": "M2",
  "address": "1, The Way",
  "city": "Townington",
  "postcode": "AB12 3DC",
  "status": "MajorRefurbishment",
  "dateOfPurchase": "1999-01-01T00:00:00.000Z",
  "dateOfSale": "2021-03-14T00:00:00.000Z",
  "yearOfConstruction": 1985,
  "yearOfRefurbishment": 2006,
  "currentAssetValue": 1200000,
  "longitude": 51.507351,
  "latitude": -0.127758,
  "targetCarbon": 5,
  "targetEnergy": 1,
  "targetElectricity": 3,
  "targetFuelsAndThermals": 4,
  "targetWater": 6,
  "gresbSector": "Office",
  "carParkingSpaces": 14,
  "fri": true,
  "assetImageUri": "https://myapi.com/api/v1/Assets/2/AssetImage"
}
```

> Response (201)

**Summary:** Provides a single asset given an ID

### HTTP Request 
`GET /api/v1/assets/{assetId}` 

**Parameters**

| Name    | Located in | Description                            | Required | Type        |
| ------- | ---------- | -------------------------------------- | -------- | ----------- |
| assetId | path       | A valid id of an asset stored in SIERA | Yes      | **integer** |

**Response Body**

The response body will the specified asset which matches the assetId given as a parameter.

| Attribute                | Type and description                                                                                                                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `assetId`                | **integer**<br/>The SIERA-generated id of the asset                                                                                                                                                      |
| `assetName`              | **string**<br/>The name of the asset                                                                                                                                                                     |
| `assetReference`         | **string**<br/>The user-specified asset reference, unique within the API caller's SIERA instance                                                                                                         |
| `country`                | **enumeration**<br/>A valid country from the [country](#enumerations-country) enumeration                                                                                                                             |
| `controlledBy`           | **enumeration**<br/>A valid item from the [asset control](#enumerations-asset-control) enumeration showing who primarily is responsible for the asset, the landlord or the tenant                                     |
| `sector`                 | **enumeration**<br/>A valid item from the [sector](#enumerations-sector) enumeration indicating the property sector this asset belongs to                                                                             |
| `organisationId`         | **integer**<br/>The id value of an organisation which exists in the API-caller's SIERA instance                                                                                                          |
| `fundId`                 | **integer**<br/>The id value of a fund which exists in the authorised user or API-caller's SIERA instance                                                                                                |
| `gia`                    | **integer**<br/>The *Gross Internal Area* (GIA) of the asset, measured in units indicated by the measurement type                                                                                        |
| `nla`                    | **integer**<br/>The *Net Lettable Area* (NLA) of the asset, measured in units indicated by the measurement type                                                                                          |
| `cpa`                    | **integer**<br/> The *Common Part Areas* (CPA) of the asset, measured in units indicated by the measurement type. For example, entrance lobbies, hallways and toilets                                    |
| `ext`                    | **integer**<br/>  The external areas of the asset, measured in units indicated by the measurement type. For example, car parks, outside eating areas and greenspace                                      |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `address`                | **string**<br/> The address of the asset                                                                                                                                                                 |
| `city`                   | **string**<br/> The city of the asset                                                                                                                                                                    |
| `postcode`               | **string**<br/> The postcode of the asset                                                                                                                                                                |
| `status`                 | **enumeration**<br/> A valid item from the [asset status](#enumerations-asset-status) enumeration indicates the current state of the asset in relation to its ability to be commercially occupied.                    |
| `dateOfPurchase`         | **datetime**<br/> The date which the asset was purchased                                                                                                                                                 |
| `dateOfSale`             | **datetime**<br/> The date which the asset was sold                                                                                                                                                      |
| `yearOfConstruction`     | **integer**<br/> The year that the asset was built                                                                                                                                                       |
| `yearOfRefurbishment`    | **integer**<br/> The year that the asset was refurbished                                                                                                                                                 |
| `currentAssetValue`      | **integer**<br/> The current value of the asset in Great British Pounds (GBP)                                                                                                                            |
| `longitude`              | **integer**<br/> The decimal longitude coordinates of the asset location (to 6 decimal places)                                                                                                           |
| `latitude`               | **integer**<br/> The decimal latitude coordinates of the asset location (to 6 decimal places)                                                                                                            |
| `targetCarbon`           | **float**<br/> The target percentage for the annual reduction of carbon usage for all meters on the asset                                                                                                |
| `targetEnergy`           | **float**<br/> The target percentage for the annual reduction of energy usage for all meters on the asset                                                                                                |
| `targetElectricity`      | **float**<br/> The target percentage for the annual reduction of electricity usage for all meters on the asset                                                                                           |
| `targetFuelsAndThermals` | **float**<br/> The target percentage for the annual reduction of fuels & thermals usage for all meters on the asset                                                                                      |
| `targetWater`            | **float**<br/> The target percentage for the annual reduction of water usage for all meters on the asset                                                                                                 |
| `gresbSector`            | **enumeration**<br/> A valid item from the [GRESB sector](#enumerations-gresb-sector) enumeration indicating how the asset is classified for [GRESB](https://www.gresb.com) certification|
| `carParkingSpaces`       | **integer**<br/> The number of car parking spaces available at the asset                                                                                                                                 |
| `fri`                    | **boolean**<br/> A boolean flag indicating if the current lease is [Full Repairing and Insuring (FRI)](https://www.herrington-carmichael.com/full-repairing-and-insuring-lease/) or not                  |
| `assetImageUri`          | **string**<br/> A URI of a downloadable image for the asset                                                                                                                                              |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset id was not found      |
| 500  | Server error                                         |

## Upload a new asset

```shell
```

> POST /api/v1/assets

```shell
curl POST https://api.sieraglobal.com/api/v1/assets \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
  { 
    "assetName": "Chelsea House, London",
    "assetReference": "CHL-2",
    "country": "UnitedKingdom",
    "controlledBy": "Landlord",
    "sector": "Retail",
    "organisationId": 2,
    "fundId": 3,
    "gia": 1234,
    "nla": 1100,
    "cpa": 15,
    "ext": 100,
    "measurementType": "M2",
    "address": "1, The Way",
    "city": "Townington",
    "postcode": "AB12 3DC",
    "status": "MajorRefurbishment",
    "dateOfPurchase": "1999-01-01T00:00:00.000Z",
    "dateOfSale": "2021-03-14T00:00:00.000Z",
    "yearOfConstruction": 1985,
    "yearOfRefurbishment": 2006,
    "currentAssetValue": 1200000,
    "longitude": 51.507351,
    "latitude": -0.127758,
    "targetCarbon": 5,
    "targetEnergy": 1,
    "targetElectricity": 3,
    "targetFuelsAndThermals": 4,
    "targetWater": 6,
    "gresbSector": "Office",
    "carParkingSpaces": 14,
    "fri": true
  }
```

> Response (201)

```json
{
  "assetId": 3
}
```

**Summary:** Uploads a new asset

### HTTP Request 
`POST /api/v1/assets` 


**Request body**

| Attribute                | Type and description                                                                                                                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `assetName`              | **string**<br/>The name of the asset                                                                                                                                                                     |
| `assetReference`         | **string**<br/>The user-specified asset reference, unique within the API caller's SIERA instance                                                                                                         |
| `country`                | **enumeration**<br/>A valid country from the [country](#enumerations-country) enumeration                                                                                                                             |
| `controlledBy`           | **enumeration**<br/>A valid item from the [asset control](#enumerations-asset-control) enumeration showing who primarily is responsible for the asset, the landlord or the tenant                                     |
| `sector`                 | **enumeration**<br/>A valid item from the [sector](#enumerations-sector) enumeration indicating the property sector this asset belongs to                                                                             |
| `organisationId`         | **integer**<br/>The id value of an organisation which exists in the API-caller's SIERA instance                                                                                                          |
| `fundId`                 | **integer**<br/>The id value of a fund which exists in the authorised user or API-caller's SIERA instance                                                                                                |
| `gia`                    | **float**<br/>The *Gross Internal Area* (GIA) of the asset, measured in units indicated by the measurement type. This may be null                                                                        |
| `nla`                    | **float**<br/>The *Net Lettable Area* (NLA) of the asset, measured in units indicated by the measurement type. This may be null                                                                          |
| `cpa`                    | **integer**<br/> The *Common Part Areas* (CPA) of the asset, measured in units indicated by the measurement type. For example, entrance lobbies, hallways and toilets                                    |
| `ext`                    | **integer**<br/>  The external areas of the asset, measured in units indicated by the measurement type. For example, car parks, outside eating areas and greenspace                                      |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `address`                | **string**<br/> The address of the asset                                                                                                                                                                 |
| `city`                   | **string**<br/> The city of the asset                                                                                                                                                                    |
| `postcode`               | **string**<br/> The postcode of the asset                                                                                                                                                                |
| `status`                 | **enumeration**<br/> A valid item from the [asset status](#enumerations-asset-status) indicates the current state of the asset in relation to its ability to be commercially occupied.                                |
| `dateOfPurchase`         | **datetime**<br/> The date which the asset was purchased                                                                                                                                                 |
| `dateOfSale`             | **datetime**<br/> The date which the asset was sold                                                                                                                                                      |
| `yearOfConstruction`     | **integer**<br/> The year that the asset was built                                                                                                                                                       |
| `yearOfRefurbishment`    | **integer**<br/> The year that the asset was refurbished                                                                                                                                                 |
| `currentAssetValue`      | **integer**<br/> The current value of the asset in Great British Pounds (GBP)                                                                                                                            |
| `longitude`              | **decimal**<br/> The decimal longitude coordinates of the asset location (to 6 decimal places)                                                                                                           |
| `latitude`               | **decimal**<br/> The decimal latitude coordinates of the asset location (to 6 decimal places)                                                                                                            |
| `targetCarbon`           | **float**<br/> The target percentage for the annual reduction of carbon usage for all meters on the asset                                                                                                |
| `targetEnergy`           | **float**<br/> The target percentage for the annual reduction of energy usage for all meters on the asset                                                                                                |
| `targetElectricity`      | **float**<br/> The target percentage for the annual reduction of electricity usage for all meters on the asset                                                                                           |
| `targetFuelsAndThermals` | **float**<br/> The target percentage for the annual reduction of fuels & thermals usage for all meters on the asset                                                                                      |
| `targetWater`            | **float**<br/> The target percentage for the annual reduction of water usage for all meters on the asset                                                                                                 |
| `gresbSector`            | **enumeration**<br/> A valid item from the [GRESB sector](#enumerations-gresb-sector) enumeration indicating how the asset is classified for [GRESB](https://www.gresb.com) certification|
| `carParkingSpaces`       | **integer**<br/> The number of car parking spaces available at the asset                                                                                                                                 |
| `fri`                    | **boolean**<br/> A boolean flag indicating if the current lease is [Full Repairing and Insuring (FRI)](https://www.herrington-carmichael.com/full-repairing-and-insuring-lease/) or not                  |

**Response Body**

The response body will a new asset ID relating to the uploaded asset

| Attribute | Type and description                                    |
| --------- | ------------------------------------------------------- |
| `assetId` | **integer**<br/>The SIERA-generated id of the new asset |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 201  | Created                                              |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 500  | Server error                                         |

## Update an asset

```shell
```

> PUT /api/v1/assets/{assetId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/assets/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
  { 
    "assetName": "Birmingham House, London",
    "assetReference": "CHL-3",
    "country": "UnitedKingdom",
    "controlledBy": "Landlord",
    "sector": "Retail",
    "organisationId": 2,
    "fundId": 3,
    "gia": 1234,
    "nla": 1100,
    "cpa": 14,
    "ext": 121,
    "measurementType": "M2",
    "address": "2, The Way",
    "city": "Townington",
    "postcode": "AB12 3DC",
    "status": "MajorRefurbishment",
    "dateOfPurchase": "2000-01-01T00:00:00.000Z",
    "dateOfSale": "2021-03-19T00:00:00.000Z",
    "yearOfConstruction": 1985,
    "yearOfRefurbishment": 2007,
    "currentAssetValue": 1250000,
    "longitude": 51.507351,
    "latitude": -0.127758,
    "targetCarbon": 4,
    "targetEnergy": 3,
    "targetElectricity": 5,
    "targetFuelsAndThermals": 1,
    "targetWater": 6,
    "gresbSector": "Office",
    "carParkingSpaces": 18,
    "fri": false
  }
```

> Response (200)

**Summary:** Updates an existing asset by ID

### HTTP Request 
`PUT /api/v1/assets/{assetId}` 

**Parameters**

| Name    | Located in | Description                                | Required | Type        |
| ------- | ---------- | ------------------------------------------ | -------- | ----------- |
| assetId | path       | The id of the asset to be updated in SIERA | Yes      | **integer** |

**Request body**

| Attribute                | Type and description                                                                                                                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `assetName`              | **string**<br/>The name of the asset                                                                                                                                                                     |
| `assetReference`         | **string**<br/>The user-specified asset reference, unique within the API caller's SIERA instance                                                                                                         |
| `country`                | **enumeration**<br/>A valid country from the [country](#enumerations-country) enumeration                                                                                                                             |
| `controlledBy`           | **enumeration**<br/>A valid item from the [asset control](#enumerations-asset-control) enumeration showing who primarily is responsible for the asset, the landlord or the tenant                                     |
| `sector`                 | **enumeration**<br/>A valid item from the [sector](#enumerations-sector) enumeration indicating the property sector this asset belongs to                                                                             |
| `organisationId`         | **integer**<br/>The id value of an organisation which exists in the API-caller's SIERA instance                                                                                                          |
| `fundId`                 | **integer**<br/>The id value of a fund which exists in the authorised user or API-caller's SIERA instance                                                                                                |
| `gia`                    | **integer**<br/>The *Gross Internal Area* (GIA) of the asset, measured in units indicated by the measurement type                                                                                        |
| `nla`                    | **integer**<br/>The *Net Lettable Area* (NLA) of the asset, measured in units indicated by the measurement type                                                                                          |
| `cpa`                    | **integer**<br/> The *Common Part Areas* (CPA) of the asset, measured in units indicated by the measurement type. For example, entrance lobbies, hallways and toilets                                    |
| `ext`                    | **integer**<br/>  The external areas of the asset, measured in units indicated by the measurement type. For example, car parks, outside eating areas and greenspace                                      |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `address`                | **string**<br/> The address of the asset                                                                                                                                                                 |
| `city`                   | **string**<br/> The city of the asset                                                                                                                                                                    |
| `postcode`               | **string**<br/> The postcode of the asset                                                                                                                                                                |
| `status`                 | **enumeration**<br/> A valid item from the [asset status](#enumerations-asset-status) enumeration indicates the current state of the asset in relation to its ability to be commercially occupied.                    |
| `dateOfPurchase`         | **datetime**<br/> The date which the asset was purchased                                                                                                                                                 |
| `dateOfSale`             | **datetime**<br/> The date which the asset was sold                                                                                                                                                      |
| `yearOfConstruction`     | **integer**<br/> The year that the asset was built                                                                                                                                                       |
| `yearOfRefurbishment`    | **integer**<br/> The year that the asset was refurbished                                                                                                                                                 |
| `currentAssetValue`      | **integer**<br/> The current value of the asset in Great British Pounds (GBP)                                                                                                                            |
| `longitude`              | **decimal**<br/> The decimal longitude coordinates of the asset location (to 6 decimal places)                                                                                                           |
| `latitude`               | **decimal**<br/> The decimal latitude coordinates of the asset location (to 6 decimal places)                                                                                                            |
| `targetCarbon`           | **float**<br/> The target percentage for the annual reduction of carbon usage for all meters on the asset                                                                                                |
| `targetEnergy`           | **float**<br/> The target percentage for the annual reduction of energy usage for all meters on the asset                                                                                                |
| `targetElectricity`      | **float**<br/> The target percentage for the annual reduction of electricity usage for all meters on the asset                                                                                           |
| `targetFuelsAndThermals` | **float**<br/> The target percentage for the annual reduction of fuels & thermals usage for all meters on the asset                                                                                      |
| `targetWater`            | **float**<br/> The target percentage for the annual reduction of water usage for all meters on the asset                                                                                                 |
| `gresbSector`            | **enumeration**<br/> A valid item from the [GRESB sector](#enumerations-gresb-sector) enumeration indicating how the asset is classified for [GRESB](https://www.gresb.com) certification|
| `carParkingSpaces`       | **integer**<br/> The number of car parking spaces available at the asset                                                                                                                                 |
| `fri`                    | **boolean**<br/> A boolean flag indicating if the current lease is [Full Repairing and Insuring (FRI)](https://www.herrington-carmichael.com/full-repairing-and-insuring-lease/) or not                  |
| `assetImageUri`          | **string**<br/> This URI is for the endpoint where the asset image can be downloaded                                                                                                                     |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset id was not found      |
| 500  | Server error                                         |

## Delete an asset 

```shell
```

> DELETE /api/v1/assets/{assetId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/assets/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing asset by ID

### HTTP Request 
`DELETE /api/v1/assets/{assetId}` 

**Parameters**

| Name    | Located in | Description                                | Required | Type        |
| ------- | ---------- | ------------------------------------------ | -------- | ----------- |
| assetId | path       | The id of the asset to be deleted in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset id was not found      |
| 500  | Server error                                         |

## Get all meters for an asset

```shell
```

> GET /api/v1/assets/{assetId}/meters

```shell
curl https://api.sieraglobal.com/api/v1/assets/2/meters \
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
    "controlledBy": "Landlord",
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
  }
]
```

**Summary** Provides all meters given an asset ID

### HTTP Request 
`GET /api/v1/assets/{assetId}/meters` 

**Parameters**

| Name    | Located in | Description                            | Required | Type        |
| ------- | ---------- | -------------------------------------- | -------- | ----------- |
| assetId | path       | A valid id of an asset stored in SIERA | Yes      | **integer** |


**Response Body**

The response body will be a list of meters which are associated with the asset specified by the assetId parameter.

| Attribute                | Type and description                                                                                                                                                                                                                                                     |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `meterId`                | **integer**<br/>The SIERA-generated id of the meter                                                                                                                                                                                                                      |
| `assetId`                | **integer**<br/>The SIERA-generated id of the associated asset                                                                                                                                                                                                           |
| `unitId`                 | **integer**<br/>The SIERA-generated id of any associated unit                                                                                                                                                                                                            |
| `mpan`                   | **string**<br/>The meter point administration number (MPAN) of the meter                                                                                                                                                                                                 |
| `serialNumber`           | **string**<br/>The serial number of the meter                                                                                                                                                                                                                            |
| `comment`                | **string**<br/>A free-text description relating to the meter                                                                                                                                                                                                             |
| `supplier`               | **string**<br/>Any utilities supplier related to the meter                                                                                                                                                                                                               |
| `areaCovered`            | **enumeration**<br/>A valid area of the property which this meter covers, from the [area covered](#enumerations-area-covered) enumeration                                                                                                                                             |
| `controlledBy`           | **enumeration**<br/>A valid item from the [asset control](#enumerations-asset-control) enumeration showing who primarily pays for the energy from this meter, the landlord or the tenant                                                                                              |
| `floorAreaServed`        | **integer**<br/>The floor area covered by this meter                                                                                                                                                                                                                     |
| `meterType`              | **enumeration**<br/>A valid utility of the meter from the [meter type](#enumerations-meter-type) enumeration                                                                                                                                                                          |
| `generationType`         | **enumeration**<br/>A valid generation type of the meter from the [generation type](#enumeration-generation-type) enumeration                                                                                                                                                        |
| `measurementType`        | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>)                                                                 |
| `locationCarbonFactorId` | **integer**<br/>The id value of an location-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                    |
| `marketCarbonFactorId`   | **integer**<br/>The id value of an market-based carbon factor Id which exists in the API-caller's SIERA instance, or one of the [default carbon factors](#carbon-factors) provided by Evora                                                                      |
| `unitRateId`             | **integer**<br/>The id value of a cost unit rate Id which exists in the API-caller's SIERA instance, or one of the [default unit rates](#unit-rates) provided by Evora                                                                                           |
| `isActive`               | **boolean**<br/>A boolean flag indicating if this meter is considered active and currently in use or not.                                                                                                                                                                |
| `isAMR`                  | **boolean**<br/>A boolean flag indicating if this meter's readings are being retrieved by automatic meter reading or not.                                                                                                                                                |
| `isSubmeter`             | **boolean**<br/>A boolean flag indicating if this meter isa sub-meter or not                                                                                                                                                                                             |
| `isValidated`            | **boolean**<br/>A boolean flag indicating if this meter has been validated or not.                                                                                                                                                                                       |
| `isROC`                  | **boolean**<br/>A boolean flag indicating if this meter has an [Renewables Obligation Certificate](https://www.ofgem.gov.uk/environmental-and-social-schemes/renewables-obligation-ro) generation meter which measures total electricity produced by solar panel or not. |
| `isFIT`                  | **boolean**<br/>A boolean flag indicating if this meter is a Feed-In-Time tariff (relating to solar panels) or not.                                                                                                                                                      |
| `isCCA`                  | **boolean**<br/>A boolean flag indicating if this meter is part of a [Community Choice Aggregation](https://en.wikipedia.org/wiki/Community_Choice_Aggregation) or not.                                                                                                  |
| `isEUETS`                | **boolean**<br/>A boolean flag indicating if this meter is part of the [EU Energy Trading System](https://ec.europa.eu/clima/policies/ets_en) or not.                                                                                                                    |
| `hasHalfHourData`        | **boolean**<br/>A boolean flag indicating if this meter has received half-hourly data or not.                                                                                                                                                                            |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset was not found         |
| 500  | Server error                                         |

## Get all waste destinations for an asset

```shell
```

> GET /api/v1/assets/{assetId}/wastedestinations

```shell
curl https://api.sieraglobal.com/api/v1/assets/2/wastedestinations \
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

**Summary:** Provides all waste destinations given an asset ID

### HTTP Request 
`GET /api/v1/assets/{assetId}/wastedestinations` 


**Response Body**

The response body will be a list of waste destinations which are associated with the asset specified by the assetId parameter.

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

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset was not found         |
| 500  | Server error                                         |


## Get all action plans for an asset

```shell
```

> GET /api/v1/assets/{assetId}/actionplans

```shell
curl https://api.sieraglobal.com/api/v1/assets/2/actionplans \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json

[
    {
        "actionId": 2,
        "assetId": 2,
        "actionDescription": "Upgrade lighting to LED",
        "impact": "Energy",
        "approved": true,
        "status": "AgreedActions",
        "current": 350,
        "target": 200,
        "cost": "Low",
        "costType": "RevenueServiceCharge",
        "scope": "WholeBuilding",
        "manager": "Jeff Parsons",
        "completion": "",
        "dueDate": "9/1/2022",
        "currency": "GBP",
        "utilityType": "NotApplicable",
        "performanceMeasure": "InstallationOfHighEfficiencyEquipment",
        "targetUsagePercentage": 42.86
    },
    {
        "actionId": 3,
        "assetId": 2,
        "actionDescription": "Replace southfacing windows with high-efficiency glazing",
        "impact": "Energy",
        "approved": true,
        "status": "AgreedActions",
        "current": 600,
        "target": 300,
        "cost": "12000",
        "costType": "RevenueServiceCharge",
        "scope": "WholeBuilding",
        "manager": "Jeff Parsons",
        "completion": "",
        "dueDate": "9/1/2022",
        "currency": "GBP",
        "utilityType": "NotApplicable",
        "performanceMeasure": "WindowReplacements",
        "targetUsagePercentage": 50
    },
]
```

**Summary:** Provides all action plans given an asset ID

### HTTP Request 
`GET /api/v1/assets/{assetId}/actionplans` 

**Parameters**

| Name    | Located in | Description                            | Required | Type        |
| ------- | ---------- | -------------------------------------- | -------- | ----------- |
| assetId | path       | A valid id of an asset stored in SIERA | Yes      | **integer** |

**Response Body**

The response body will be a list of action plans which are associated with the asset specified by the assetId parameter.

| Attribute               | Type and description                                                                                                                   |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `actionId`              | **integer**<br/>The id of the action plan                                                                                              |
| `assetId`               | **integer**<br/>The id of the asset                                                                                                    |
| `actionDescription`     | **string**<br/>A description of the action plan                                                                                        |
| `impact`                | **string**<br/>The utility or utility group affected by the action                                                                     |
| `approved`              | **boolean**<br/>A boolean flag to indicate if the action plan has been approved or not                                                 |
| `status`                | **enumeration**<br/>A valid action status from the [action status](#enumerations-action-status) enumeration                                         |
| `current`               | **float**<br/>The current usage amount related to this action                                                                          |
| `target`                | **float**<br/>A target usage the action is hoped to achieve                                                                            |
| `cost`                  | **string**<br/>A text description of the costs of the action. This can be a number amount or relative description such as high or low. |
| `costType`              | **enumeration**<br/>A valid cost type from the [action cost type](#enumerations-action-cost-type) enumeration                                       |
| `scope`                 | **enumeration**<br/>A valid floor area scope from the [action scope](#enumerations-action-scope) enumeration                                        |
| `manager`               | **string**<br/>The name of a person who is considered the manager of this action                                                       |
| `completion`            | **datetime**<br/>The actual completion date of the action, in the format *m/d/yyyy*                                                    |
| `dueDate`               | **datetime**<br/>The expected completion date of the action, in the format *m/d/yyyy*                                                  |
| `currency`              | **string**<br/>The currency of the costs related to the action, of GBP, USD or EUR.                                                    |
| `utilityType`           | **enumeration**<br/>A valid utility from the [action utility](#enumerations-action-utility) enumeration                                             |
| `performanceMeasure`    | **enumeration**<br/>A valid measure description from the [action measure description](#enumerations-action-measure-description) enumeration         |
| `targetUsagePercentage` | **float**<br/>A read-only percentage change between the current and target values of the action                                        |


**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset was not found         |
| 500  | Server error                                         |


## Get all asset units for an asset

```shell
```

> GET /api/v1/assets/{assetId}/assetunits

```shell
curl https://api.sieraglobal.com/api/v1/assets/2/assetsunits \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
[
  {
    "unitId": 12,
    "unitName": "Unit A",
    "unitReference": "TAC-234",
    "occupier": "Pets At Home",
    "actionNotes": "",
    "gia": 1100,
    "nla": 900,
    "measurementUnit": "M2",
    "vacant": false,
    "leaseStart": "2020-12-17T12:00:00.000Z",
    "leaseLength": 24,
    "leaseExpiry": "2022-12-17T12:00:00.000Z",
    "leaseBreak": "",
    "erv": 1200,
    "fri": false,
    "epcExempt": false
  },
  {
    "unitId": 13,
    "unitName": "Unit B",
    "unitReference": "TAC-235",
    "occupier": "Asda Home",
    "actionNotes": "",
    "gia": 1050,
    "nla": 800,
    "measurementUnit": "M2",
    "vacant": false,
    "leaseStart": "2021-11-21T12:00:00.000Z",
    "leaseLength": 24,
    "leaseExpiry": "2023-12-21T12:00:00.000Z",
    "leaseBreak": "2022-12-17T12:00:00.000Z",
    "erv": 900,
    "fri": false,
    "epcExempt": false
  }
]
```

**Summary:** Provides all asset units given an asset ID

### HTTP Request 
`GET /api/v1/assets/{assetId}/assetunits` 

**Parameters**

| Name    | Located in | Description                                  | Required | Type        |
| ------- | ---------- | -------------------------------------------- | -------- | ----------- |
| assetId | path       | The id of the asset associated with the unit | Yes      | **integer** |

**Response Body**

The response body will include a list of all assets in SIERA which are associated with the asset specified by the assetId parameter.

| Attribute         | Type and description                                                                                                                                                                                     |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `unitId`          | **integer**<br/>The SIERA-generated id of the asset unit                                                                                                                                                 |
| `unitName`        | **string**<br/>The name of the asset unit                                                                                                                                                                |
| `unitReference`   | **string**<br/>The asset unit reference                                                                                                                                                                  |
| `occupier`        | **string**<br/>The name of the current occupier of the unit                                                                                                                                              |
| `gia`             | **float**<br/>The *Gross Internal Area* (GIA) of the asset, measured in units indicated by the measurement unit. This may be null                                                                        |
| `nla`             | **float**<br/>The *Net Lettable Area* (NLA) of the asset, measured in units indicated by the measurement unit. This may be null                                                                          |
| `measurementUnit` | **enumeration**<br/>The unit of measurement used to indicate floor area of this asset. Must be a valid item from the [measurement unit](#enumerations-measurement-unit) enumeration (m<sup>2</sup> or ft<sup>2</sup>) |
| `leaseStart`      | **datetime**<br/>The start date of the tenant of this unit's lease                                                                                                                                       |
| `leaseLength`     | **integer**<br/>The length in months of the tenant of this unit's lease                                                                                                                                  |
| `leaseExpiry`     | **datetime**<br/>The expiry date of the tenant of this unit's lease                                                                                                                                      |
| `leaseBreak`      | **datetime**<br/>The start date of a break in the tenant of this unit's lease                                                                                                                            |
| `erv`             | **float**<br/>The estimated rental value (ERV) of this unit                                                                                                                                              |
| `fri`             | **boolean**<br/>A boolean flag indicating if the current lease is [Full Repairing and Insuring (FRI)](https://www.herrington-carmichael.com/full-repairing-and-insuring-lease/) or not                   |
| `epcExempt`       | **boolean**<br/>A boolean flag indicating if this unit has an [EPC exemption](https://www.gov.uk/energy-performance-certificate-commercial-property/exemptions) or not                                   |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset was not found         |
| 500  | Server error                                         |

## Get an asset image

**Summary** The response will return a file, if one is found for the given asset ID.

### HTTP Request 
`GET /api/v1/assets/{assetId}/assetimage` 

**Parameters**

| Name    | Located in | Description                            | Required | Type        |
| ------- | ---------- | -------------------------------------- | -------- | ----------- |
| assetId | path       | A valid id of an asset stored in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 200  | OK                                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset was not found         |
| 500  | Server error                                         |

## Validation rules

When uploading new assets or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for assets are:

1. When uploading a new asset, the **assetId** must be 0 or null.
2. When updating an asset, the **assetId** must be of an existing asset in SIERA.
3. The **assetReference** must be unique. Validation will fail if any other asset has the same reference.
4. The **organisationId** must already exist in SIERA.
5. The **fundId** must already exist in SIERA.
6. The **dateOfPurchase** (if present) must be before the **dateOfSale** (if present).