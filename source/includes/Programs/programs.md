# Program

## Program Overview

A program is typically used when a patient is identified as belonging to a group for which a particular set of coordinated interventions is to be followed. For example, programs might be used for diseases such as HIV or tuberculosis or conditions such as pregnancy or interventions such as childhood immunization.

## Available Operations for Program type

1. [List Programs](#list-programs)
2. [Create a Program](#create-a-program)
3. [Update a Program](#update-a-program)
4. [Delete a Program](#delete-a-program)

## List Programs

> List Programs

```shell
GET /program
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/program")
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

fetch("/openmrs/ws/rest/v1/program", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2",
            "name": "malaria",
            "allWorkflows": [
                {
                    "uuid": "65fd8425-1090-4a24-8db6-c89aa80daa5d",
                    "concept": {
                        "uuid": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                        "display": "Malaria",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                                "resourceAlias": "concept"
                            }
                        ]
                    },
                    "retired": false,
                    "states": [
                        {
                            "uuid": "f0f0c506-a969-4a3b-84dc-d5d7057b9fcd",
                            "retired": false,
                            "concept": {
                                "uuid": "11034efc-1b2b-4cda-a414-74786a76b800",
                                "display": "dead",
                                "links": [
                                    {
                                        "rel": "self",
                                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800",
                                        "resourceAlias": "concept"
                                    }
                                ]
                            },
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/f0f0c506-a969-4a3b-84dc-d5d7057b9fcd",
                                    "resourceAlias": "state"
                                }
                            ]
                        },
                        {
                            "uuid": "ce13f1c0-742a-415b-91ad-a0b1bd888bc8",
                            "retired": false,
                            "concept": {
                                "uuid": "51d62167-7642-489b-ad0a-79b3b8654882",
                                "display": "cured",
                                "links": [
                                    {
                                        "rel": "self",
                                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882",
                                        "resourceAlias": "concept"
                                    }
                                ]
                            },
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/ce13f1c0-742a-415b-91ad-a0b1bd888bc8",
                                    "resourceAlias": "state"
                                }
                            ]
                        },
                        {
                            "uuid": "535c60a7-d349-4a36-97d0-898e938cdd6f",
                            "retired": false,
                            "concept": {
                                "uuid": "160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                                "display": "Malaria, confirmed",
                                "links": [
                                    {
                                        "rel": "self",
                                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                                        "resourceAlias": "concept"
                                    }
                                ]
                            },
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/535c60a7-d349-4a36-97d0-898e938cdd6f",
                                    "resourceAlias": "state"
                                }
                            ]
                        }
                    ],
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d",
                            "resourceAlias": "workflow"
                        }
                    ]
                }
            ],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/program/959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2",
                    "resourceAlias": "program"
                }
            ]
        }
    ]
}
```

Fetch all Programs that match the search query parameter, otherwise fetch all Programs. Returns a `200 OK` status with the Programs response.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of program.

## List Program by UUID.

> List Program by UUID

```shell
GET /program/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/program/:uuid")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/program/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieve a Program by its UUID. Returns a `404 Not Found` status if program does not exist.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

## Create a Program

> Create a Program

```shell
POST /program
{
    "name": "program",
    "description": "program",
    "concept": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
    "retired": false,
    "outcomesConcept": "5c938680-c300-4fc0-9a72-e798220f287b"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"name\": \"program\",\n    \"description\": \"program\",\n    \"concept\": \"116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\n    \"retired\": false,\n    \"outcomesConcept\": \"5c938680-c300-4fc0-9a72-e798220f287b\"\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/program")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var raw = JSON.stringify({"name": "program","description": "program","concept":"116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","retired": false,"outcomesConcept": "5c938680-c300-4fc0-9a72-e798220f287b"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/program", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a program you need to specify the below properties in the request body.  If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the program
    *description* | `String` | Description of the program
    *retired* | `Boolean` | Is program retired
    *[concept](#concepts)* | `Concept_UUID` | Concept resource UUID (Required)
    *[outcomesConcept](#concepts)* | `Concept_UUID` | Concept resource UUID containing program outcomes


## Update a Program

> Update a Program

```shell
POST /program/:uuid
{
    "name": "program",
    "description": "program",
    "concept": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
    "retired": false,
    "outcomesConcept": "5c938680-c300-4fc0-9a72-e798220f287b"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"name\": \"program\",\n    \"description\": \"program\",\n    \"concept\": \"116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\n    \"retired\": false,\n    \"outcomesConcept\": \"5c938680-c300-4fc0-9a72-e798220f287b\"\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/program/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var raw = JSON.stringify({"name": "program","description": "program","concept":"116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","retired": false,"outcomesConcept": "5c938680-c300-4fc0-9a72-e798220f287b"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/program/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

Update a Program. This method only modifies properties specified in the request. Returns a `404 Not found`. If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the program
    *description* | `String` | Description of the program
    *retired* | `Boolean` | Is program retired
    *[concept](#concepts)* | `Concept_UUID` | Concept resource UUID (Required)
    *[outcomesConcept](#concepts)* | `Concept_UUID` | Concept resource UUID containing program outcomes



## Delete a Program

> Delete a Program

```shell
DELETE /program/:uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/program/:uuid?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/program/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Delete or retire a Program by its UUID. Returns a `404 Not Found` status if patient not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `String` | Program's uuid to delete
    *purge* | `Boolean` | The program will be retired unless purge = 'true'
