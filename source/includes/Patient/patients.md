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
5.  [List patientIdentifier sub resource](#list-patientidentifier-sub-resources)
6.  [Create patientIdentifier sub resource with properties](#create-a-patientIdentifier-sub-resource-with-properties)
7.  [Update patientIdentifier sub resource](#update-patientidentifier-sub-resource-with-properties)
8.  [Delete patientIdentifier sub resource](#delete-patientidentifier-sub-resource-with-properties)
9.  [List allergy sub resource](#list-allergy-subresources)
10. [Create allergy sub resource with properties]()
11. [Update allergy sub resource](#update-allergy-sub-resource-with-properties)
12. [Delete allergy sub resource](#delete-allergy-sub-resource-with-properties)

## Search patients

> Search patients

```shell
GET /patient?q=Sarah&v=default&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient?q=Sarah&v=default&limit=1")
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

fetch("/openmrs/ws/rest/v1/patient?q=Sarah&v=default&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "b52ec6f9-0e26-424c-a4a1-c64f9d571eb3",
            "display": "1003EY - Sarah Lewis",
            "identifiers": [
                {
                    "uuid": "5c09b5b6-de14-4a28-bb0c-761a82cbdc1b",
                    "display": "OpenMRS ID = 1003EY",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3/identifier/5c09b5b6-de14-4a28-bb0c-761a82cbdc1b"
                        }
                    ]
                }
            ],
            "person": {
                "uuid": "b52ec6f9-0e26-424c-a4a1-c64f9d571eb3",
                "display": "Sarah Lewis",
                "gender": "F",
                "age": 83,
                "birthdate": "1936-12-04T00:00:00.000+0000",
                "birthdateEstimated": false,
                "dead": false,
                "deathDate": null,
                "causeOfDeath": null,
                "preferredName": {
                    "uuid": "b3918971-c099-4cbe-a323-4b31e4edd493",
                    "display": "Sarah Lewis",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/person/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3/name/b3918971-c099-4cbe-a323-4b31e4edd493"
                        }
                    ]
                },
                "preferredAddress": {
                    "uuid": "1955ab01-20ac-4dc4-8c11-74578b05e004",
                    "display": "Address14081",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/person/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3/address/1955ab01-20ac-4dc4-8c11-74578b05e004"
                        }
                    ]
                },
                "attributes": [],
                "voided": false,
                "birthtime": null,
                "deathdateEstimated": false,
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/person/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3"
                    },
                    {
                        "rel": "full",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/person/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3?v=full"
                    }
                ],
                "resourceVersion": "1.11"
            },
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3?v=full"
                }
            ],
            "resourceVersion": "1.8"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient?q=Sarah&v=default&limit=1&startIndex=1"
        }
    ]
}

```


* Fetch all non-retired patients that match any specified parameters otherwise fetch all non-retired patients. Returns a `200 OK` status with the patient response. 

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of patient.
    

## List patient by UUID.

> List patient by UUID

```shell
GET /patient/:target_patient_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3")
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

fetch("/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a patient by its UUID. Returns a `404 Not Found` status if patient does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a patient

> Create a patient

```shell
POST /patient
{
    "person": "b52ec6f9-0e26-424c-a4a1-c64f9d571eb3",
    "identifiers": [
        {
            "identifier": "1003EY",
            "identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334",
            "location": "8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
            "preferred": false
        }
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"person\": \"b52ec6f9-0e26-424c-a4a1-c64f9d571eb3\",\r\n    \"identifiers\": [\r\n        {\r\n            \"identifier\": \"1003EY\",\r\n            \"identifierType\": \"05a29f94-c0ed-11e2-94be-8c13b969e334\",\r\n            \"location\": \"8d6c993e-c2cc-11de-8d13-0010c6dffd0f\",\r\n            \"preferred\": false\r\n        }\r\n    ]\r\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient")
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

var raw = JSON.stringify({"person":"b52ec6f9-0e26-424c-a4a1-c64f9d571eb3","identifiers":[{"identifier":"1003EY","identifierType":"05a29f94-c0ed-11e2-94be-8c13b969e334","location":"8d6c993e-c2cc-11de-8d13-0010c6dffd0f","preferred":false}]});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* To create a patient you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *[person](#person)* | `Person_UUID` | Person resource UUID (Reqired)
    *[identifiers](#PatientIdentifierType)* | `Array[]: patientIdentifiers` | List of patientIdentifiers (Required)

## Create a patient

> Create a patient

1. for instance we just want to add one more identifier

```shell

POST /patient/:target_patient_uuid/identifier
{
    "identifier": "1003EY",
    "identifierType": "a5d38e09-efcb-4d91-a526-50ce1ba5011a",
    "location": "8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
    "preferred": false
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"identifier\": \"1003EY\",\r\n    \"identifierType\": \"a5d38e09-efcb-4d91-a526-50ce1ba5011a\",\r\n    \"location\": \"8d6c993e-c2cc-11de-8d13-0010c6dffd0f\",\r\n    \"preferred\": false\r\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3/identifier")
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

var raw = JSON.stringify({"identifier":"1003EY","identifierType":"a5d38e09-efcb-4d91-a526-50ce1ba5011a","location":"8d6c993e-c2cc-11de-8d13-0010c6dffd0f","preferred":false});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3/identifier", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Update a target patient with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if patient not exists. If the user is not logged in to perform this action, a `401 Unauthorized status returned`.

  ### Properties

    Parameter | Type | Description
    --- | --- | ---
    *[person](#person)* | `Person_UUID` | Person resource UUID
    *[identifiers](#PatientIdentifierType)* | `Array[]: patientIdentifiers` | List of patientIdentifiers 


## Delete a patient

> Delete a patient

```shell
DELETE /patient/:target_patient_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3?purge=true")
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

fetch("/openmrs/ws/rest/v1/patient/b52ec6f9-0e26-424c-a4a1-c64f9d571eb3?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or retire a target patient by its UUID. Returns a `404 Not Found` status if patient not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    **uuid** | `String` | uuid to delete
    *purge* | `Boolean` | The resource will be voided/retired unless purge = 'true'


## List patientIdentifier sub resources

> List patientIdentifier sub resources

```shell
GET /patient/:target_patient_uuid/identifier
```  

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```

```java

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "display": "OpenMRS ID = 1001W2",
            "uuid": "a122f3ce-4039-4f8c-9d6f-3faf64c7cb69",
            "identifier": "1001W2",
            "identifierType": {
                "uuid": "05a29f94-c0ed-11e2-94be-8c13b969e334",
                "display": "OpenMRS ID",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334",
                        "resourceAlias": "patientidentifiertype"
                    }
                ]
            },
            "location": {
                "uuid": "8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
                "display": "Unknown Location",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/location/8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
                        "resourceAlias": "location"
                    }
                ]
            },
            "preferred": true,
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/a122f3ce-4039-4f8c-9d6f-3faf64c7cb69",
                    "resourceAlias": "identifier"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/a122f3ce-4039-4f8c-9d6f-3faf64c7cb69?v=full",
                    "resourceAlias": "identifier"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

* Retrieve all <b>identifier</b> sub resources of a <b>patient</b> resource by `target_patient_uuid`.Returns a `404 Not Found` status if patientIdentifier not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

## List patientIdentifier sub resource by it's UUID and parent patient UUID.

> List patientIdentifier sub resource by it's UUID

```shell
GET /patient/:target_patient_uuid/identifier/:target_identifier_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/a122f3ce-4039-4f8c-9d6f-3faf64c7cb69")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/a122f3ce-4039-4f8c-9d6f-3faf64c7cb69", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a <b>patientIdentifier</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if patientIdentifier not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

## Create a patientIdentifier sub resource with properties 

> Create a patientIdentifier sub resource

```shell
POST patient/:target_patient_uuid/identifier
{ 
    "identifier" : "111:CLINIC1",
    "identifierType" : "a5d38e09-efcb-4d91-a526-50ce1ba5011a",
    "location" : "8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
    "preferred" : true
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{ \r\n    \"identifier\" : \"111:CLINIC1\",\r\n    \"identifierType\" : \"a5d38e09-efcb-4d91-a526-50ce1ba5011a\",\r\n    \"location\" : \"8d6c993e-c2cc-11de-8d13-0010c6dffd0f\",\r\n    \"preferred\" : true\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var raw = JSON.stringify({"identifier":"111:CLINIC1","identifierType":"a5d38e09-efcb-4d91-a526-50ce1ba5011a","location":"8d6c993e-c2cc-11de-8d13-0010c6dffd0f","preferred":true});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a patientIdentifier subresource for a specific patient resource you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    
### Properties

    Parameter | type | Description
    --- | --- | ---
    *identifier* | `String` | value of the identifier (Required)
    *[identifierType](#patientidentifiertype)* | `Identifier_Type_UUID` | Create identifier from this Identifier_type (Required)
    *[location](#location)* | `Location UUID` | Get patients for this location
    *preferred* | `boolean` | preferred/not preferred identifier

## Update patientIdentifier sub resource with properties

> Update patientIdentifier sub resource

```shell
POST patient/:target_patient_uuid/identifier/:target_identifier_uuid
{ 
    "identifier" : "111:CLINIC2",
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{ \r\n    \"identifier\" : \"111:CLINIC2\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/beb6be1f-07a3-484c-a4ff-92fcb566ddde")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var raw = JSON.stringify({"identifier":"111:CLINIC2"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/e739808f-f166-42ae-aaf3-8b3e8fa13fda/identifier/beb6be1f-07a3-484c-a4ff-92fcb566ddde", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Updates an patientIdentifier subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *identifier* | `String` | updated value of the identifier
    *[identifierType](#patientidentifiertype)* | `Identifier_Type_UUID` | Create identifier from this Identifier_type
    *[location](#location)* | `Location UUID` | updated location
    *preferred* | `boolean` | updated status of preferred/not preferred identifier


## Delete patientIdentifier sub resource with properties

> Delete patientIdentifier sub resource

```shell
DELETE /patient/:target_patient_uuid/identifier/:target_identifier_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/c7ea5ea9-bec7-4ad0-a803-0ef2dee8fca5/identifier/e5ce3659-9118-4912-8c2f-6d470c2c7940?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/c7ea5ea9-bec7-4ad0-a803-0ef2dee8fca5/identifier/e5ce3659-9118-4912-8c2f-6d470c2c7940?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or retire a target identifier subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    

## List allergy subresources

> List allergy subresources

```shell
GET /patient/:target_patient_uuid/allergy/
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  body: null,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87", requestOptions)
  .then(response => response.text())


```

> Success Response

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

> List allergy subresource by its UUID and parent patient UUID

```shell
GET /patient/:target_patient_uuid/allergy/:target_allergy_uuid
```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  body: null,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/2d440f27-7a87-4a14-bd21-efb5e99c58dc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/2d440f27-7a87-4a14-bd21-efb5e99c58dc")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

* Retrieve a <b>allergy</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if allergy not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

## Create a allergy sub resource with properties 

> Create a allergy sub resource

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
  .url("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var raw = JSON.stringify({"allergen":{"allergenType":"DRUG","codedAllergen":{"uuid":"162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},"severity":{"uuid":"1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"},"comment":"severe allergy","reactions":[{"reaction":{"uuid":"1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},{"reaction":{"uuid":"139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}}]});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/", requestOptions)
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

> Update allergy sub resource

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
  .url("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var raw = JSON.stringify({"allergen":{"allergenType":"DRUG","codedAllergen":{"uuid":"162298AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},"severity":{"uuid":"1500AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"},"comment":"severe allergy","reactions":[{"reaction":{"uuid":"1067AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}},{"reaction":{"uuid":"139084AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}}]});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783", requestOptions)
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

> Delete allergy sub resource

```shell
DELETE /patient/:target_patient_uuid/allergy/:target_allergy_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=2375C8D206AB15F32A3FA3FEA5824BC7");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patient/3d808dc6-e9b8-4ade-b3fd-32bb0eb08f87/allergy/ba6e3813-1390-4b4d-9c0e-01de47bb7783?purge=true", requestOptions)
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
    
