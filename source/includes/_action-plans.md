# Action Plans

The action plan endpoints allows uploading of action plan information relating to assets such as ESG-related initiatives and improvement programs. The endpoints provide the ability to download all actions, update individual actions, and delete actions.

## Get all action plans

```shell
```

> GET /api/v1/actionplans

```shell
curl https://api.sieraglobal.com/api/v1/actionplans \
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

**Summary:** Provides a list of all the action plans associated with the specified asset

### HTTP Request 
`GET /api/v1/actionplans` 

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

| Code | Description                                            |
| ---- | ------------------------------------------------------ |
| 200  | OK                                                     |
| 401  | Unauthorised, the header token expired or is missing   |
| 404  | Not found, the specified waste record id was not found |
| 500  | Server error                                           |


## Get an action plan

```shell
```

> GET /api/v1/actionplans/{actionId}

```shell
curl https://api.sieraglobal.com/api/v1/actionplans/6 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
{
  "actionId": 6,
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
}
```

**Summary:** Provides an action plan

### HTTP Request 
`GET /api/v1/actionplans/{actionId}` 

**Parameters**

| Name     | Located in | Description                                  | Required | Type        |
| -------- | ---------- | -------------------------------------------- | -------- | ----------- |
| actionId | path       | A valid id of an action plan stored in SIERA | Yes      | **integer** |

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

| Code | Description                                            |
| ---- | ------------------------------------------------------ |
| 200  | OK                                                     |
| 401  | Unauthorised, the header token expired or is missing   |
| 404  | Not found, the specified waste record id was not found |
| 500  | Server error                                           |



## Upload a new action plan

```shell
```

> POST /api/v1/actionplans

```shell
curl POST https://api.sieraglobal.com/api/v1/actionplans \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON  
  {
      "assetId": 2,
      "actionDescription": "Complete reinsulation of external wall",
      "impact": "Energy",
      "approved": true,
      "status": "AgreedActions",
      "current": 7900,
      "target": 5000,
      "cost": "34500",
      "costType": "RevenueServiceCharge",
      "scope": "WholeBuilding",
      "manager": "Sue Brown",
      "completion": "",
      "dueDate": "5/1/2022",
      "currency": "GBP",
      "utilityType": "NotApplicable",
      "performanceMeasure": "WallOrRoofInsulation"
    }
```

> Response (201)

```json
{
  "actionId": 5
}
```

**Summary:** Upload a new action plan

### HTTP Request 
`POST /api/v1/actionplans` 


**Request body**

| Attribute            | Type and description                                                                                                                   |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `assetId`            | **integer**<br/>The id of the asset                                                                                                    |
| `actionDescription`  | **string**<br/>A description of the action plan                                                                                        |
| `impact`             | **string**<br/>The utility or utility group affected by the action                                                                     |
| `approved`           | **boolean**<br/>A boolean flag to indicate if the action plan has been approved or not                                                 |
| `status`             | **enumeration**<br/>A valid action status from the [action status](#enumerations-action-status) enumeration                                         |
| `current`            | **float**<br/>The current usage amount related to this action                                                                          |
| `target`             | **float**<br/>A target usage the action is hoped to achieve                                                                            |
| `cost`               | **string**<br/>A text description of the costs of the action. This can be a number amount or relative description such as high or low. |
| `costType`           | **enumeration**<br/>A valid cost type from the [action cost type](#enumerations-action-cost-type) enumeration                                       |
| `scope`              | **enumeration**<br/>A valid floor area scope from the [action scope](#enumerations-action-scope) enumeration                                        |
| `manager`            | **string**<br/>The name of a person who is considered the manager of this action                                                       |
| `completion`         | **datetime**<br/>The actual completion date of the action, in the format *m/d/yyyy*                                                    |
| `dueDate`            | **datetime**<br/>The expected completion date of the action, in the format *m/d/yyyy*                                                  |
| `currency`           | **string**<br/>The currency of the costs related to the action, of GBP, USD or EUR.                                                    |
| `utilityType`        | **enumeration**<br/>A valid utility from the [action utility](#enumerations-action-utility) enumeration                                             |
| `performanceMeasure` | **enumeration**<br/>A valid measure description from the [action measure description](#enumerations-action-measure-description) enumeration         |

**Response Body**

The response body will a new action plan ID relating to the uploaded action plan

| Attribute  | Type and description                                          |
| ---------- | ------------------------------------------------------------- |
| `actionId` | **integer**<br/>The SIERA-generated id of the new action plan |

**Responses**

| Code | Description                                          |
| ---- | ---------------------------------------------------- |
| 201  | Created                                              |
| 400  | Validation failure                                   |
| 401  | Unauthorised, the header token expired or is missing |
| 404  | Not found, the specified asset id was not found      |
| 500  | Server error                                         |



## Update an action plan

```shell
```

> PUT /api/v1/actionplans/{actionId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/actionplans/2 \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
  {
      "actionId": 2,
      "assetId": 2,
      "actionDescription": "Complete reinsulation of external wall",
      "impact": "Energy",
      "approved": true,
      "status": "AgreedActions",
      "current": 9100,
      "target": 5000,
      "cost": "29500",
      "costType": "RevenueServiceCharge",
      "scope": "WholeBuilding",
      "manager": "Sue Brown",
      "completion": "",
      "dueDate": "8/1/2022",
      "currency": "GBP",
      "utilityType": "NotApplicable",
      "performanceMeasure": "WallOrRoofInsulation"
    }
```

> Response (200)

**Summary:** Updates an existing action plan by ID

### HTTP Request 
`PUT /api/v1/actionplan/{actionId}` 

**Parameters**

