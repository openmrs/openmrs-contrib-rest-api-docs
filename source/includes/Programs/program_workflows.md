# Program Workflow

## Program Workflow Overview

A program may be composed of one or more workflows. If there are no workflows, only the patient_program data (entry date, exit date, outcome) is maintained. Many programs have only one workflow, but some have more than one. For example, in the pregnancy program, there might be an "all patients" workflow, a "high risk" workflow, and a "delivery" workflow; a woman with a high risk pregnancy would get both the "all patients" protocol and the "high risk" protocol.


## Subresource types

### Program Workflow States

A workflow is composed of states, at most one of which will be assigned to a particular patient at a particular time; for example, an HIV program might have "registered", "ready for ARV", "on initial ARV regimen", "on other 1st line regimen", "on 2nd line regimen", "defaulted", "lost to follow-up", "died", etc. Some states are "initial" states, to which patient may be assigned upon entry into the program; other states are "terminal" states – when a patient is assigned to this state, the patient's participation in the program comes to an end.

## Available Operations for Program Workflow type

1. [List Program Workflow by UUID](#list-program-workflow-by-uuid)
2. [Create a Program Workflow](#create-a-program-workflow)
3. [Update a Program Workflow](#update-a-program-workflow)
4. [Delete a Program Workflow](#delete-a-program-workflow)
5. [List Program Workflow States](#list-program-workflow-states)
6. [Create Program Workflow State](#create-program-workflow-state)
7. [Update Program Workflow State](#update-program-workflow-state)
8. [Delete Program Workflow State](#delete-program-workflow-state)

## List Program Workflow by UUID

> List Program Workflow by UUID

```shell
GET /workflow/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid")
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

fetch("/openmrs/ws/rest/v1/workflow/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
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
    "description": null,
    "retired": false,
    "states": [
        {
            "uuid": "f0f0c506-a969-4a3b-84dc-d5d7057b9fcd",
            "description": null,
            "retired": false,
            "concept": {
                "uuid": "11034efc-1b2b-4cda-a414-74786a76b800",
                "display": "dead",
                "name": {
                    "display": "dead",
                    "uuid": "af75b2bd-5b7e-4e85-a70d-69da546047ed",
                    "name": "dead",
                    "locale": "en",
                    "localePreferred": true,
                    "conceptNameType": "FULLY_SPECIFIED",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800/name/af75b2bd-5b7e-4e85-a70d-69da546047ed",
                            "resourceAlias": "name"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800/name/af75b2bd-5b7e-4e85-a70d-69da546047ed?v=full",
                            "resourceAlias": "name"
                        }
                    ],
                    "resourceVersion": "1.9"
                },
                "datatype": {
                    "uuid": "8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Coded",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptdatatype/8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptdatatype"
                        }
                    ]
                },
                "conceptClass": {
                    "uuid": "8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Test",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptclass"
                        }
                    ]
                },
                "set": false,
                "version": null,
                "retired": false,
                "names": [
                    {
                        "uuid": "af75b2bd-5b7e-4e85-a70d-69da546047ed",
                        "display": "dead",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800/name/af75b2bd-5b7e-4e85-a70d-69da546047ed",
                                "resourceAlias": "name"
                            }
                        ]
                    }
                ],
                "descriptions": [],
                "mappings": [],
                "answers": [],
                "setMembers": [],
                "attributes": [],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800",
                        "resourceAlias": "concept"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800?v=full",
                        "resourceAlias": "concept"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/f0f0c506-a969-4a3b-84dc-d5d7057b9fcd",
                    "resourceAlias": "state"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/f0f0c506-a969-4a3b-84dc-d5d7057b9fcd?v=full",
                    "resourceAlias": "state"
                }
            ],
            "resourceVersion": "1.8"
        },
        {
            "uuid": "ce13f1c0-742a-415b-91ad-a0b1bd888bc8",
            "description": null,
            "retired": false,
            "concept": {
                "uuid": "51d62167-7642-489b-ad0a-79b3b8654882",
                "display": "cured",
                "name": {
                    "display": "cured",
                    "uuid": "dca5be41-93fa-48fb-a507-faabfd012891",
                    "name": "cured",
                    "locale": "en",
                    "localePreferred": true,
                    "conceptNameType": "FULLY_SPECIFIED",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882/name/dca5be41-93fa-48fb-a507-faabfd012891",
                            "resourceAlias": "name"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882/name/dca5be41-93fa-48fb-a507-faabfd012891?v=full",
                            "resourceAlias": "name"
                        }
                    ],
                    "resourceVersion": "1.9"
                },
                "datatype": {
                    "uuid": "8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Coded",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptdatatype/8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptdatatype"
                        }
                    ]
                },
                "conceptClass": {
                    "uuid": "8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Test",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptclass"
                        }
                    ]
                },
                "set": false,
                "version": null,
                "retired": false,
                "names": [
                    {
                        "uuid": "dca5be41-93fa-48fb-a507-faabfd012891",
                        "display": "cured",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882/name/dca5be41-93fa-48fb-a507-faabfd012891",
                                "resourceAlias": "name"
                            }
                        ]
                    }
                ],
                "descriptions": [],
                "mappings": [],
                "answers": [],
                "setMembers": [],
                "attributes": [],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882",
                        "resourceAlias": "concept"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882?v=full",
                        "resourceAlias": "concept"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/ce13f1c0-742a-415b-91ad-a0b1bd888bc8",
                    "resourceAlias": "state"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/ce13f1c0-742a-415b-91ad-a0b1bd888bc8?v=full",
                    "resourceAlias": "state"
                }
            ],
            "resourceVersion": "1.8"
        },
        {
            "uuid": "535c60a7-d349-4a36-97d0-898e938cdd6f",
            "description": null,
            "retired": false,
            "concept": {
                "uuid": "160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                "display": "Malaria, confirmed",
                "name": {
                    "display": "Malaria, confirmed",
                    "uuid": "107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                    "name": "Malaria, confirmed",
                    "locale": "en",
                    "localePreferred": true,
                    "conceptNameType": "FULLY_SPECIFIED",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                            "resourceAlias": "name"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB?v=full",
                            "resourceAlias": "name"
                        }
                    ],
                    "resourceVersion": "1.9"
                },
                "datatype": {
                    "uuid": "8d4a4c94-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "N/A",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptdatatype/8d4a4c94-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptdatatype"
                        }
                    ]
                },
                "conceptClass": {
                    "uuid": "8d4918b0-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Diagnosis",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptclass/8d4918b0-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptclass"
                        }
                    ]
                },
                "set": false,
                "version": "",
                "retired": false,
                "names": [
                    {
                        "uuid": "126352BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "Malaria confirmées",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/126352BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "name"
                            }
                        ]
                    },
                    {
                        "uuid": "107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "Malaria, confirmed",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "name"
                            }
                        ]
                    }
                ],
                "descriptions": [],
                "mappings": [
                    {
                        "uuid": "242519ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "IMO ProblemIT: 1527785",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/242519ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "285752ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "ICPC2: A73",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/285752ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "217284ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "CIEL: 160148",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/217284ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "143841ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "PIH: 7127",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/143841ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "170552ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "SNOMED NP: 61462000",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/170552ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "143842ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "ICD-10-WHO: B53.8",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/143842ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "170553ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "SNOMED NP: 2931005",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/170553ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    }
                ],
                "answers": [],
                "setMembers": [],
                "attributes": [],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                        "resourceAlias": "concept"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA?v=full",
                        "resourceAlias": "concept"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/535c60a7-d349-4a36-97d0-898e938cdd6f",
                    "resourceAlias": "state"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/535c60a7-d349-4a36-97d0-898e938cdd6f?v=full",
                    "resourceAlias": "state"
                }
            ],
            "resourceVersion": "1.8"
        }
    ],
    "links": [
        {
            "rel": "self",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d",
            "resourceAlias": "workflow"
        },
        {
            "rel": "full",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d?v=full",
            "resourceAlias": "workflow"
        }
    ],
    "resourceVersion": "1.8"
}
```

Fetch Program Workflow by UUID. Return a `404 Not Found` status if given workflow doesn't exist.
If user is not logged in to perform this action, a `401 Unauthorized` status is returned.

## Create a Program Workflow

> Create a Program Workflow

```shell
POST /workflow
{
    "program": "959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2",
    "concept": "112992AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"program\": \"959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2\",\"concept\": \"112992AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow")
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

var raw = JSON.stringify({"program": "959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2","concept": "112992AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a workflow you need to specify the below properties in the request body. `401 Unauthorized` is returned if the request is not authenticated or if the authenticated user does not have appropriate permissions.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[program](#programs)* | `Program_UUID` | UUID of the parent program
    *[concept](#concept)* | `Concept_UUID` | UUID of Concept related to the workflow


## Update a Program Workflow

> Update a Program Workflow

```shell
POST /workflow/:uuid
{
    "program": "959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2",
    "concept": "112992AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"program\": \"959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2\",\"concept\": \"112992AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid")
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

var raw = JSON.stringify({"program": "959dc77c-7c2a-4f0d-9c4e-3a8f48c488e2","concept": "112992AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"});

var requestOptions = {
    method: 'POST',
    headers: requestHeaders,
    body: raw,
    redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
```

To update a workflow you need to specify the below properties in the request body. `401 Unauthorized` is returned if the request is not authenticated or if the authenticated user does not have appropriate permissions.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[program](#programs)* | `Program_UUID` | UUID of the parent program
    *[concept](#concept)* | `Concept_UUID` | UUID of Concept related to the workflow

## Delete a Program Workflow

> Delete a Program Workflow

```shell
DELETE /workflow/:uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retire given Workflow. Returns a `404 Not Found` status if workflow does not exist. If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

## List Program Workflow States

> List Program Workflow States

```shell
GET /workflow/:uuid/state
```


```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid/state")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();
```


```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid/state", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "ce13f1c0-742a-415b-91ad-a0b1bd888bc8",
            "description": null,
            "retired": false,
            "concept": {
                "uuid": "51d62167-7642-489b-ad0a-79b3b8654882",
                "display": "cured",
                "name": {
                    "display": "cured",
                    "uuid": "dca5be41-93fa-48fb-a507-faabfd012891",
                    "name": "cured",
                    "locale": "en",
                    "localePreferred": true,
                    "conceptNameType": "FULLY_SPECIFIED",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882/name/dca5be41-93fa-48fb-a507-faabfd012891",
                            "resourceAlias": "name"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882/name/dca5be41-93fa-48fb-a507-faabfd012891?v=full",
                            "resourceAlias": "name"
                        }
                    ],
                    "resourceVersion": "1.9"
                },
                "datatype": {
                    "uuid": "8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Coded",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptdatatype/8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptdatatype"
                        }
                    ]
                },
                "conceptClass": {
                    "uuid": "8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Test",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptclass"
                        }
                    ]
                },
                "set": false,
                "version": null,
                "retired": false,
                "names": [
                    {
                        "uuid": "dca5be41-93fa-48fb-a507-faabfd012891",
                        "display": "cured",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882/name/dca5be41-93fa-48fb-a507-faabfd012891",
                                "resourceAlias": "name"
                            }
                        ]
                    }
                ],
                "descriptions": [],
                "mappings": [],
                "answers": [],
                "setMembers": [],
                "attributes": [],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882",
                        "resourceAlias": "concept"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/51d62167-7642-489b-ad0a-79b3b8654882?v=full",
                        "resourceAlias": "concept"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/ce13f1c0-742a-415b-91ad-a0b1bd888bc8",
                    "resourceAlias": "state"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/ce13f1c0-742a-415b-91ad-a0b1bd888bc8?v=full",
                    "resourceAlias": "state"
                }
            ],
            "resourceVersion": "1.8"
        },
        {
            "uuid": "f0f0c506-a969-4a3b-84dc-d5d7057b9fcd",
            "description": null,
            "retired": false,
            "concept": {
                "uuid": "11034efc-1b2b-4cda-a414-74786a76b800",
                "display": "dead",
                "name": {
                    "display": "dead",
                    "uuid": "af75b2bd-5b7e-4e85-a70d-69da546047ed",
                    "name": "dead",
                    "locale": "en",
                    "localePreferred": true,
                    "conceptNameType": "FULLY_SPECIFIED",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800/name/af75b2bd-5b7e-4e85-a70d-69da546047ed",
                            "resourceAlias": "name"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800/name/af75b2bd-5b7e-4e85-a70d-69da546047ed?v=full",
                            "resourceAlias": "name"
                        }
                    ],
                    "resourceVersion": "1.9"
                },
                "datatype": {
                    "uuid": "8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Coded",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptdatatype/8d4a48b6-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptdatatype"
                        }
                    ]
                },
                "conceptClass": {
                    "uuid": "8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Test",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptclass"
                        }
                    ]
                },
                "set": false,
                "version": null,
                "retired": false,
                "names": [
                    {
                        "uuid": "af75b2bd-5b7e-4e85-a70d-69da546047ed",
                        "display": "dead",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800/name/af75b2bd-5b7e-4e85-a70d-69da546047ed",
                                "resourceAlias": "name"
                            }
                        ]
                    }
                ],
                "descriptions": [],
                "mappings": [],
                "answers": [],
                "setMembers": [],
                "attributes": [],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800",
                        "resourceAlias": "concept"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/11034efc-1b2b-4cda-a414-74786a76b800?v=full",
                        "resourceAlias": "concept"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/f0f0c506-a969-4a3b-84dc-d5d7057b9fcd",
                    "resourceAlias": "state"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/f0f0c506-a969-4a3b-84dc-d5d7057b9fcd?v=full",
                    "resourceAlias": "state"
                }
            ],
            "resourceVersion": "1.8"
        },
        {
            "uuid": "535c60a7-d349-4a36-97d0-898e938cdd6f",
            "description": null,
            "retired": false,
            "concept": {
                "uuid": "160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                "display": "Malaria, confirmed",
                "name": {
                    "display": "Malaria, confirmed",
                    "uuid": "107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                    "name": "Malaria, confirmed",
                    "locale": "en",
                    "localePreferred": true,
                    "conceptNameType": "FULLY_SPECIFIED",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                            "resourceAlias": "name"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB?v=full",
                            "resourceAlias": "name"
                        }
                    ],
                    "resourceVersion": "1.9"
                },
                "datatype": {
                    "uuid": "8d4a4c94-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "N/A",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptdatatype/8d4a4c94-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptdatatype"
                        }
                    ]
                },
                "conceptClass": {
                    "uuid": "8d4918b0-c2cc-11de-8d13-0010c6dffd0f",
                    "display": "Diagnosis",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptclass/8d4918b0-c2cc-11de-8d13-0010c6dffd0f",
                            "resourceAlias": "conceptclass"
                        }
                    ]
                },
                "set": false,
                "version": "",
                "retired": false,
                "names": [
                    {
                        "uuid": "126352BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "Malaria confirmées",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/126352BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "name"
                            }
                        ]
                    },
                    {
                        "uuid": "107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "Malaria, confirmed",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/name/107966BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "name"
                            }
                        ]
                    }
                ],
                "descriptions": [],
                "mappings": [
                    {
                        "uuid": "242519ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "IMO ProblemIT: 1527785",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/242519ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "285752ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "ICPC2: A73",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/285752ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "217284ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "CIEL: 160148",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/217284ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "143841ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "PIH: 7127",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/143841ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "170552ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "SNOMED NP: 61462000",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/170552ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "143842ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "ICD-10-WHO: B53.8",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/143842ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    },
                    {
                        "uuid": "170553ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                        "display": "SNOMED NP: 2931005",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/170553ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
                                "resourceAlias": "mapping"
                            }
                        ]
                    }
                ],
                "answers": [],
                "setMembers": [],
                "attributes": [],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                        "resourceAlias": "concept"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/160148AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA?v=full",
                        "resourceAlias": "concept"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/535c60a7-d349-4a36-97d0-898e938cdd6f",
                    "resourceAlias": "state"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/workflow/65fd8425-1090-4a24-8db6-c89aa80daa5d/state/535c60a7-d349-4a36-97d0-898e938cdd6f?v=full",
                    "resourceAlias": "state"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}
```

List all workflow states for given Program Workflow object. Returns `404 Not Found` status if the workflow does not exist. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

## List Program Workflow States by UUID

> List Program Workflow States by UUID

```shell
GET /workflow/:uuid/state/:state_uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid/state/:state_uuid")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid/state/:state_uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

List Program Workflow State by its `UUID` and `UUID` of its Program Workflow. Returns `404 Not Found` status if the state does not exist. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized`
status is returned.


## Create Program Workflow State

> Create Program Workflow State

```shell
POST /workflow/:uuid/state
{
    "concept": "7737c9ef-80ad-44e6-920f-4106da899df4",
    "initial": true,
    "terminal": false
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"concept\": \"7737c9ef-80ad-44e6-920f-4106da899df4\",\"initial\": true,\"terminal\": false}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid/state")
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

var raw = JSON.stringify({"concept": "7737c9ef-80ad-44e6-920f-4106da899df4","initial": true,"terminal": false});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid/state", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a Program Workflow State you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *[concept](#concepts)* | `Concept_UUID` | UUID of related Concept
    *initial* | `Boolean` | is initial state if true
    *terminal* | `Boolean` | is terminal state if true


## Update Program Workflow State

> Update Program Workflow State

```shell
POST /workflow/:uuid/state/:state_uuid
{
    "concept": "7737c9ef-80ad-44e6-920f-4106da899df4",
    "initial": true,
    "terminal": false
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"concept\": \"7737c9ef-80ad-44e6-920f-4106da899df4\",\"initial\": true,\"terminal\": false}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid/state/:state_uuid")
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

var raw = JSON.stringify({"concept": "7737c9ef-80ad-44e6-920f-4106da899df4","initial": true,"terminal": false});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid/state/:state_uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To update a Program Workflow State by its `UUID` you need to specify below properties in your request body.
Returns a `404 Not Found` status if given state doesn't exist.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *[concept](#concepts)* | `Concept_UUID` | UUID of related Concept
    *initial* | `Boolean` | is initial state if true
    *terminal* | `Boolean` | is terminal state if true

## Delete Program Workflow State

> Delete Program Workflow State

```shell
DELETE /workflow/:uuid/state/:state_uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/workflow/:uuid/state/:state_uuid")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();
```


```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/workflow/:uuid/state/:state_uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Deletes given by UUID Program Workflow State.
Returns a `404 Not Found` status if given state doesn't exist.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.
