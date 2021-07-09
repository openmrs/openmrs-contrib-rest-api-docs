# Database Changes

## Database Changes Overview

Database Change is a Liquibase change set represented by `OpenMRSChangeSet` class.

## Available Operations for Database Changes type

1. [List Database Changes](#list-database-changes)

## List Database Changes

> List Database Changes

```shell
GET /databasechange?v=default
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/databasechange?v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
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

fetch("/openmrs/ws/rest/v1/databasechange?v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
  "results": [
    {
      "uuid": "1227303685425-1",
      "display": "ben (generated) createTable tableName=cohort",
      "author": "ben (generated)",
      "description": "createTable tableName=cohort",
      "runStatus": "INVALID_MD5SUM",
      "links": [
        {
          "rel": "self",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange/1227303685425-1",
          "resourceAlias": "databasechange"
        },
        {
          "rel": "full",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange/1227303685425-1?v=full",
          "resourceAlias": "databasechange"
        }
      ],
      "resourceVersion": "1.8"
    },
    {
      "uuid": "1227303685425-2",
      "display": "ben (generated) createTable tableName=cohort_member",
      "author": "ben (generated)",
      "description": "createTable tableName=cohort_member",
      "runStatus": "ALREADY_RAN",
      "links": [
        {
          "rel": "self",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange/1227303685425-2",
          "resourceAlias": "databasechange"
        },
        {
          "rel": "full",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange/1227303685425-2?v=full",
          "resourceAlias": "databasechange"
        }
      ],
      "resourceVersion": "1.8"
    }
  ],
  "links": [
    {
      "rel": "next",
      "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange?v=default&startIndex=50",
      "resourceAlias": null
    }
  ]
}
```

Fetches all liquibase change sets. Returns a `200 OK` status with the List of DatabaseChange response.

## Get Database Change by its Id

> Get Database Change by its Id

```shell
GET /databasechange/:id
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/databasechange/:id")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
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

fetch("/openmrs/ws/rest/v1/databasechange/:id", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "uuid": "1227303685425-34",
    "display": "ben (generated) createTable tableName=hl7_in_error",
    "author": "ben (generated)",
    "description": "createTable tableName=hl7_in_error",
    "runStatus": "INVALID_MD5SUM",
    "links": [
        {
            "rel": "self",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange/1227303685425-34",
            "resourceAlias": "databasechange"
        },
        {
            "rel": "full",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/databasechange/1227303685425-34?v=full",
            "resourceAlias": "databasechange"
        }
    ],
    "resourceVersion": "1.8"
}
```

Fetches Liquibase change set by its id. Returns a `404 Not Found` status if the change set does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.
