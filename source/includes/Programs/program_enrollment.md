# Program Enrollment

## Program Enrollment Overview

A program enrollment represents the fact that a patient is enrolled in one of the Programs over a time period at a Location. This is longitudinal data with a start date and end date.

## Available Operations for Program Enrollment type

1. [List Program Enrollment by UUID](#list-program-enrollment-by-uuid)
2. [List Program Enrollments by Patient](#list-program-enrollments-by-patient)
3. [Update Program Enrollment Patient State](#update-program-enrollment-patient-state)

## List Program Enrollment by UUID

> List Program Enrollment by UUID

```shell
GET /programenrollment/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/programenrollment/:uuid")
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

fetch("/openmrs/ws/rest/v1/programenrollment/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "uuid": "19ff2ee8-691f-4c4c-a0af-644a0d4198a7",
    "patient": {
        "uuid": "c5149f66-2695-102d-b4c2-001d929acb54",
        "display": "NNO 110 CCC - Jen George Henry",
        "links": [
            {
                "rel": "self",
                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/patient/c5149f66-2695-102d-b4c2-001d929acb54"
            }
        ]
    },
    "program": {
        "uuid": "acbd87f3-566f-4386-a11e-877e612d3911",
        "name": "Palliative care program",
        "allWorkflows": [
            {
                "uuid": "F2D47AE5-7083-4901-B630-51860D09A884",
                "concept": {
                    "uuid": "e7a7c2ca-7433-4851-8687-67e8541ca40b",
                    "display": "Palliative Care Treatment Status",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/e7a7c2ca-7433-4851-8687-67e8541ca40b"
                        }
                    ]
                },
                "retired": false,
                "states": [
                    {
                        "uuid": "e92017b9-45cf-41b9-bc69-a5b0232544c1",
                        "retired": false,
                        "concept": {
                            "uuid": "655b604e-977f-11e1-8993-905e29aff6c1",
                            "display": "Patient transferred out",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/655b604e-977f-11e1-8993-905e29aff6c1"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/e92017b9-45cf-41b9-bc69-a5b0232544c1"
                            }
                        ]
                    },
                    {
                        "uuid": "7c1f852e-5120-4371-8136-f64614f5dfc7",
                        "retired": false,
                        "concept": {
                            "uuid": "65664784-977f-11e1-8993-905e29aff6c1",
                            "display": "On treatment",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/65664784-977f-11e1-8993-905e29aff6c1"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/7c1f852e-5120-4371-8136-f64614f5dfc7"
                            }
                        ]
                    },
                    {
                        "uuid": "4bed1c08-1fe9-4972-8e7e-e93323c9f2c4",
                        "retired": false,
                        "concept": {
                            "uuid": "655b5e46-977f-11e1-8993-905e29aff6c1",
                            "display": "Patient died",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/655b5e46-977f-11e1-8993-905e29aff6c1"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/4bed1c08-1fe9-4972-8e7e-e93323c9f2c4"
                            }
                        ]
                    },
                    {
                        "uuid": "0f034ef4-3f70-4514-a020-5fb928fc3394",
                        "retired": false,
                        "concept": {
                            "uuid": "655b5f4a-977f-11e1-8993-905e29aff6c1",
                            "display": "Patient defaulted",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/655b5f4a-977f-11e1-8993-905e29aff6c1"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/0f034ef4-3f70-4514-a020-5fb928fc3394"
                            }
                        ]
                    },
                    {
                        "uuid": "13490dc8-e5bd-11e7-80c1-9a214cf093ae",
                        "retired": false,
                        "concept": {
                            "uuid": "6566dba4-977f-11e1-8993-905e29aff6c1",
                            "display": "Discharged",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/6566dba4-977f-11e1-8993-905e29aff6c1"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/13490dc8-e5bd-11e7-80c1-9a214cf093ae"
                            }
                        ]
                    },
                    {
                        "uuid": "b35ed57c-7d54-4795-b678-f0947a135fda",
                        "retired": false,
                        "concept": {
                            "uuid": "655a6acc-977f-11e1-8993-905e29aff6c1",
                            "display": "Treatment stopped",
                            "links": [
                                {
                                    "rel": "self",
                                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/655a6acc-977f-11e1-8993-905e29aff6c1"
                                }
                            ]
                        },
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/b35ed57c-7d54-4795-b678-f0947a135fda"
                            }
                        ]
                    }
                ],
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884"
                    }
                ]
            }
        ],
        "links": [
            {
                "rel": "self",
                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/program/acbd87f3-566f-4386-a11e-877e612d3911"
            }
        ]
    },
    "display": "Palliative care program",
    "dateEnrolled": "2021-01-19T00:00:00.000+0000",
    "dateCompleted": "2021-09-01T00:00:00.000+0000",
    "location": {
        "uuid": "0d414ce2-5ab4-11e0-870c-9f6107fee88e",
        "display": "Neno District Hospital",
        "links": [
            {
                "rel": "self",
                "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/location/0d414ce2-5ab4-11e0-870c-9f6107fee88e"
            }
        ]
    },
    "voided": false,
    "outcome": null,
    "states": [
        {
            "state": {
                "uuid": "7c1f852e-5120-4371-8136-f64614f5dfc7",
                "retired": false,
                "concept": {
                    "uuid": "65664784-977f-11e1-8993-905e29aff6c1",
                    "display": "On treatment",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/65664784-977f-11e1-8993-905e29aff6c1"
                        }
                    ]
                },
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/7c1f852e-5120-4371-8136-f64614f5dfc7"
                    }
                ]
            },
            "uuid": "fe0b3ca4-0d34-4b28-b686-49ec49dc6e1f",
            "startDate": "2021-01-19T00:00:00.000+0000",
            "endDate": "2021-09-01T00:00:00.000+0000",
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/19ff2ee8-691f-4c4c-a0af-644a0d4198a7/state/fe0b3ca4-0d34-4b28-b686-49ec49dc6e1f"
                }
            ]
        },
        {
            "state": {
                "uuid": "b35ed57c-7d54-4795-b678-f0947a135fda",
                "retired": false,
                "concept": {
                    "uuid": "655a6acc-977f-11e1-8993-905e29aff6c1",
                    "display": "Treatment stopped",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/concept/655a6acc-977f-11e1-8993-905e29aff6c1"
                        }
                    ]
                },
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/workflow/F2D47AE5-7083-4901-B630-51860D09A884/state/b35ed57c-7d54-4795-b678-f0947a135fda"
                    }
                ]
            },
            "uuid": "c44546a6-611b-4231-8a65-4e9d570580cd",
            "startDate": "2021-09-01T00:00:00.000+0000",
            "endDate": "2021-09-01T00:00:00.000+0000",
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/19ff2ee8-691f-4c4c-a0af-644a0d4198a7/state/c44546a6-611b-4231-8a65-4e9d570580cd"
                }
            ]
        }
    ],
    "attributes": [],
    "links": [
        {
            "rel": "self",
            "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/19ff2ee8-691f-4c4c-a0af-644a0d4198a7"
        },
        {
            "rel": "full",
            "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/19ff2ee8-691f-4c4c-a0af-644a0d4198a7?v=full"
        }
    ],
    "resourceVersion": "1.8"
}
```

Fetch Program Enrollment by UUID. Return a `404 Not Found` status if given program enrollment doesn't exist.
If user is not logged in to perform this action, a `401 Unauthorized` status is returned.

## List Program Enrollments by Patient

> List Program Enrollments by Patient

```shell
GET /programenrollment?patient=:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/programenrollment?patient=:uuid")
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

fetch("/openmrs/ws/rest/v1/programenrollment?patient=:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "08044a4d-f323-45ad-98fd-9b421bbf36b6",
            "display": "CHRONIC CARE PROGRAM",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/08044a4d-f323-45ad-98fd-9b421bbf36b6"
                }
            ]
        },
        {
            "uuid": "9a507e64-1520-4441-ba04-49ed63ea9e07",
            "display": "MENTAL HEALTH CARE PROGRAM",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/9a507e64-1520-4441-ba04-49ed63ea9e07"
                }
            ]
        },
        {
            "uuid": "19ff2ee8-691f-4c4c-a0af-644a0d4198a7",
            "display": "Palliative care program",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://bwenzi.pih-emr.org:8081/openmrs/ws/rest/v1/programenrollment/19ff2ee8-691f-4c4c-a0af-644a0d4198a7"
                }
            ]
        }
    ]
}
```

Fetch Program Enrollment by Patient. Returns a `200 OK` status. If Patient does not exist or has no program enrollments then it returns an empty results array.
If user is not logged in to perform this action, a `401 Unauthorized` status is returned.

## Update Program Enrollment Patient State

> Update Program Enrollment Patient State

```shell
POST /programenrollment/:uuid
{
    "states":[{
        "state":"b35ed57c-7d54-4795-b678-f0947a135fda",
        "startDate":"2021-09-01"
        }]
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"states\":[{\"state\":\"b35ed57c-7d54-4795-b678-f0947a135fda\",\"startDate\":\"2021-09-01\"}]}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/programenrollment/:uuid")
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

var raw = JSON.stringify({"states":[{"state":"b35ed57c-7d54-4795-b678-f0947a135fda","startDate":"2021-09-01"}]});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/programenrollment/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To update a Program Enrollment Patient State by its `UUID` you need to specify below properties in your request body.
Returns a `404 Not Found` status if given state doesn't exist.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    states | `Array[]:` *[Program Workflow States](#create-program-workflow-state)* | List with of one Program Workflow State
    
