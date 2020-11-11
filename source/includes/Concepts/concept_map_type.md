# Concept Map Type

## Overview

* Concept mappings are generally used to map between a local concept and an external concept, most often a reference (standard) terminology but sometimes concepts from other systems with which you need to Inter operate (i.e., transform data moving between systems).
* Mappings are useful when you need to receive or send information to external systems, letting you define how your system's concepts relate to external concepts such as standardized medical vocabularies (e.g., ICD, LOINC, SNOMED). 
  
* For example, add a mapping to a concept in the MCL dictionary. You can save the concept now and create some answers.

* Repeat the steps and create the concepts PLANNING PREGNANCY and CURRENTLY PREGNANT of Class Finding and Datatype Boolean. The last possible answer will be the OTHER of Class Misc and Datatype N/A. After creating three new concepts, you can edit ANTENATAL VISIT REASON and add them as answers.

## Available operations. 

1. [List concept mapping types](#list-concept-map-types)
2. [Create a concept mapping type](#create-a-concept-map-type)
3. [Update a concept mapping typee](#update-a-concept-map-type)
4. [Delete a concept mapping type](#delete-a-concept-map-type)


## List concept map types

## List all non-retired concept map types.

> List all non-retired concept map types

```shell
  GET /conceptmaptype?q=associated
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype?q=associated&limit=1")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype?q=associated&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response
{
    "results": [
        {
            "uuid": "55e02065-7d8c-11e1-909d-c80aa9edcf4e",
            "display": "Associated finding",
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/conceptmaptype/55e02065-7d8c-11e1-909d-c80aa9edcf4e"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "/openmrs/ws/rest/v1/conceptmaptype?q=associated&limit=1&startIndex=1"
        }
    ]
}
```

* Quickly filter concept map types with a given search query. Returns a `404 Not Found` status if concept map type not exists. 
    If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `String` | Full or partial name search term. Search is case insensitive.


## List concept map type by UUID.

> List concept map type by UUID

```shell
  GET /conceptmaptype/:target_concept_map_type_uuid
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype/55e02065-7d8c-11e1-909d-c80aa9edcf4e")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype/55e02065-7d8c-11e1-909d-c80aa9edcf4e", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a concept map type by its UUID. Returns a `404 Not Found` status if concept map type not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a concept map type

> Create a concept map type

```shell
POST /conceptmaptype
{
	"name": "SAME-AS",
	"description": "used to map concepts which are Identical",
	"isHidden": false
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n\t\"name\": \"SAME-AS\",\r\n\t\"description\":\"used to map concepts which are Identical\",\r\n\t\"isHidden\": false\r\n}\r\n{\r\n\t\"name\": \"SAME-AS\",\r\n\t\"description\":\"used to map concepts which are Identical\"\r\n\t\"isHidden\": false\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1//conceptmaptype")
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

var raw = "{\n	\"name\": \"SAME-AS\",\n	\"description\":\"used to map concepts which are Identical\",\n	\"isHidden\": false\n}\n{\n	\"name\": \"SAME-AS\",\n	\"description\":\"used to map concepts which are Identical\"\n	\"isHidden\": false\n}\n";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1//conceptmaptype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a concept map type, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.
* A `400 Bad request` status is returned if the name is already being used by some concept map type. 

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept mapping type (Required)
    *description* | `String` | A brief description of the concept mapping type
    *isHidden* | `Boolean` | State to record concept map is hidden or not
    
## Update a concept map type

> Update a concept map type

```shell
POST /conceptmaptype/:target_concept_map_type_uuid
{
  "name": "SAME-AS",
  "description": "dummy update",
  "isHidden": true
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n\t\"name\": \"SAME-AS\",\r\n\t\"description\": \"dummy update\",\r\n\t\"isHidden\": false\r\n}\r\n{\r\n\t\"name\": \"SAME-AS\",\r\n\t\"description\":\"used to map concepts which are Identical\"\r\n\t\"isHidden\": false\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1//conceptmaptype/35543629-7d8c-11e1-909d-c80aa9edcf4e")
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

var raw = "{\n	\"name\": \"SAME-AS\",\n	\"description\": \"dummy update\",\n	\"isHidden\": false\n}\n{\n	\"name\": \"SAME-AS\",\n	\"description\":\"used to map concepts which are Identical\"\n	\"isHidden\": false\n}\n";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1//conceptmaptype/35543629-7d8c-11e1-909d-c80aa9edcf4e", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target concept map type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if concept map not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept mapping type 
    *description* | `String` |  A brief description of the concept mapping type
    *isHidden* | `Boolean` | State to record concept map is hidden or not
    
    
### Delete a concept map type

> Delete a concept map type

```shell
DELETE /conceptmaptype/:target_concept_map_type_uuid?purge=true
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype/55e02065-7d8c-11e1-909d-c80aa9edcf4e?purge=true")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype/55e02065-7d8c-11e1-909d-c80aa9edcf4e?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target concept map type by its UUID. Returns a `404 Not Found` status if concept map not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
* A `500 Internal Server Error `status is returned if the concept map is currently in use.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

