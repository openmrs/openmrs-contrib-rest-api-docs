# Encounters 

## Encounter Overview

* An encounter represents an interaction between a patient and the healthcare system at a single point in time. Common examples would be a patient seeing a doctor during a clinic visit, a patient going to the lab to have blood drawn for testing, or telephone call between a provider and the patient).

* Each Encounter has an encounter type, date/time, location, and provider.

* Encounters are classified into Encounter Types, which describe the type of interaction the Encounter represents – e.g., "HIV Initial", "Pediatric Follow Up", "Lab"). Implementations can define their own types of encounters.

* One or more encounters may be grouped within a **Visit** (e.g., an outpatient clinic visit or a hospitalization).

* Every Encounter can have 0 to n **Observations** associated with it.
 
* Every Encounter can have 0 to n **Orders** associated with it.

* More than one Encouter can be associated with a single visit.

 
## Let's look at an example of Encounter

* During a typical Amani Clinic Outpatient Visit, a patient checks in at registration is seen by a doctor and receives medicine dispensed in the pharmacy. This would be recorded as **one visit** containing three encounters, whose types are **Registration, Consultation and Dispensing**.

## Sub Resource types of Encounter

### Encounter Provider

* A [Provider](#provider) is a person who provides care or services to patients. A provider may be a clinician like a doctor or a nurse, a social worker, or a lab tech, any healthcare worker that a patient can have an encounter with is a provider.

## Available operations for Encounter 

1. [List encounters](#list-encounters)
2. [Create an encounter](#create-an-encounter)
3. [Update an encounter](#update-an-encounter)
4. [Delete an encounter](#delete-an-encounter)
5. [List encounter provider sub resource](#list-encounter-provider-sub-resources)
6. [Create encounter provider  sub resource with properties](#create-encounter-provider-sub-resource-with-properties)
7. [Update encounter provider  sub resource](#update-encounter-provider-sub-resource)
6. [Delete encounter provider  sub resource](#delete-encounter-provider-sub-resource)


## List encounters

> List encounters

```shell
GET /encounter?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&concept=18316c68-b5f9-4986-b76d-9975cd0ebe31&fromdate=2016-10-08&v=default&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&concept=18316c68-b5f9-4986-b76d-9975cd0ebe31&fromdate=2016-10-08&v=default&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=3EFCD2FD54D00BE8491DFFD43AA706DC")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=3EFCD2FD54D00BE8491DFFD43AA706DC");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&concept=18316c68-b5f9-4986-b76d-9975cd0ebe31&fromdate=2016-10-08&v=default&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response
   
```response

{
    "results": [
        {
            "uuid": "d3360c01-9813-4ff8-bd81-909af6612632",
            "display": "Vitals 24/02/2015",
            "encounterDatetime": "2015-02-24T06:08:25.000+0000",
            "patient": {
                "uuid": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
                "display": "1000C6 - Elizabeth Johnson",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/96be32d2-9367-4d1d-a285-79a5e5db12b8"
                    }
                ]
            },
            "location": {
                "uuid": "58c57d25-8d39-41ab-8422-108a0c277d98",
                "display": "Outpatient Clinic",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/58c57d25-8d39-41ab-8422-108a0c277d98"
                    }
                ]
            },
            "form": {
                "uuid": "a000cb34-9ec1-4344-a1c8-f692232f6edd",
                "display": "Vitals",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/form/a000cb34-9ec1-4344-a1c8-f692232f6edd"
                    }
                ]
            },
            "encounterType": {
                "uuid": "67a71486-1a54-468f-ac3e-7091a9a79584",
                "display": "Vitals",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encountertype/67a71486-1a54-468f-ac3e-7091a9a79584"
                    }
                ]
            },
            "obs": [
                {
                    "uuid": "22639f6e-b4b8-4c99-8a6a-d1faff59cff6",
                    "display": "Diastolic blood pressure: 36.0",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/obs/22639f6e-b4b8-4c99-8a6a-d1faff59cff6"
                        }
                    ]
                },
                {
                    "uuid": "eb66922c-c0a9-49e4-8648-18d68f9a4499",
                    "display": "Weight (kg): 63.0",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/obs/eb66922c-c0a9-49e4-8648-18d68f9a4499"
                        }
                    ]
                },
                {
                    "uuid": "c29194d7-af8b-449d-a0e5-7ca6ec19ce65",
                    "display": "Height (cm): 93.0",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/obs/c29194d7-af8b-449d-a0e5-7ca6ec19ce65"
                        }
                    ]
                }
            ],
            "orders": [],
            "voided": false,
            "visit": {
                "uuid": "69b3265b-1521-4c27-8d3f-ae99b689e7a9",
                "display": "Facility Visit @ Unknown Location - 24/02/2015 06:00",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/visit/69b3265b-1521-4c27-8d3f-ae99b689e7a9"
                    }
                ]
            },
            "encounterProviders": [],
            "diagnoses": [],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632?v=full"
                }
            ],
            "resourceVersion": "2.2"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encounter?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&concept=18316c68-b5f9-4986-b76d-9975cd0ebe31&fromdate=2016-10-08&v=default&limit=1&startIndex=1"
        }
    ]
}
```

* Quickly filter encounters with given query parameters. Add `includeAll=true` parameter if wanting to include voided encounters. Returns a `404 Not Found` status if Encounter not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Get encounter by Encounter UUID, Patient Identifier or name
    *[patient](#patients)* | `Patient UUID` | Get encounter(s) for a patient
    *[encounterType](#encounter-type)* | `Encounter_Type UUID` | Filter by encounter type (must be used with patient parameter cant be used independently)
    *[order](#order)* | `Order UUID` | Filter to encounter(s) containing the specified order (must be used with patient)
    *[obsConcept](#concepts)* | `Concept UUID` | Filter to encounter(s) containing observation(s) for the given concept (must be used with patient parameter cant be used independently)
    *obsValues* | `String` | Filter to encounter(s) containing an observations with the given value (must be used with patient and obsConcept parameters together )
    *fromdate* | `Date or Timestamp (ISO 8601)` | Start date of the encounter (must be used with patient parameter cant be used independently)
    *todate* | `Date or Timestamp (ISO 8601)` | End date of the encounter (must be used with patient parameter cant be used independently)
    *includeAll* | `Boolean` | If true, returns also voided Encounters  

    
## List encounter by UUID.

> List encounter by UUID

```shell
GET /encounter/:target_encounter_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=3EFCD2FD54D00BE8491DFFD43AA706DC")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=3EFCD2FD54D00BE8491DFFD43AA706DC");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an encounter by its UUID. Returns a `404 Not Found` status if Encounter not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an encounter

