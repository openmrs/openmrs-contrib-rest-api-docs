# Concept State Conversion

## Available Operations for Concept State Conversion type

1. [List Concept State Conversions](#list-concept-state-conversions)
2. [Create a Concept State Conversion](#create-concept-state-conversion)
3. [Update a Concept State Conversion](#update-concept-state-conversion)
4. [Delete a Concept State Conversion](#delete-concept-state-conversion)

## List Concept State Conversions

> List Concept State Conversions

```shell
GET /stateconversion
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/stateconversion")
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
fetch("/openmrs/ws/rest/v1/stateconversion", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "ddf056be-40dd-44db-a95b-85bddd931131",
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
            "programWorkflow": {
                "uuid": "54524222-f41d-4d0d-b688-0fd5331377b4",
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
                        "uuid": "8d250876-baac-4592-8f87-d7d7bf00dcdb",
                        "retired": false,
                        "concept": {
                            "uuid": "7737c9ef-80ad-44e6-920f-4106da899df4",
                            "display": "malaria dead",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/7737c9ef-80ad-44e6-920f-4106da899df4",
                                    "resourceAlias": "concept"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/54524222-f41d-4d0d-b688-0fd5331377b4/state/8d250876-baac-4592-8f87-d7d7bf00dcdb",
                                "resourceAlias": "state"
                            }
                        ]
                    },
                    {
                        "uuid": "65b552f7-a768-4986-b00c-28f765625450",
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
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/54524222-f41d-4d0d-b688-0fd5331377b4/state/65b552f7-a768-4986-b00c-28f765625450",
                                "resourceAlias": "state"
                            }
                        ]
                    }
                ],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/54524222-f41d-4d0d-b688-0fd5331377b4",
                        "resourceAlias": "workflow"
                    }
                ]
            },
            "programWorkflowState": {
                "uuid": "65b552f7-a768-4986-b00c-28f765625450",
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
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/54524222-f41d-4d0d-b688-0fd5331377b4/state/65b552f7-a768-4986-b00c-28f765625450",
                        "resourceAlias": "state"
                    }
                ]
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/stateconversion/ddf056be-40dd-44db-a95b-85bddd931131",
                    "resourceAlias": "stateconversion"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/stateconversion/ddf056be-40dd-44db-a95b-85bddd931131?v=full",
                    "resourceAlias": "stateconversion"
                }
            ]
        }
    ]
}
```

Fetch all Concept State Conversions. Returns a `200 OK` status with the Concept State Conversions response.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

## List Concept State Conversion by UUID.

> List Concept State Conversion by UUID

```shell
GET /stateconversion/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/stateconversion/:uuid")
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
fetch("/openmrs/ws/rest/v1/stateconversion/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieve a Concept State Conversion by its UUID. Returns a `404 Not Found` status if conversion does not exist.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

## Create a Concept State Conversion

> Create a Concept State Conversion

```shell
POST /stateconversion
{
    "concept": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
    "programWorkflow": "54524222-f41d-4d0d-b688-0fd5331377b4",
    "programWorkflowState": "65b552f7-a768-4986-b00c-28f765625450"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"concept\": \"116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\"programWorkflow\": \"54524222-f41d-4d0d-b688-0fd5331377b4\",\"programWorkflowState\": \"65b552f7-a768-4986-b00c-28f765625450\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/stateconversion")
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
var raw = JSON.stringify({"concept": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","programWorkflow": "54524222-f41d-4d0d-b688-0fd5331377b4","programWorkflowState": "65b552f7-a768-4986-b00c-28f765625450"});
var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/stateconversion", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a Concept State Conversion you need to specify the below properties in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *[concept](#concepts)* | `Concept_UUID` | Concept resource UUID
    *[programWorkflow](#program-workflows)* | `ProgramWorkflow_UUID` | ProgramWorkflow resource UUID
    *[programWorkflowState](#program-workflows)* | `ProgramWorkflowState_UUID` | ProgramWorkflowState resource UUID


## Update a Concept State Conversion

> Update a Concept State Conversion

```shell
POST /stateconversion/:uuid
{
    "concept": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
    "programWorkflow": "54524222-f41d-4d0d-b688-0fd5331377b4",
    "programWorkflowState": "65b552f7-a768-4986-b00c-28f765625450"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"concept\": \"116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\"programWorkflow\": \"54524222-f41d-4d0d-b688-0fd5331377b4\",\"programWorkflowState\": \"65b552f7-a768-4986-b00c-28f765625450\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/stateconversion/:uuid")
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
var raw = JSON.stringify({"concept": "116128AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","programWorkflow": "54524222-f41d-4d0d-b688-0fd5331377b4","programWorkflowState": "65b552f7-a768-4986-b00c-28f765625450"});
var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/stateconversion/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Update a Concept State Conversion. This method only modifies properties specified in the request. Returns a `404 Not Found` status if conversion does not exist. If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *[concept](#concepts)* | `Concept_UUID` | Concept resource UUID
    *[programWorkflow](#program-workflows)* | `ProgramWorkflow_UUID` | ProgramWorkflow resource UUID
    *[programWorkflowState](#program-workflows)* | `ProgramWorkflowState_UUID` | ProgramWorkflowState resource UUID


## Delete a Concept State Conversion

> Delete a Concept State Conversion

```shell
DELETE /stateconversion/:uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/stateconversion/:uuid?purge=true")
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
fetch("/openmrs/ws/rest/v1/stateconversion/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Purge a Concept State Conversion by its UUID. Returns a `404 Not Found` status if conversion does not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
