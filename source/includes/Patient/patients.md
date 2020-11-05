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

```console
GET /patient/:target_patient_uuid/allergy/:target_allergy_uuid
```
* List allergy subresource by its UUID and parent patient UUID.

    Retrieve a <b>allergy</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if allergy not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

## Create a allergy sub resource with properties 

```console
POST patient/:target_patient_uuid/allergy
{
    "allergen": {},
    "severity": {
        "uuid": "string"
    },
    "comment": "string",
    "reactions": [
        {
            "allergy": {
            "uuid": "string"
        },
        "reaction": {
            "uuid": "string"
        }
    }
]
}
```
* To create an allergy subresource for a specific patient resource, you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query parameter 
    Parameter | Description
    --- | ---
    `target_patient_uuid` | patient resource uuid

    ### Properties for resource

    Parameter | type | Description
    --- | --- | ---
    *allergen* | `String` | value of the allergen
    *severity* | `Severity_UUID` | Severity uuid
    *comment* | `String` | comment for the allergy
    *allergy* | `allergy_UUID` | allergy uuid
    *reaction* | `reaction_UUID` | reaction uuid


## Update allergy sub resource with properties

```console
POST patient/:target_patient_uuid/allergy/:target_allergy_uuid
{
"allergen": {},
"severity": {
    "uuid": "string"
},
"comment": "string",
"reactions": [
    {
        "allergy": {
        "uuid": "string"
    },
    "reaction": {
        "uuid": "string"
    }
}
]
}
```
* Updates an allergy subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if property not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Query parameter 
    
    Parameter | Description
    --- | ---
    `target_patient_uuid` | patient resource uuid
    `target_allergy_uuid` | allergy resource uuid

    ### Properties for resource

    Parameter | type | Description
    --- | --- | ---
    *allergen* | `String` | value of the allergen
    *severity* | `Severity_UUID` | Severity uuid
    *comment* | `String` | comment for the allergy
    *allergy* | `allergy_UUID` | allergy uuid
    *reaction* | `reaction_UUID` | reaction uuid


## Delete allergy sub resource with properties

```console
DELETE /patient/:target_patient_uuid/allergy/:target_allergy_uuid
```
* Delete or retire a target allergy subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
