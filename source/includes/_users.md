# Users

The User endpoints allow you to download users data from SIERA. You can also upload new users, update users or delete them from a given instance in SIERA.

## Get all users

```shell
```

> GET /api/v1/admin/users

```shell
curl https://api.sieraglobal.com/api/v1/admin/users \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
[
  {
    "userId": "ADD3DFF1-26E8-4C77-9000-1EC11CCEFBBD",
    "image": null,
    "userName": "Admin Test User",
    "company": "SIERA Root Instance",
    "role": "Admin",
    "numberOfAssets": 20,
    "lastLogin": null
  },{
    "userId": "A0B13F79-44AB-4A31-932C-244D6FA7F7F0",
    "image": null,
    "userName": "Test User 1",
    "company": "SIERA Root Instance",
    "role": "Users",
    "numberOfAssets": 5,
    "lastLogin": null
  },{
    "userId": "056ECBE4-4599-4D8A-8574-620B86224DBD",
    "image": null,
    "userName": "Test User 2",
    "company": "SIERA Root Instance",
    "role": "Users",
    "numberOfAssets": 8,
    "lastLogin": null
  }
]
```

**Summary:** Provides a list of all users in the API caller's instance in SIERA.

### HTTP Request 
`GET /api/v1/admin/users` 


**Response Body**

The response body will include a list of all users in the API caller's instance in SIERA.

| Attribute | Type and description |
| ---- | ----------- |
| `userId` | **string**<br/>The SIERA-generated id of the user |
| `image` | **string**<br/>The user image |
| `userName` | **string**<br/>The user-specified user name, unique within the API caller's SIERA instance |
| `company` | **string**<br/> The user's company name is related to |
| `role` | **string**<br/> The user's role is related to |
| `numberOfAssets` | **integer**<br/> Count of the assets accessed to |
| `lastLogin` | **datetime**<br/> Last logged in to the SIERA |

## Upload a new user

```shell
```

> POST /api/v1/admin/users

```shell
curl POST https://api.sieraglobal.com/api/v1/admin/users \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
{
  "email": "testadmin@test.com",
  "roleId": "056ECBE4-4599-4D8A-8574-620B86224DBD",
  "userName": "Test User 2"
}
```

> Response (200)

**Summary:** Uploads a new user

### HTTP Request 
`POST /api/v1/admin/users` 


**Request body**

| Attribute | Type and description |
| ---- | ----------- |
| `email` | **string**<br/>The email of the user |
| `roleId` | **string**<br/>The id value of an role which exists in the API-caller's SIERA instance |
| `userName` | **string**<br/>The user-specified user name, unique within the API caller's SIERA instance |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Created |
| 400 | Validation failure, one or more of the enumerations were not correctly identified |
| 401 | Not found, the specified user id does not exist in the caller's instance or was not found |
| 500 | Server error |

## Get an user

```shell
```

> GET /api/v1/admin/users/{userId}

```shell
curl https://api.sieraglobal.com/api/v1/admin/users/A0B13F79-44AB-4A31-932C-244D6FA7F7F0 \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

> Response (200)

```json
{
    "userId": "A0B13F79-44AB-4A31-932C-244D6FA7F7F0",
    "image": null,
    "userName": "Test User 1",
    "company": "SIERA Root Instance",
    "role": "Users",
    "numberOfAssets": 5,
    "lastLogin": null
}
```

> Response (200)

**Summary:** Provides a single user given an ID

### HTTP Request 
`GET /api/v1/admin/users/{userId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | A valid id of an user stored in SIERA | Yes | **string** |

**Response Body**

The response body will the specified user which matches the userId given as a parameter.

| Attribute | Type and description |
| ---- | ----------- |
| `userId` | **string**<br/>The SIERA-generated id of the user |
| `image` | **string**<br/>The user image |
| `userName` | **string**<br/>The user-specified user name, unique within the API caller's SIERA instance |
| `company` | **string**<br/> The user's company name is related to |
| `role` | **string**<br/> The user's role is related to |
| `numberOfAssets` | **integer**<br/> Count of the assets accessed to |
| `lastLogin` | **datetime**<br/> Last logged in to the SIERA |

## Update an user

```shell
```

> PUT /api/v1/admin/users/{userId}

```shell
curl PUT https://api.sieraglobal.com/api/v1/admin/users/A0B13F79-44AB-4A31-932C-244D6FA7F7F0 \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -V "Content-Type: application/json" \
  -d @- <<JSON
{
  "email": "testadmin@test.com",
  "roleId": "056ECBE4-4599-4D8A-8574-620B86224DBD",
  "userName": "Test User 2"
}
```

> Response (200)

**Summary:** Updates an existing user by ID

### HTTP Request 
`PUT /api/v1/admin/users/{userId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | The id of the user to be updated in SIERA | Yes | **string** |

**Request body**

| Attribute | Type and description |
| ---- | ----------- |
| `email` | **string**<br/>The email of the user |
| `roleId` | **string**<br/>The id value of an role which exists in the API-caller's SIERA instance |
| `userName` | **string**<br/>The user-specified user name, unique within the API caller's SIERA instance |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Created |
| 400 | Validation failure, one or more of the enumerations were not correctly identified |
| 401 | Not found, the specified user id does not exist in the caller's instance or was not found |
| 500 | Server error |

## Delete an user 

```shell
```

> DELETE /api/v1/admin/users/{userId}

```shell
curl -X DELETE https://api.sieraglobal.com/api/v1/admin/users/A0B13F79-44AB-4A31-932C-244D6FA7F7F0 \
  -H "Authorization: Bearer $ACCESS_TOKEN" 
```

> Response (200)

**Summary:** Deletes an existing user by ID

### HTTP Request 
`DELETE /api/v1/admin/users/{userId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | The id of the user to be deleted in SIERA | Yes | **string** |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Not found, the specified user id does not exist in the caller's instance or was not found |
| 500 | Server error |