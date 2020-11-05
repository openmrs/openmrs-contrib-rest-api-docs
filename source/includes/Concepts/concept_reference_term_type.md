# Concept Reference Term

## Overview

* Concept reference terms represent terms within external vocabularies (typically standardized terminologies like SNOMED, ICD, LOINC, etc.). OpenMRS concept can be mapped to these reference terms through [concept mappings](concept_mapping.md). 
  
* For example, the concept `left Lung` can be mapped to an external concept `lower lobe of Lung` using a concept mapping `BROADER-THAN`.

## Available operations. 
1.  [List concept reference terms](#list-concept-reference-terms)
2.  [Create a concept reference term](#create-a-concept-reference-term)
3.  [Update a concept reference term](#update-a-concept-reference-term)
4.  [Delete a concept reference term](#delete-a-concept-reference-term)

## List concept reference terms

> List all concepts reference terms

```shell
GET /conceptreferenceterm?codeOrName=274663001
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptreferenceterm?codeOrName=274663001")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=4F55735593751E224686B006CD388234")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=4F55735593751E224686B006CD388234");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptreferenceterm?codeOrName=274663001", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "c4091da9-3d7c-37c8-906d-51183e750629",
            "display": "SNOMED CT: 274663001",
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629"
                }
            ]
        }
    ]
}

```

* Quickly filter concept reference term with given query parameters. Returns a `404 Not Found` status if concept reference term type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *codeOrName* | `String` |  Represents a code or name from a standard medical code
    *source* | `String` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (i.e., LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc.), but the concept source can also be a custom (i.e., org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database

    
## Query concept reference term by UUID.

> Query concept reference term by UUID

```shell
GET /conceptreferenceterm/:target_concept_reference_term_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=4F55735593751E224686B006CD388234")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=4F55735593751E224686B006CD388234");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Retrieve a concept reference term by its UUID. Returns a `404 Not Found` status if concept reference term not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a concept reference term

> Create a concept reference term

```shell

POST /conceptreferenceterm
{
  "name": "Acute Pain",	
  "code": "274663001", 
  "description": "description for the concept reference term"	
  "conceptSource": "1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD",
  "version": "1.0.0"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Acute Pain\",\t\r\n  \"code\": \"274663001\", \r\n  \"description\": \"description for the concept reference term\",\t\r\n  \"conceptSource\": \"1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD\",\r\n  \"version\": \"1.0.0\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptreferenceterm")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=B369B31B00020CC1488C42325A76272B")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=B369B31B00020CC1488C42325A76272B");

var raw = JSON.stringify({"name":"Acute Pain","code":"274663001","description":"description for the concept reference term","conceptSource":"1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD","version":"1.0.0"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptreferenceterm", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* To Create an concept reference term, you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
* A `400 Bad Request` status is returned if the code used is already being used by some other concept reference term with the same concept source

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the concept reference term
    *description* | `String` | A brief description of the concept reference term
    *code* | `String` | Represents a name from a standard medical code (required)
    *conceptSource* | `target_concept_source_UUID` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (i.e., LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc.), but the concept source can also be a custom (i.e., org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept reference term type

    
### Update a concept reference term

> Update a concept reference term

```shell

POST /conceptreferenceterm/:target_concept_reference_term_type_uuid
{
  "name": "Acute Pain",	
  "code": "274663001", 
  "description": "Modified description for the concept reference term"	
  "conceptSource": "1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD",
  "version": "1.0.0"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Acute Pain\",\t\r\n  \"code\": \"274663001\", \r\n  \"description\": \"description for the concept reference term\",\t\r\n  \"conceptSource\": \"1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD\",\r\n  \"version\": \"1.0.0\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=B369B31B00020CC1488C42325A76272B")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=B369B31B00020CC1488C42325A76272B");

var raw = JSON.stringify({"name":"Acute Pain","code":"274663001","description":"description for the concept reference term","conceptSource":"1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD","version":"1.0.0"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target concept reference term with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if concept reference term not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the concept reference term
    *description* | `String` | A brief description of the concept reference term
    *code* | `String` | Represents a name from a standard medical code 
    *conceptSource* | `target_concept_source_UUID` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (i.e., LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc.), but the concept source can also be a custom (i.e., org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database 
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept reference term type

    
### Delete a concept reference term

> Delete a concept reference term

```shell
DELETE /conceptreferenceterm/:target_concept_reference_term_type_uuid?purge=true    
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=B369B31B00020CC1488C42325A76272B")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=B369B31B00020CC1488C42325A76272B");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/conceptreferenceterm/c4091da9-3d7c-37c8-906d-51183e750629?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or retire a target concept reference term by its UUID. Returns a `404 Not Found` status if concept reference term not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.
* A `500 Internal Server Error` status is returned if the concept reference term to be deleted is currently in use.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