> Creating a new Encouter in existing visit

```shell
POST /Encounter
{
  "encounterDatetime": "2015-02-24T06:08:25.000+0000",
  "patient": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
  "encounterType": "67a71486-1a54-468f-ac3e-7091a9a79584",
  "location": "58c57d25-8d39-41ab-8422-108a0c277d98",
  "encounterProviders": [
    {
      "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
      "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
    }
  ],
  "visit":"69b3265b-1521-4c27-8d3f-ae99b689e7a9"
}
```

> Creating a new Encouter for a new Visit

```shell
POST /Encounter
{
    "encounterDatetime": "2015-02-24T06:08:25.000+0000",
    "patient": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
    "encounterType": "67a71486-1a54-468f-ac3e-7091a9a79584",
    "location": "58c57d25-8d39-41ab-8422-108a0c277d98",
    "encounterProviders": [
        {
            "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
            "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
        }
    ],
    "visit": {
        "patient": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
        "visitType": "7b0f5697-27e3-40c4-8bae-f4049abfb4ed",
        "startDatetime": "2015-02-24T06:08:25.000+0000",
        "stopDatetime" : "2015-02-24T06:09:25.000+0000"
    }
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"encounterDatetime\": \"2015-02-24T06:08:25.000+0000\",\r\n    \"patient\": \"96be32d2-9367-4d1d-a285-79a5e5db12b8\",\r\n    \"encounterType\": \"67a71486-1a54-468f-ac3e-7091a9a79584\",\r\n    \"location\": \"58c57d25-8d39-41ab-8422-108a0c277d98\",\r\n    \"encounterProviders\": [\r\n        {\r\n            \"provider\": \"bb1a7781-7896-40be-aaca-7d1b41d843a6\",\r\n            \"encounterRole\": \"240b26f9-dd88-4172-823d-4a8bfeb7841f\"\r\n        }\r\n    ],\r\n    \"visit\": {\r\n        \"patient\": \"96be32d2-9367-4d1d-a285-79a5e5db12b8\",\r\n        \"visitType\": \"7b0f5697-27e3-40c4-8bae-f4049abfb4ed\",\r\n        \"startDatetime\": \"2015-02-24T06:08:25.000+0000\",\r\n        \"stopDatetime\" : \"2015-02-24T06:09:25.000+0000\"\r\n    }\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/encounter")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=3D897DB2CD0E3465BBCF887F133ED465")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=3D897DB2CD0E3465BBCF887F133ED465");

var raw = JSON.stringify({"encounterDatetime":"2015-02-24T06:08:25.000+0000","patient":"96be32d2-9367-4d1d-a285-79a5e5db12b8","encounterType":"67a71486-1a54-468f-ac3e-7091a9a79584","location":"58c57d25-8d39-41ab-8422-108a0c277d98","encounterProviders":[{"provider":"bb1a7781-7896-40be-aaca-7d1b41d843a6","encounterRole":"240b26f9-dd88-4172-823d-4a8bfeb7841f"}],"visit":{"patient":"96be32d2-9367-4d1d-a285-79a5e5db12b8","visitType":"7b0f5697-27e3-40c4-8bae-f4049abfb4ed","startDatetime":"2015-02-24T06:08:25.000+0000","stopDatetime":"2015-02-24T06:09:25.000+0000"}});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/encounter", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create an encounter you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounterDatetime* | `Date (ISO8601 Long)` | The date and time the encounter was created. Should be between visit start and stop dates (required)
    *[patient](#patients)* | `Patient UUID` | The patient to whom the encounter applies (Required)
    *[encounterType](#encounter-type)* | `EncounterType UUID` | The type of encounter – e.g., Initial visit, Return visit, etc. (required)
    *[location](#location)* | `Location UUID` | The location at which the encounter occurred (required)
    *[encounterProviders](#providers)* | `Array of Provider UUID and associated Encounter Role UUID` | An array of providers and their role within the encounter. At least one provider is required    
    *[obs](#observations)* | `Array[]: Obs` | Array of observations and values for the encounter    
    *[orders](#order)* | `Array[]: Order UUID` | List of orders created during the encounter    
    *[form](#forms)* | `Form UUID` | Target Form UUID to be filled for the encounter
    *[visit](#visits)* | `Visit UUID` | When creating an encounter for an existing visit, this specifies the visit this encounter will be grouped into.
   

## Update an encounter

> Update an encounter

```shell
POST /encounter/:target_encounter_uuid
{
  "encounterDatetime": "2015-02-24T06:08:25.000+0001"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"encounterDatetime\": \"2015-02-24T06:08:25.000+0001\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var raw = JSON.stringify({"encounterDatetime":"2015-02-24T06:08:25.000+0001"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


*  Update a target encounter with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if Encounter not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounterDatetime* | `Date (ISO8601 Long)` | The date and time the encounter was created. Should be between visit start and stop dates. 
    *[patient](#patients)* | `Patient UUID` | The patient to whom the encounter applies 
    *[encounterType](#encounter-type)* | `EncounterType UUID` | The type of encounter – e.g., Initial visit, Return visit, etc. 
    *[location](#location)* | `Location UUID` | The location at which the encounter occurred 
    *[encounterProviders](#providers)* | `Array of Provider UUID and associated Encounter Role UUID` | An array of providers and their role within the encounter. At least one provider is required    
    *[obs](#observations)* | `Array[]: Obs` | Array of observations and values for the encounter    
    *[orders](#order)* | `Array[]: Order UUID` | List of orders created during the encounter    
    *[form](#forms)* | `Form UUID` | Target Form UUID to be filled for the encounter
    *[visit](#visits)* | `Visit UUID` | When creating an encounter for an existing visit, this specifies the visit this encounter will be grouped into.
    
## Delete an encounter

> Delete an encounter

```shell
  DELETE /encounter/:target_encounter_uuid?purge=true
```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```


* Delete or Void a target encounter by its UUID. Returns a `404 Not Found` status if Encounter not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’


## List encounter provider subresources

> List encounter provider subresources

```shell
GET /encounter/:target_encounter_uuid/encounterprovider 
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


> Success Response

```response

{
    "results": [
        {
            "uuid": "7146fea4-af02-4452-b4ed-240e71da7224",
            "provider": {
                "uuid": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
                "display": "doctor - Jake Smith",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/provider/bb1a7781-7896-40be-aaca-7d1b41d843a6"
                    }
                ]
            },
            "encounterRole": {
                "uuid": "240b26f9-dd88-4172-823d-4a8bfeb7841f",
                "display": "Clinician",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f"
                    }
                ]
            },
            "voided": false,
            "links": [
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224?v=full"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```

* Retrieve all encounter provider sub resources of an encounter resource by target_encounter_uuid. Returns a `404 Not Found` status if encounter provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status is returned.


## List encounter provider subresources by it's UUID and parent encounter UUID.

> List encounter provider subresources by it's UUID

```shell
GET /encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an encounter provider sub resources of a encounter resource. Returns a `404 Not Found` status if encounter provider not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
## Create an encounter provider sub resource with properties

> Create an encounter provider sub resource with properties

```shell
POST encounter/:target_encounter_uuid/encounterprovider 
{
  "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
  "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"provider\": \"bb1a7781-7896-40be-aaca-7d1b41d843a6\",\r\n  \"encounterRole\": \"240b26f9-dd88-4172-823d-4a8bfeb7841f\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var raw = JSON.stringify({"provider":"bb1a7781-7896-40be-aaca-7d1b41d843a6","encounterRole":"240b26f9-dd88-4172-823d-4a8bfeb7841f"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider", requestOptions)


```

* To Create an attribute subresource for a specific visit resource, you need to specify below attributes in the request body. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[provider](#providers)* | `Provider_Type UUID` | UUID of a provider currently registered in OpenMRS (required)
    *[encounterRole](#encounter-role)* | `Encounter_Role UUID` | UUID of encounter role. This is the role provider will participate during this encounter (required)
    
 
 
## Update encounter provider subresource

> Update encounter provider subresource

```shell
POST encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
{
  "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"encounterRole\": \"240b26f9-dd88-4172-823d-4a8bfeb7841f\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var raw = JSON.stringify({"encounterRole":"240b26f9-dd88-4172-823d-4a8bfeb7841f"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Updates an encounter provider subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if encounter provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[provider](#providers)* | `Provider UUID` | UUID of a provider currently registered in OpenMRS
    *[encounterRole](#encounter-role)* | `Encounter_Role UUID` | UUID of encounter role. This is the role provider will participate during this encounter 


## Delete encounter provider subresource

> Delete encounter provider subresource

```shell
DELETE /encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=FEAED37621B56D3A7C0361AD9858D314");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounter/d3360c01-9813-4ff8-bd81-909af6612632/encounterprovider/7146fea4-af02-4452-b4ed-240e71da7224?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or Voided a target encounter provider subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = 'true'. Purging will attempt to remove the encounter provider type from the system irreversibly. Encounter provider types that have been used (i.e., are referenced from existing data) cannot be purged.

