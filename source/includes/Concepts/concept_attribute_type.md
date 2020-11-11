# Concept Attribute Type

## Concept Attribute Type Overview

* If you wish to record extra information about concept, you can create Concept Attributes and assign them to Concept Attribute Types. 

## Available operations for Concept Attribute Type. 

1. [List concept_attribute types](#list-concept-attribute-types)
2. [Create a concept_attribute_type](#create-a-concept-attribute-type)
3. [Update a concept_attribute type](#update-a-concept-attribute-type)
4. [Delete a concept_attribute type](#delete-a-concept-attribute-type)


## List concept attribute types

> List all non-retired concept attribute types

```shell
GET /conceptattributetype?q=time&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype?q=time&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=66002746B1A29A6E9CA461CD6309BCC2")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=66002746B1A29A6E9CA461CD6309BCC2");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype?q=time&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "ecc8e1af-3465-4840-85b8-ec5a2298bdcf",
            "display": "Time Span",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype/ecc8e1af-3465-4840-85b8-ec5a2298bdcf"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype?q=time&limit=1&startIndex=1"
        }
    ]
}

```

* Quickly filter concept attribute types with a given search query. Returns a `404 Not Found` status if concept  attribute type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `String` | Full or partial display name of concept source


## List concept attribute type by UUID.

> List concept attribute type by UUID

```shell
GET /conceptattributetype/:target_concept_attribute_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype?ecc8e1af-3465-4840-85b8-ec5a2298bdcf")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=66002746B1A29A6E9CA461CD6309BCC2")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=66002746B1A29A6E9CA461CD6309BCC2");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype?ecc8e1af-3465-4840-85b8-ec5a2298bdcf", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```	

* Retrieve a concept attribute type by its UUID. Returns a `404 Not Found` status if concept attribute type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a concept attribute type

> Create a concept attribute type

```shell
POST /conceptattributetype
{
  "name": "Time Span",
  "description": "This attribute type will record the time span for the concept",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 1,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": null
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Time Span\",\r\n  \"description\": \"This attribute type will record the time span for the concept\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.LongFreeTextDatatype\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 1,\r\n  \"datatypeConfig\": \"default\",\r\n  \"preferredHandlerClassname\": \"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler\",\r\n  \"handlerConfig\": null\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=7F21B551667D3B99C226980B29262DAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=7F21B551667D3B99C226980B29262DAF");

var raw = JSON.stringify({"name":"Time Span","description":"This attribute type will record the time span for the concept","datatypeClassname":"org.openmrs.customdatatype.datatype.LongFreeTextDatatype","minOccurs":0,"maxOccurs":1,"datatypeConfig":"default","preferredHandlerClassname":"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler","handlerConfig":null});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a concept attribute type, you need to specify below attributes in the request body. If you are not logged in to perform this action,a `401 Unauthorized` status returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*name* | `String` | Name of the concept attribute type (Required)
*description* | `String` | Description (Required)
*datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
*minOccurs* | `Number` | Minimum number of times this value can be specified for a single concept. Use `0` or `1` as the default value (Required)
*maxOccurs* | `Number` | Maximum number of times this value can be specified for a single concept (e.g., use 1 to prevent an attribute from being added to a concept multiple times)
*preferredHandlerClassname* | `Handler` | Specifies the Java class to be used when handling this concept attribute type. The java class must implement [`CustomDataTypeHandler`(https://docs.openmrs.org/doc/org/openmrs/customdatatype/CustomDatatypeHandler.html). If not specified, the system will try to choose the best handler for the chosen datatype
*datatypeConfig* | `String` | Provides ability to define custom data types configuration for OpenMRS
*handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list, and this configuration would tell the handler the possible choices in the list for this specific attribute type

## Update a concept attribute type

> Update a concept attribute type

```shell
POST /conceptattributetype/:target_concept_attribute_type_uuid
{
  "name": "Time Span",
  "description": "Dummy description update",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 1,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": null
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Time Span\",\r\n  \"description\": \"Dummy description update\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.LongFreeTextDatatype\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 1,\r\n  \"datatypeConfig\": \"default\",\r\n  \"preferredHandlerClassname\": \"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler\",\r\n  \"handlerConfig\": null\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype/b5d56fd4-9add-4c00-a227-eb69d70669dd")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=7F21B551667D3B99C226980B29262DAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=7F21B551667D3B99C226980B29262DAF");

var raw = JSON.stringify({"name":"Time Span","description":"Dummy description update","datatypeClassname":"org.openmrs.customdatatype.datatype.LongFreeTextDatatype","minOccurs":0,"maxOccurs":1,"datatypeConfig":"default","preferredHandlerClassname":"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler","handlerConfig":null});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype/b5d56fd4-9add-4c00-a227-eb69d70669dd", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```		

*  Update a target concept attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if concept attribute not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes


Parameter | Type | Description
--- | --- | ---
*name* | `String` | Name of the concept attribute type
*description* | `String` | Description 
*datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly
*minOccurs* | `Number` | Minimum number of times this value can be specified for a single concept. Use `0` or `1` as the default value
*maxOccurs* | `Number` | Maximum number of times this value can be specified for a single concept (e.g., use 1 to prevent an attribute from being added to a concept multiple times)
*preferredHandlerClassname* | `Handler` | Specifies the Java class to be used when handling this concept attribute type. The java class must implement [`CustomDataTypeHandler`(https://docs.openmrs.org/doc/org/openmrs/customdatatype/CustomDatatypeHandler.html). If not specified, the system will try to choose the best handler for the chosen datatype
*datatypeConfig* | `String` | Provides ability to define custom data types configuration for OpenMRS
*handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list, and this configuration would tell the handler the possible choices in the list for this specific attribute type

## Delete a concept attribute type

> Delete a concept attribute type

```shell
DELETE /conceptattributetype/:target_concept_attribute_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype/ecc8e1af-3465-4840-85b8-ec5a2298bdcf?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=66002746B1A29A6E9CA461CD6309BCC2")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=66002746B1A29A6E9CA461CD6309BCC2");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptattributetype/ecc8e1af-3465-4840-85b8-ec5a2298bdcf?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or retire a target concept attribute type by its UUID. Returns `404 Not Found` status if concept attribute does not exist. If not authenticated or user does not have sufficient privilege, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = "true"

