# Concept Source

## Concept Source Overview

* Concepts are often managed within a dictionary (as a collection of concepts). While OpenMRS has, it's own dictionary of concepts, other dictionaries may exist in other systems or as standardized reference terminologies (like LOINC or ICD). The authorities who manage these other concept dictionaries represent "Concept Sources."
* For eg `PIH Malawi`:`Partners in Health Malawi concept dictionary`, `SNOMED CT`:`SNOMED Preferred mapping` etc.


## Available operations for Concept Source. 

1. [List concept_source types](#list-concept-source)
2. [Create a concept_source](#create-a-concept-source)
3. [Update a concept_source type](#update-a-concept-source)
4. [Delete a concept_source type](#delete-a-concept-source)


## List concept source

>List all non-retired concept source


```shell
GET /conceptsource?q=pih&limit=1
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource?q=pih&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource?q=pih&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response
{
    "results": [
        {
            "uuid": "fb9aaaf1-65e2-4c18-b53c-16b575f2f385",
            "display": "PIH",
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/conceptsource/fb9aaaf1-65e2-4c18-b53c-16b575f2f385"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "/openmrs/ws/rest/v1/conceptsource?q=pih&limit=1&startIndex=1"
        }
    ]
}

```
*   Quickly filter concept source types with a given search query. Returns a `404 Not Found` status if concept source type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `String` | Full or partial match to concept source name. Search is case-insensitive for eg. PIH

    
## Query concept source by UUID

> Query concept source by UUID

```shell
GET /conceptsource/:target_concept_source_type_uuid
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D")
  .build();
Response response = client.newCall(request).execute();

```
```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


 *  Retrieve a concept source type by its UUID. Returns a `404 Not Found` status if concept source type not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create a concept source

> Create a concept source

```shell
POST /conceptsource
{
  "name": "SNOMED CT",
  "description": "SNOMED Preferred mapping",
  "hl7Code": "SCT",
  "uniqueId":"2.16.840.1.113883.6.96"	
}
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"SNOMED CT\",\r\n  \"description\": \"SNOMED Preferred mapping\",\r\n  \"hl7Code\": \"SCT\",\r\n  \"uniqueId\":\"2.16.840.1.113883.6.96\"\t\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=3359211CFE448283F1CDCE925E43545E")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=3359211CFE448283F1CDCE925E43545E");

var raw = JSON.stringify({"name":"SNOMED CT","description":"SNOMED Preferred mapping","hl7Code":"SCT","uniqueId":"2.16.840.1.113883.6.96"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a concept source type you need to specify below attributes in the request body. If you are not logged in to perform this action,a `401 Unauthorized` status returned.
* A `500 Internal Server Error` status is returned if the new concept source class name, description or Hl7Code is already used for some other concept source class.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept source type (Required)
    *description* | `String` | Description for the concept source type resource (Required)
    *hl7Code* | `String` | A short code defined by governing bodies like HL7 (as in Vocabulary Table 0396). Alternatively, this could be the "Implementation Id" code used by another OpenMRS installation to define its concepts and forms
    *uniqueId* | `String` | A globally unique id to for the concept source
   
## Update a concept source

> Update a concept source

```shell
POST /conceptsource/:target_concept_source_type_uuid
{
 "name": "SNOMED CTS",
 "description": "SNOMED Preferred mapping",
 "hl7Code": "SCT"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n \"name\": \"SNOMED CTS\",\r\n \"description\": \"SNOMED Preferred mapping\",\r\n \"hl7Code\": \"SCT\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D");

var raw = JSON.stringify({"name":"SNOMED CTS","description":"SNOMED Preferred mapping","hl7Code":"SCT"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

``` 

*  Update a target concept source type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept source not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept source type
    *description* | `String` | Description for the concept source type resource
    *hl7Code* | `String` | The 5-20 character code defined for this source by governing bodies. Alternatively, this could be the "Implementation Id" code used by another OpenMRS installation to define its concepts and forms
    *uniqueId* | `String` | A globally unique id to for the concept source
    
    
## Delete a concept source

> Delete a concept source

```shell
DELETE /conceptsource/:target_concept_source_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/9ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=BB426C696078A92639710E2B54C97C4D");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/9ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

* Delete or Retire a target concept source type by its UUID. Returns a `404 Not Found` status if concept source not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
* If the target concept source is referenced somewhere else in the database a `500 Internal Server Error` status is returned.

  ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

