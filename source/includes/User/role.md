# Role

## Role Overview

A **Role** represents a group of privileges in the system. Roles may inherit privileges from other roles, and users may have one or more roles.

## Available operations for Role.

1. [List roles](#list-roles)
2. [Create a role](#create-a-role)
3. [Update a role](#update-a-role)
4. [Delete a role](#delete-a-role)


## List roles

> List roles

```shell
GET /role?v=default&limit=1
```
> Success Response

```response

{
    "results": [
        {
            "uuid": "774b2af3-6437-4e5a-a310-547554c7c65c",
            "display": "Anonymous",
            "name": "Anonymous",
            "description": "Privileges for non-authenticated users.",
            "retired": false,
            "privileges": [],
            "inheritedRoles": [],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c?v=full"
                }
            ],
            "resourceVersion": "1.8"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default&startIndex=1"
        }
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Fetch all the roles that match any specified parameters otherwise fetch all roles. Returns a `200 OK` status with the role response. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Get a role by UUID.

> Get a role by UUID

```shell
GET /role/:target_role_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*Retrieve a role by its UUID. Returns a `404 Not Found` status if the role does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a role

> Create a role

```shell
POST /role
{
    "name": "Clinician",
    "description": "A provider assisting the Lead Surgeon.",
    "privileges": [
        {
            "name": "Delete Patients",
            "description": "Able to delete patients"
        }
    ],
    "inheritedRoles": [
        "774b2af3-6437-4e5a-a310-547554c7c65c"
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Clinician\",\r\n    \"description\": \"A provider assisting the Lead Surgeon.\",\r\n    \"privileges\": [\r\n        {\r\n            \"name\": \"Delete Patients\",\r\n            \"description\": \"Able to delete patients\"\r\n        }\r\n    ],\r\n    \"inheritedRoles\": [\r\n        \"774b2af3-6437-4e5a-a310-547554c7c65c\"\r\n    ]\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/role")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA");

var raw = JSON.stringify({"name":"Clinician","description":"A provider assisting the Lead Surgeon.","privileges":[{"name":"Delete Patients","description":"Able to delete patients"}],"inheritedRoles":["774b2af3-6437-4e5a-a310-547554c7c65c"]});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/role", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a role, you need to specify below attributes in the request body. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *[privileges](#privilege)* | `Array[] : privileges` | An array of the privilege resource
    *[inheritedRoles](#role)* | `Array[] : inheritedRoles` | An array of the inheritedRoles type or UUIDs

## Update a role

```shell
POST /role/:target_role_uuid
{
  "description": "Manages forms and attaches them to the UI"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"description\": \"Manages forms and attaches them to the UI\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/role/86f043da-1019-4caf-8db6-d5a472334f58")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA");

var raw = JSON.stringify({"description":"Manages forms and attaches them to the UI"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/role/86f043da-1019-4caf-8db6-d5a472334f58", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))


```

*  Update a role with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if the role does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *[privileges](#privilege)* | `Array[] : privileges` | An array of the privilege resource
    *[inheritedRoles](#role)* | `Array[] : inheritedRoles` | An array of the inheritedRoles type or UUIDs


## Delete a role

> Delete a role

```shell
DELETE /role/:target_role_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/role/86f043da-1019-4caf-8db6-d5a472334f58?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/role/86f043da-1019-4caf-8db6-d5a472334f58?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete a role by its UUID. Returns a `404 Not Found` status if the role does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | must be `true` to delete the role from the system; if `false`, the request will have no effect

