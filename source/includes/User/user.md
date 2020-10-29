# User

## User Overview

A User in OpenMRS is an account that a person may use to log into the system.

The real-life person is represented by a Person record in OpenMRS, and a person may have more than one user account. If you want a patient to be able to view her record in OpenMRS, then you need to create a user account and link it to the patient's person record.

## Available operations for User

1. [List users](#list-user)
2. [Create a user](#create-a-user)
3. [Update a user](#update-a-user)
4. [Delete a user](#delete-a-user)

## List user

### List all non-retired users.


> Get all non-retired Users 

```shell
GET /user?
q=admin
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/user?q=admin")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();

```

  Quickly filter users with given query parameters. Returns a `404 Not Found` status if the user does not exist.
  If not logged in to perform this action, a `401 Unauthorized` status is returned.
  

### Query Parameters

| Parameter | Type           | Description                           |
| --------- | -------------- | ------------------------------------- |
| _q_       | `Search Query` | Filter users by username or system ID |


### Get user by UUID.

> Get User by UUID

```shell
GET /user/:target_user_uuid
```

```java

1. Here the target UUID used is of the admin user.  

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();

```

  Retrieve a user by its UUID. Returns a `404 Not Found` status if the user does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a user


> Create a new User

```shell
POST /user
{
   "username":"demoUser",
   "password":"Password123",
   "person":{
      "names":[
         {
            "givenName":"Demo",
            "familyName":"User"
         }
      ],
      "gender":"M",
      "birthdate":"1997-09-02",
      "addresses":[
         {
            "address1":"30, Vivekananda Layout, Munnekolal,Marathahalli",
            "cityVillage":"Bengaluru",
            "country":"India",
            "postalCode":"560037"
         }
      ]
   },
   "systemId":"systemId"
}

```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"username\": \"demoUser\",\r\n    \"password\": \"Password123\",\r\n    \"person\" :\r\n        {\r\n        \"names\": [\r\n            {\r\n                \"givenName\": \"Demo\",\r\n                \"familyName\": \"User\"\r\n            }\r\n        ],\r\n        \"gender\": \"M\",\r\n        \"birthdate\": \"1997-09-02\",\r\n        \"addresses\": [\r\n        {\r\n         \"address1\": \"30, Vivekananda Layout, Munnekolal,Marathahalli\",\r\n        \"cityVillage\": \"Bengaluru\",\r\n        \"country\": \"India\",\r\n        \"postalCode\": \"560037\"\r\n        }\r\n    ]\r\n        },\r\n\"systemId\": \"systemId\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/user")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();

```

- For convenience, the person's information can be included in order to create the corresponding person record at the same time as their user record. When creating a user record for an existing person, the existing person must only be referenced by UUID. If you are not logged in to perform this action,
a `401 Unauthorized` status is returned.
- The password should be minimum 8 chars long with atleast one lower and upper character alphabet along with a numeral.
- Some properties are not allowed to be set including name and description therefore arent included in the API usage examples.

### Attributes

Parameter | Type | Description
--- | --- | ---
*name* | `String` | Name of the user
*description* | `String | Description of the user
*username* | `String | username of the user
*password* | `String | password of the user
*person* | `String` | person resource associated with the user
*systemId* | `String` | a unique identifier assigned to each user
*roles* | `Array[] : role` | a list of roles attributed to the user
*userProperties* | `JSON Object`| A set of key value pairs. Used to store user specific data
*secretQuestion* | `String` | A secret question chosen by the user


## Update a user


> Update a user using its UUID

```shell
POST /user/:target_user_uuid
{
   "username":"demoUser",
   "password":"Password123",
   "person":{
      "names":[
         {
            "givenName":"Demo",
            "familyName":"User"
         }
      ],
      "gender":"M",
      "birthdate":"1997-09-02",
      "addresses":[
         {
            "address1":"30, Vivekananda Layout, Munnekolal,Marathahalli",
            "cityVillage":"Bengaluru",
            "country":"India",
            "postalCode":"560037"
         }
      ]
   },
   "systemId":"systemId"
}

```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"username\": \"demoUser\",\r\n    \"password\": \"Password123\",\r\n    \"person\" :\r\n        {\r\n        \"names\": [\r\n            {\r\n                \"givenName\": \"Demo\",\r\n                \"familyName\": \"User\"\r\n            }\r\n        ],\r\n        \"gender\": \"M\",\r\n        \"birthdate\": \"1997-09-02\",\r\n        \"addresses\": [\r\n        {\r\n         \"address1\": \"30, Vivekananda Layout, Munnekolal,Marathahalli\",\r\n        \"cityVillage\": \"Bengaluru\",\r\n        \"country\": \"India\",\r\n        \"postalCode\": \"560037\"\r\n        }\r\n    ]\r\n        },\r\n\"systemId\": \"systemId\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/user/564b2790-0508-11e3-8ffd-0800200c9a66
")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();

```
- Update a target user with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
  status if the user does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.
    
### Attributes

  Parameter | Type | Description
  --- | --- | ---
  *name* | `String` | Name of the user
  *description* | `String | Description of the user
  *username* | `String | username of the user
  *password* | `String | password of the user
  *person* | `String` | person resource associated with the user
  *systemId* | `String` | a unique identifier assigned to each user
  *roles* | `Array[] : role` | a list of roles attributed to the user
  *userProperties* | `JSON Object`| A set of key value pairs. Used to store user specific data
  *secretQuestion* | `String` | A secret question chosen by the user


## Delete a user

> Delete a user using its UUID

```shell
DELETE /user/:target_user_uuid?purge=true
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/user/b953d87d-7e67-47b9-ad1e-fa8b7cdaea4d?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();

```



- Delete or retire a target user by its UUID. Returns a `404 Not Found` status if the user does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

| Parameter | Type      | Description                                       |
| --------- | --------- | ------------------------------------------------- |
| _purge_   | `Boolean` | The resource will be voided unless purge = ‘true’ |

