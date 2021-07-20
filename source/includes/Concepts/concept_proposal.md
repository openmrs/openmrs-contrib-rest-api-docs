# Concept Proposal

## Concept Proposal Overview

## Available operations.

1. [List Concept Proposals](#list-concept-proposals)
2. [Create a Concept Proposal](#create-a-concept-proposal)
3. [Update a Concept Proposal](#update-a-concept-proposal)
4. [Delete a Concept Proposal](#delete-a-concept-proposal)
5. [Ignore a Concept Proposal](#ignore-a-concept-proposal)
5. [Convert a Concept Proposal](#convert-a-concept-proposal)


## List Concept Proposals

> List Concept Proposals

```shell
GET /conceptproposal
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=C40164E7FA407F9E872B0BBDBB4582B0")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=C40164E7FA407F9E872B0BBDBB4582B0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "d9adb319-f634-4764-b8ac-7c55a302b656",
            "encounter": null,
            "originalText": "test",
            "state": "UNMAPPED",
            "creator": {
                "uuid": "1c3db49d-440a-11e6-a65c-00e04c680037",
                "display": "admin",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/user/1c3db49d-440a-11e6-a65c-00e04c680037",
                        "resourceAlias": "user"
                    }
                ]
            },
            "dateCreated": "2021-07-20T21:16:33.000+0200",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptproposal/d9adb319-f634-4764-b8ac-7c55a302b656",
                    "resourceAlias": "conceptproposal"
                }
            ]
        }
    ]
}
```

Retrieve all Concept Proposals. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
You can also pass query parameters to add sorting or filtering to your query.

### Query Parameters

  Parameter | Type | Description
      --- | --- | ---
  *includeCompleted* | `Boolean` | If true, will also include mapped proposals
  *sortOn* | `String` | If set to "originalText" then will sort proposals alphabetically by original text
  *sortOrder* | `String` | Order of sorting, "asc" or "desc".


## List Concept Proposal by UUID.

> List Concept Proposal by UUID

```shell
GET /conceptproposal/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal/:uuid")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=CDA2E6D4A724D5E5DC294136C185284C")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=CDA2E6D4A724D5E5DC294136C185284C");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieve a concept proposal by its UUID. Returns a `404 Not Found` status if proposal does not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a Concept Proposal

> Create a Concept Proposal

```shell
POST /conceptproposal
{
    "originalText": "text",
    "mappedConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c",
    "encounter": "b93eafe5-a6d0-45c8-8429-f3c38dc382e7",
    "obsConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"originalText\": \"text\",\"mappedConcept\": \"a95e0f2a-915e-42bb-ae9a-92248ff85e8c\",\"encounter\": \"b93eafe5-a6d0-45c8-8429-f3c38dc382e7\",\"obsConcept\": \"a95e0f2a-915e-42bb-ae9a-92248ff85e8c\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=77AE436C4972FB63FC69B7836445489F")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=77AE436C4972FB63FC69B7836445489F");

var raw = JSON.stringify({"originalText": "text","mappedConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c","encounter": "b93eafe5-a6d0-45c8-8429-f3c38dc382e7","obsConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a Concept Proposal, you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *originalText* | `String` | Name of the concept proposal (Required)
    *mappedConcept* | `Concept_UUID` | UUID of Concept that you want to map this proposal to
    *encounter* | `Encounter_UUID` | UUID of Encounter that will be used for creating Observation
    *obsConcept* | `Concept_UUID` | UUID of Concept that will be used for creating Observation

## Update a Concept Proposal

> Update a Concept Proposal

```shell
POST /conceptproposal/:uuid
{
    "finalText": "text",
    "comments": "comments",
    "mappedConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c",
    "encounter": "b93eafe5-a6d0-45c8-8429-f3c38dc382e7",
    "obsConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"finalText\": \"text\",\"comments\": \"comments\",\"mappedConcept\": \"a95e0f2a-915e-42bb-ae9a-92248ff85e8c\",\"encounter\": \"b93eafe5-a6d0-45c8-8429-f3c38dc382e7\",\"obsConcept\": \"a95e0f2a-915e-42bb-ae9a-92248ff85e8c\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=77AE436C4972FB63FC69B7836445489F")
  .build();
Response response = client.newCall(request).execute();

```


```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"finalText": "text","comments": "comments","mappedConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c","encounter": "b93eafe5-a6d0-45c8-8429-f3c38dc382e7","obsConcept": "a95e0f2a-915e-42bb-ae9a-92248ff85e8c"});

var requestOptions = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal/:uuid", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
```

Update a Concept Proposal with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if proposal does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *finalText* | `String` | Final name of the concept proposal (Required)
    *comments* | `String` | Comments of the concept proposal. Will be shared with other proposal creators.
    *mappedConcept* | `Concept_UUID` | UUID of Concept that you want to map this proposal to
    *encounter* | `Encounter_UUID` | UUID of Encounter that will be used for creating Observation
    *obsConcept* | `Concept_UUID` | UUID of Concept that will be used for creating Observation


## Delete a Concept Proposal

> Delete a Concept Proposal

```shell
DELETE /conceptproposal/:uuid?purge=true
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal/:uuid?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=CDA2E6D4A724D5E5DC294136C185284C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=CDA2E6D4A724D5E5DC294136C185284C");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete (purge) a concept proposal by its UUID. Returns a `404 Not Found` status if proposal does not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.


## Ignore a Concept Proposal

> Ignore a Concept Proposal

```shell
POST /conceptproposal/:uuid
{
    "action": "ignore"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"action\": \"ignore\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=77AE436C4972FB63FC69B7836445489F")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"action": "ignore"});

var requestOptions = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal/:uuid", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
```

Ignore a Concept Proposal with given UUID. This method will also ignore any other proposals with the same original name. Returns a `404 Not Found` status if proposal does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

## Convert a Concept Proposal

> Convert a Concept Proposal

```shell
POST /conceptproposal/:uuid
{
  "action": "convert",
  "actionToTakeOnConvert": "saveAsMapped",
  "conceptNameLocale": "en"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"action\": \"convert\",\"actionToTakeOnConvert\": \"saveAsMapped\",\"conceptNameLocale\": \"en\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptproposal/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=77AE436C4972FB63FC69B7836445489F")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"action": "convert","actionToTakeOnConvert": "saveAsMapped","conceptNameLocale": "en"});

var requestOptions = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptproposal/:uuid", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
```

Map a Concept Proposal with given UUID. This method will also map any other proposals with the same original name. Returns a `404 Not Found` status if proposal does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *action* | `String` | Has to be set to "convert" (Required)
    *actionToTakeOnConvert* | `String` | If set to "saveAsSynonym", proposal will be mapped to concept's synonym. If set to "saveAsMapped" then will map proposal to observation based on encounter and obsConcept. (Required)
    *conceptNameLocale* | `String` | Language code of proposal's text (future concept name)
