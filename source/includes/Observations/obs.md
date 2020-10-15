# Observations 

## Observations Overview

* Observation is one piece of information recorded about a person at the moment in time.Every observation has a Concept as its question and depending on the datatype of the concept, it has a value that is a number, date, text, Concept, etc.

* Most of the information you store in OpenMRS is in the form of Observations, and most Observations happen in an Encounter. When you enter a form in OpenMRS, typically one Encounter is created with anywhere between tens or hundreds of Observations.

* Note that individual Observation is valid only at one moment in time, and it does not carry forward. You may query the system for the last observation for pregnancy status, but this does not tell you whether or not the patient is pregnant at any point after the moment of that observation.

* Examples of observations include Serum Creatinine of 0.9mg/dL or a Review of the cardiopulmonary system is normal.
 
## Available operations for Observations. 

1. [List observations](#list-observations)
2. [Create an observation](#create-an-observation)
3. [Update an observation](#update-an-observation)
4. [Delete an observation](#delete-an-observation)


## List all observations.

```shell
GET /obs?patient=070f0120-0283-4858-885d-a20d967729cf&limit=1"
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/obs?patient=070f0120-0283-4858-885d-a20d967729cf&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FE2FBD1F287477C74C655E0D467BA389")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=FE2FBD1F287477C74C655E0D467BA389");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/obs?patient=070f0120-0283-4858-885d-a20d967729cf&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


> Success Response

```response

{
    "results": [
        {
            "uuid": "99a0c42b-d50e-4ae3-b826-d1959c737e74",
            "display": "Visit Diagnoses: Primary, Confirmed diagnosis, Disease of bone and joint",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/obs/99a0c42b-d50e-4ae3-b826-d1959c737e74"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/obs?patient=070f0120-0283-4858-885d-a20d967729cf&limit=2&startIndex=2"
        }
    ]
}

```
    
* Quickly filter observations with given query parameters. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *[patient](#patients)* | `target_patient_uuid` | patient resource UUID
    *[concept](#concepts)* | `target_concept_uuid`| concept resource UUID (we can use this parameter only if patient UUID is specified for the query)

    
### Query observations by UUID.

```shell
GET /obs/:target_observation_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/obs/94616eb5-6a87-4b83-b1e2-2083b3f7a36b")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FE2FBD1F287477C74C655E0D467BA389")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=FE2FBD1F287477C74C655E0D467BA389");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/obs/94616eb5-6a87-4b83-b1e2-2083b3f7a36b", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an observation by its UUID.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.
    
   
## Create an observation

```shell
POST /obs 
{
  "person": "070f0120-0283-4858-885d-a20d967729cf",
  "concept": "5089AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
  "obsDatetime": "2019-11-14T07:37:31.000+0000",
  "value": 70
}
```
```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=56AEC369713B93BCB5B9BC7B34AA6E5F");

var raw = JSON.stringify({"person":"070f0120-0283-4858-885d-a20d967729cf","concept":"5089AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","obsDatetime":"2019-11-14T07:37:31.000+0000","value":70});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/obs", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"person\": \"070f0120-0283-4858-885d-a20d967729cf\",\r\n  \"concept\": \"5089AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\r\n  \"obsDatetime\": \"2019-11-14T07:37:31.000+0000\",\r\n  \"value\": 70\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/obs")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=56AEC369713B93BCB5B9BC7B34AA6E5F")
  .build();
Response response = client.newCall(request).execute();

```


* To Create an observation, you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[person](#person)* | `Person UUID` | The Person this Obs is acting on (Required)
    *obsDateTime* | `String` | The type of `obsDateTime` is an "ISO 8601 timestamp" (Required)
    *[concept](#concepts)* | `concept UUID` | the coded value/name given to an obs when it is made (Required)
    *[Location](#location)* | `location UUID` | the location this Obs took place (was taken).
    *order* | `String` | the order of an Obs.
    *[encounter](#encounters)* | `encounter UUID` | what obs are collected and grouped together into. An encounter is a visit.
    *accessionNumber* | `String` | An identifier used by the fulfiller (e.g., the lab) to identify the specimen or requisition used to produce this observation.
    *groupMembers* | `Array[]: Obs` |  a list of Obs grouped under this Obs
    *comment* | `String` | An option free text comment about the observation.
    *value* | `String` | The value for the observation (e.g., the answer to a question or the result of a lab test) (Required)
    *status* | `String` | `PRELIMINARY`, `FINAL`, `AMENDED`
    *[valueCodedName](#list-all-concept-names-for-a-concept)*|`Concept Name`| ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale
    *interpretation* | `String` | `NORMAL`, `ABNORMAL`, `CRITICALLY_ABNORMAL`, `NEGATIVE`, `POSITIVE`,`CRITICALLY_LOW`,  `LOW`, `HIGH`, `CRITICALLY_HIGH`, `VERY_SUSCEPTIBLE`, `SUSCEPTIBLE`, `INTERMEDIATE`, `RESISTANT`, `SIGNIFICANT_CHANGE_DOWN`, `SIGNIFICANT_CHANGE_UP`, `OFF_SCALE_LOW`, `OFF_SCALE_HIGH`
    *voided* | `Boolean` | true if the observation is voided
    
## Update an observation

```shell
POST /obs/:uuid_of_obs_to_be_updated
{
  "value": 71
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"value\": 71\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/obs/727124cd-191e-4073-a619-d3169c228374")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=56AEC369713B93BCB5B9BC7B34AA6E5F")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=56AEC369713B93BCB5B9BC7B34AA6E5F");

var raw = JSON.stringify({"value":71});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/obs/727124cd-191e-4073-a619-d3169c228374", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target obs, this method only modifies properties in the request. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.
    

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[person](#person)* | `Person UUID` | The Person this Obs is acting on (Required)
    *obsDateTime* | `String` | The type of `obsDateTime` is an "ISO 8601 timestamp" (Required)
    *[concept](#concepts)* | `concept UUID` | the coded value/name given to an obs when it is made (Required)
    *[Location](#location)* | `location UUID` | the location this Obs took place (was taken).
    *order* | `String` | the order of an Obs.
    *[encounter](#encounters)* | `encounter UUID` | what obs are collected and grouped together into. An encounter is a visit.
    *accessionNumber* | `String` | An identifier used by the fulfiller (e.g., the lab) to identify the specimen or requisition used to produce this observation.
    *groupMembers* | `Array[]: Obs` |  a list of Obs grouped under this Obs
    *comment* | `String` | An option free text comment about the observation.
    *value* | `String` | The value for the observation (e.g., the answer to a question or the result of a lab test) (Required)
    *status* | `String` | `PRELIMINARY`, `FINAL`, `AMENDED`
    *[valueCodedName](#list-all-concept-names-for-a-concept)*|`Concept Name`| ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale
    *interpretation* | `String` | `NORMAL`, `ABNORMAL`, `CRITICALLY_ABNORMAL`, `NEGATIVE`, `POSITIVE`,`CRITICALLY_LOW`,  `LOW`, `HIGH`, `CRITICALLY_HIGH`, `VERY_SUSCEPTIBLE`, `SUSCEPTIBLE`, `INTERMEDIATE`, `RESISTANT`, `SIGNIFICANT_CHANGE_DOWN`, `SIGNIFICANT_CHANGE_UP`, `OFF_SCALE_LOW`, `OFF_SCALE_HIGH`
    *voided* | `Boolean` | true if the observation is voided
    
        
## Delete an observation

```shell
DELETE /obs/:target_obs_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/obs/4b2412bd-b538-4038-81d4-d2af153082b6?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=4C54B3334747032502B326EB3362BA0D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=4C54B3334747032502B326EB3362BA0D");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/obs/4b2412bd-b538-4038-81d4-d2af153082b6?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or void a target observation. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

