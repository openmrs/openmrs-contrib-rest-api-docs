# Patients

## Patients Overview

* Anyone who receives care in OpenMRS must be a **Patient**.

* Every Patient must have at least one Identifier, which is explained below. (for example,
Anyone who has an Encounter or who is enrolled in a Program is a Patient.)

* A Patient is also a Person, meaning they must have at least one name, and they may have addresses.

## Subresource types of Patient

### PatientIdentifier (Identifier)

* A PatientIdentifier is a medical record number assigned by your facility, used to identify and re-identify the patient on subsequent visits.

### Allergy

* OpenMRS lets you manually maintain an **Allergy List** for a patient, including the allergen, reaction, severity, etc.

### 1. Allergen
An allergen refers to a substance capable of triggering a response that starts in the immune system and results in an allergic reaction, for eg in drugs Aspirin, Codeine.., in food beef, eggs.. and others like dust and pollen.

### 2. Severity
Refers to the severity of the allergy e.g. mild , moderate and severe (`uuid:=1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA`)

### 3. Reactions
Reactions refers to the effects of the allergy on anybody for e.g. headache(`uuid:=139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA`) or even unknown(`uuid:=1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA`) 


## Available operations for Patients

1.  [List Patients](#search-patients)
2.  [Create a patient record](#create-a-patient)
3.  [Update a patient record](#update-a-patient)
4.  [Delete a patient record](#delete-a-patient)
5.  [List patientIdentifier sub resource](#list-patientIdentifier-sub-resources)
6.  [Create patientIdentifier sub resource with properties](#create-a-patientIdentifier-sub-resource-with-properties)
7.  [Update patientIdentifier sub resource](#update-patientidentifier-sub-resource-with-properties)
8.  [Delete patientIdentifier sub resource](#delete-patientidentifier-sub-resource-with-properties)
9.  [List allergy sub resource](#list-allergy-sub-resources)
10. [Create allergy sub resource with properties]()
11. [Update allergy sub resource](#update-allergy-sub-resource-with-properties)
12. [Delete allergy sub resource](#delete-allergy-sub-resource-with-properties)

## Search patients

### Search patients

```console
GET /patient?
country=india
&gender=M
```

    Fetch all non-retired patients that match any specified parameters otherwise fetch all non-retired patients. Returns a `200 OK` status with the patient response. 

### Query Parameters

    Parameter | Description
    --- | ---
    matchSimilar | use this parameter to enter anything to match 
    country | Country where the patient is registered
    birthDate | must be used with matchSimilar
    Gender | Gender of the patient
    city | City where the patient is registered
    address  | Address of the patients
    familyName | must be used with matchSimilar
    middleName | must be used with matchSimilar
    postalCode | must be used with matchSimilar
    givenname  | must be used with matchSimilar
    state | must be used with matchSimilar


### List patient by UUID.

```console
GET /patient/:target_patient_uuid
```

    Retrieve a patient by its UUID. Returns a `404 Not Found` status if patient does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a patient

```console
POST /patient
{
    "person": "uuid",
    "identifiers": [
    {
        "identifier": "string",
        "identifierType": "uuid",
        "location": "uuid",
        "preferred": true
    }
    ]
}
```

* To create a patient you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Properties

    Parameter | Type | Description
    --- | --- | ---
    *person* | `PERSON_UUID` | Person resource UUID
    *identifiers* | `Array[]: Identifiers` | List of patientIdentifiers

## Update a patient

```console
    POST /patient/:target_patient_uuid
    -d modified_patient_object
```

* Update a target patient with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if patient not exists. If the user is not logged in to perform this action, a `401 Unauthorized status returned`.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_patient_uuid` | Target patient resource UUID

    ### Properties

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Patient` | Patient resource with updated properties


## Delete a patient

```console
DELETE /patient/:target_patient_uuid?purge=true
```

* Delete or retire a target patient by its UUID. Returns a `404 Not Found` status if patient not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    **uuid** | `String` | uuid to delete
    *purge* | `Boolean` | The resource will be voided/retired unless purge = 'true'

## List patientIdentifier sub resources

* ### List all patientIdentifier sub resources for a patient.

```console
GET /patient/:target_patient_uuid/identifier
```  

    Retrieve all <b>identifier</b> sub resources of a <b>patient</b> resource by `target_patient_uuid`.Returns a `404 Not Found` status if patientIdentifier not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

* ### List patientIdentifier sub resource by it's UUID and parent patient UUID.

```console
GET /patient/:target_patient_uuid/identifier/:target_identifier_uuid
```

    Retrieve a <b>patientIdentifier</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if patientIdentifier not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

## Create a patientIdentifier sub resource with properties 

```console
POST patient/:target_patient_uuid/identifier
{ 
    "identifier" : "string",
    "identifierType" : "target_identifer_uuid",
    "location" : "target_location_uuid",
    "preferred" : true/false
}
```

* To create a patientIdentifier subresource for a specific patient resource you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query parameter 
    Parameter | Description
    --- | ---
    `target_patient_uuid` | patient resource uuid

    ### Properties for resource

    Parameter | type | Description
    --- | --- | ---
    *identifier* | `String` | value of the identifier
    *identifierType* | `Identifier_Type_UUID` | Create identifier from this Identifier_type
    *location* | `Location UUID` | Get patients for this location
    *preferred* | `boolean` | preferred/not preferred identifier

## Update patientIdentifier sub resource with properties

```console
POST patient/:target_patient_uuid/identifier/:target_identifier_uuid
{ 
"identifier" : "string",
"identifierType" : "target_identifer_uuid",
"location" : "target_location_uuid",
"preferred" : true/false
}
```

* Updates an patientIdentifier subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Properties

    Parameter | Type | Description
    --- | --- | ---
    *identifier* | `String` | updated value of the identifier
    *identifierType* | `Identifier_Type_UUID` | Create identifier from this Identifier_type
    *location* | `Location UUID` | updated location
    *preferred* | `boolean` | updated status of preferred/not preferred identifier


## Delete patientIdentifier sub resource with properties

```console
DELETE /patient/:target_patient_uuid/identifier/:target_identifier_uuid
```

* Delete or retire a target identifier subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    

## List allergy subresources

```console
GET /patient/:target_patient_uuid/allergy/
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: null,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87", requestOptions)
  .then(response => response.text())


```

```response

{
    "results": [
        {
            "display": "ACE inhibitors",
            "uuid": "2d440f27-7a87-4a14-bd21-efb5e99c58dc",
            "allergen": {
                "allergenType": "DRUG",
                "codedAllergen": {
                    "uuid": "162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                    "display": "ACE inhibitors",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                        }
                    ]
                },
                "nonCodedAllergen": ""
            },
            "severity": {
                "uuid": "1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                "display": "Severe",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                    }
                ]
            },
            "comment": "take precautions can cause problems",
            "reactions": [
                {
                    "reaction": {
                        "uuid": "1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                        "display": "Unknown",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                            }
                        ]
                    },
                    "reactionNonCoded": null
                },
                {
                    "reaction": {
                        "uuid": "139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                        "display": "Headache",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                            }
                        ]
                    },
                    "reactionNonCoded": null
                },
                {
                    "reaction": {
                        "uuid": "159098AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                        "display": "Hepatotoxicity",
                        "links": [
                            {
                                "rel": "self",
                                "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/159098AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                            }
                        ]
                    },
                    "reactionNonCoded": null
                }
            ],
            "patient": {
                "uuid": "3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87",
                "display": "100J7W - AGB Ake",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87"
                    }
                ]
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/2d440f27-7a87-4a14-bd21-efb5e99c58dc"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/2d440f27-7a87-4a14-bd21-efb5e99c58dc?v=full"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

* Retrieve a <b>allergy</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if allergy not exists for that patient. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 


## List allergy subresource by its UUID and parent patient UUID.

```shell
GET /patient/:target_patient_uuid/allergy/:target_allergy_uuid
```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: null,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/2d440f27-7a87-4a14-bd21-efb5e99c58dc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/2d440f27-7a87-4a14-bd21-efb5e99c58dc")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

* Retrieve a <b>allergy</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if allergy not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

## Create a allergy sub resource with properties 

```shell
POST patient/:target_patient_uuid/allergy
{
    "allergen": {
        "allergenType": "DRUG",
        "codedAllergen": {
            "uuid": "162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
        }
    },
    "severity": {
        "uuid": "1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
    },
    "comment": "severe allergy",
    "reactions": [
        {
            "reaction": {
                "uuid": "1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
            }
        },
        {
            "reaction": {
                "uuid": "139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
            }
        }
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"allergen\": {\r\n        \"allergenType\": \"DRUG\",\r\n        \"codedAllergen\": {\r\n            \"uuid\": \"162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n        }\r\n    },\r\n    \"severity\": {\r\n        \"uuid\": \"1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n    },\r\n    \"comment\": \"severe allergy\",\r\n    \"reactions\": [\r\n        {\r\n            \"reaction\": {\r\n                \"uuid\": \"1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n            }\r\n        },\r\n        {\r\n            \"reaction\": {\r\n                \"uuid\": \"139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n            }\r\n        }\r\n    ]\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var raw = JSON.stringify({"allergen":{"allergenType":"DRUG","codedAllergen":{"uuid":"162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},"severity":{"uuid":"1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"},"comment":"severe allergy","reactions":[{"reaction":{"uuid":"1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},{"reaction":{"uuid":"139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}}]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create an allergy subresource for a specific patient resource, you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    
### Properties

    Parameter | type | Description
    --- | --- | ---
    *allergen* | `String` | value of the allergen (Required)
    *severity* | `Severity_UUID` | Severity uuid 
    *comment* | `String` | comment in reference to the allergy
    *reaction* | `reaction_UUID` | reaction uuid


## Update allergy sub resource with properties

```shell
POST patient/:target_patient_uuid/allergy/:target_allergy_uuid
{
    "allergen": {
        "allergenType": "DRUG",
        "codedAllergen": {
            "uuid": "162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
        }
    },
    "severity": {
        "uuid": "1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
    },
    "comment": "severe allergy",
    "reactions": [
        {
            "reaction": {
                "uuid": "1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
            }
        },
        {
            "reaction": {
                "uuid": "139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
            }
        }
    ]
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"allergen\": {\r\n        \"allergenType\": \"DRUG\",\r\n        \"codedAllergen\": {\r\n            \"uuid\": \"162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n        }\r\n    },\r\n    \"severity\": {\r\n        \"uuid\": \"1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n    },\r\n    \"comment\": \"severe allergy\",\r\n    \"reactions\": [\r\n        {\r\n            \"reaction\": {\r\n                \"uuid\": \"1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n            }\r\n        },\r\n        {\r\n            \"reaction\": {\r\n                \"uuid\": \"139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\r\n            }\r\n        }\r\n    ]\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var raw = JSON.stringify({"allergen":{"allergenType":"DRUG","codedAllergen":{"uuid":"162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},"severity":{"uuid":"1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"},"comment":"severe allergy","reactions":[{"reaction":{"uuid":"1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},{"reaction":{"uuid":"139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}}]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Updates an allergy subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if property not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

### Properties

    Parameter | type | Description
    --- | --- | ---
    *allergen* | `String` | value of the allergen
    *severity* | `Severity_UUID` | Severity uuid
    *comment* | `String` | comment for the allergy
    *reaction* | `reaction_UUID` | reaction uuid


## Delete allergy sub resource with properties

```shell
DELETE /patient/:target_patient_uuid/allergy/:target_allergy_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or retire a target allergy subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