| Name     | Located in | Description                                  | Required | Type        |
| -------- | ---------- | -------------------------------------------- | -------- | ----------- |
| actionId | path       | A valid id of an action plan stored in SIERA | Yes      | **integer** |

**Request body**

| Attribute            | Type and description                                                                                                                   |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `actionId`           | **integer**<br/>The id of the action plan                                                                                              |
| `assetId`            | **integer**<br/>The id of the asset                                                                                                    |
| `actionDescription`  | **string**<br/>A description of the action plan                                                                                        |
| `impact`             | **string**<br/>The utility or utility group affected by the action                                                                     |
| `approved`           | **boolean**<br/>A boolean flag to indicate if the action plan has been approved or not                                                 |
| `status`             | **enumeration**<br/>A valid action status from the [action status](#enumerations-action-status) enumeration                                         |
| `current`            | **float**<br/>The current usage amount related to this action                                                                          |
| `target`             | **float**<br/>A target usage the action is hoped to achieve                                                                            |
| `cost`               | **string**<br/>A text description of the costs of the action. This can be a number amount or relative description such as high or low. |
| `costType`           | **enumeration**<br/>A valid cost type from the [action cost type](#enumerations-action-cost-type) enumeration                                       |
| `scope`              | **enumeration**<br/>A valid floor area scope from the [action scope](#enumerations-action-scope) enumeration                                        |
| `manager`            | **string**<br/>The name of a person who is considered the manager of this action                                                       |
| `completion`         | **datetime**<br/>The actual completion date of the action, in the format *m/d/yyyy*                                                    |
| `dueDate`            | **datetime**<br/>The expected completion date of the action, in the format *m/d/yyyy*                                                  |
| `currency`           | **string**<br/>The currency of the costs related to the action, of GBP, USD or EUR.                                                    |
| `utilityType`        | **enumeration**<br/>A valid utility from the [action utility](#enumerations-action-utility) enumeration                                             |
| `performanceMeasure` | **enumeration**<br/>A valid measure description from the [action measure description](#enumerations-action-measure-description) enumeration         |


**Responses**

| Code | Description                                           |
| ---- | ----------------------------------------------------- |
| 201  | Created                                               |
| 400  | Validation failure                                    |
| 401  | Unauthorised, the header token expired or is missing  |
| 404  | Not found, the specified action plan id was not found |
| 500  | Server error                                          |

## Delete a action plan 

```shell
```

> DELETE /api/v1/actionplans/{actionId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/actionplans/4 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing action plan by ID

### HTTP Request 
`DELETE /api/v1/actionplans/{actionId}` 

**Parameters**

| Name     | Located in | Description                                      | Required | Type        |
| -------- | ---------- | ------------------------------------------------ | -------- | ----------- |
| actionId | path       | The id of the action plan to be deleted in SIERA | Yes      | **integer** |

**Responses**

| Code | Description                                           |
| ---- | ----------------------------------------------------- |
| 200  | OK                                                    |
| 401  | Unauthorised, the header token expired or is missing  |
| 404  | Not found, the specified action plan id was not found |
| 500  | Server error                                          |

## Validation rules

When uploading new waste destinations or updating existing, SIERA will apply the following rules and if they are not met, a response of 400 will be returned with an error message and the field causing the validation failure.

The validation requirements for waste detinations are:

1. When uploading a new action plan, the **actionId** must be 0 or null. 
2. When updating an action plan, the **actionId** must be of an existing action plan in SIERA.
3. The **assetId** must exist in SIERA.
4. The action must not be currently part of a survey which has been submitted. If this is encountered contact [SIERA Support](mailto:support@sieraglobal.com).
5. The **impact** and **performanceMeasure** must be in a valid combination (as some measures may only apply to certain utilities or impacts). The table below details the valid combinations

| Impact           | Measure                                       |
| ---------------- | --------------------------------------------- |
| Energy           | AMR                                           |
| Energy           | AutomationSystemUpgradesOrReplacements        |
| Energy           | InstallationOfHighEfficiencyEquipment         |
| Energy           | InstallationOfOnSiteRenewableEnergy           |
| Energy           | ManagementSystemsUpgradesOrReplacements       |
| Energy           | OccupierEngagementOrInformationalTechnologies |
| Energy           | TechnicalAssessmentEnergy                     |
| Energy           | WallOrRoofInsulation                          |
| Energy           | WindowReplacements                            |
| Water            | CoolingTower                                  |
| Water            | DripOrSmartIrrigation                         |
| Water            | HighEfficiencyOrDryFixtures                   |
| Water            | LeakDetectionSystem                           |
| Water            | MeteringOfWaterSubsystems                     |
| Water            | OnSiteWasteWaterTreatment                     |
| Water            | ReuseOfStormWaterOrGreyWater                  |
| Waste            | CompostingLandscapeOrFoodWaste                |
| Water            | DroughtTolerantOrNativeLandscaping            |
| Waste            | OngoingWastePerformanceMonitoring             |
| Waste            | OnSiteWasteWaterTreatment                     |
| Waste            | Recycling                                     |
| Waste            | WasteStreamAudit                              |
| TenantEngagement | BuildingSpecificCommunication                 |
| TenantEngagement | FeedbackSessions                              |
| TenantEngagement | Other                                         |
| TenantEngagement | SocialMediaOnlinePlatform                     |
| TenantEngagement | TenantMeetingsIncludingSustainability         |
| TenantEngagement | TenantsReceiveFeedbackOnPerformance           |
| TenantEngagement | TenantSustainabilityEvents                    |
| TenantEngagement | TenantSustainabilityGuide                     |
| TenantEngagement | TenantSustainabilityTraining                  |