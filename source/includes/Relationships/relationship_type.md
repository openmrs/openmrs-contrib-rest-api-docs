# Relationship Type

## Relationship Type Overview

Relationship Types define the types of relationships between Persons. Also, manage how relationship types are shown to the user (which types are shown by default and in which order).

Relationships have two directions. Some relationships differ depending on the direction; for example, if A is related to B as "Parent", then B is, by definition, related to A as "Child". Other relationships are the same in either direction (e.g., the reverse relationship of "Sibling" is also "Sibling").

## Available operations for Relationship Type

1. [List relationship types](#list-relationship-types)
2. [Create a relationship type](#create-a-relationship-type)
3. [Update a relationship type](#update-a-relationship-type)
4. [Delete a relationship type](#delete-a-relationship-type)

## List Relationship Types

> Get all non-retired Relationship Types

```shell
GET /relationshiptype
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/relationshiptype
&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/relationshiptype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "8d919b58-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Doctor/Patient",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/relationshiptype/8d919b58-c2cc-11de-8d13-0010c6dffd0f",
                    "resourceAlias": "relationshiptype"
                }
            ]
        },
        {
            "uuid": "8d91a01c-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Sibling/Sibling",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/relationshiptype/8d91a01c-c2cc-11de-8d13-0010c6dffd0f",
                    "resourceAlias": "relationshiptype"
                }
            ]
        },
        {
            "uuid": "8d91a210-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Parent/Child",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/relationshiptype/8d91a210-c2cc-11de-8d13-0010c6dffd0f",
                    "resourceAlias": "relationshiptype"
                }
            ]
        },
        {
            "uuid": "8d91a3dc-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Aunt/Uncle/Niece/Nephew",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/relationshiptype/8d91a3dc-c2cc-11de-8d13-0010c6dffd0f",
                    "resourceAlias": "relationshiptype"
                }
            ]
        },
        {
            "uuid": "2a5f4ff4-a179-4b8a-aa4c-40f71956ebbc",
            "display": "Supervisor/Supervisee",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/relationshiptype/2a5f4ff4-a179-4b8a-aa4c-40f71956ebbc",
                    "resourceAlias": "relationshiptype"
                }
            ]
        }
    ]
}
```

You can filter Relationship Types display with given query parameters.
If not logged in to perform this action, a `401 Unauthorized` status is returned.


### Query Parameters

| Parameter | Type           | Description                           |
| --------- | -------------- | ------------------------------------- |
| _q_       | `Search Query` | Filter relationship types by name     |


## Get Relationship Type by UUID

> Get Relationship Type by UUID

```shell
GET /relationshiptype/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/relationshiptype/:uuid")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/relationshiptype/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieve a Relationship Type by its UUID. Returns a `404 Not Found` status if the user does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

## Create a Relationship Type

> Create a Relationship Type

```shell
{
    "description": "Relationship from a primary care provider to the patient",
    "aIsToB": "Doctor",
    "bIsToA": "Patient",
    "weight": 0
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"description\": \"Relationship from a primary care provider to the patient\",\"aIsToB\": \"Doctor\",\"bIsToA\": \"Patient\",\"weight\": 0}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/relationshiptype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"description": "Relationship from a primary care provider to the patient","aIsToB": "Doctor","bIsToA": "Patient","weight": 0});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/relationshiptype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*aIsToB* | `String` | How is A related to B
*bIsToA* | `String` | How is B related to A
*description* | `String` | Relationship description
*weight* | `integer` | Relationship weight

## Update a Relationship Type

> Update a Relationship Type using its UUID

```shell
POST /relationshiptype/:uuid
{
    "description": "Relationship between brother/sister, brother/brother, and sister/sister"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"description\": \"Relationship between brother/sister, brother/brother, and sister/sister\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/relationshiptype/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"description":"Relationship between brother/sister, brother/brother, and sister/sister"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/relationshiptype/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Update a target Relationship Type with given UUID. Returns a `404 Not Found` status if the Relationship Type does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*aIsToB* | `String` | How is A related to B
*bIsToA* | `String` | How is B related to A
*description* | `String` | Relationship description
*weight* | `integer` | Relationship weight

## Delete a Relationship Type

> Delete a Relationship Type using its UUID

```shell
DELETE /relationshiptype/:uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/relationshiptype/:uuid?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/relationshiptype/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Delete or retire a Relationship Type by its UUID. Returns a `404 Not Found` status if the Relationship Type does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

| Parameter | Type      | Description                                       |
| --------- | --------- | ------------------------------------------------- |
| _purge_   | `Boolean` | The resource will be voided unless purge = ‘true’ |
