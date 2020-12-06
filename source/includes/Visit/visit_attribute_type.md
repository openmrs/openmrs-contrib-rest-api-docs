# Visits Attribute Type

## Visits Attribute Type Overview

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types. 

* For example, you might create attributes for "Followup Visit," or "Distance Patient Traveled."
 

## Available operations for Visits Attribute Type 

1. [List visits attribute types](#list-visits-attribute-types)
2. [Create a visit attribute type](#create-a-visit-attribute-type)
3. [Update a visit attribute type](#update-a-visit-attribute-type)
4. [Delete a visit attribute type](#delete-a-visit-attribute-type)

## List visits attribute types

> List visits attribute types

```shell
GET /visitattributetype?q=Patient&v=full 
```  

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visitattributetype?q=Patient&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visitattributetype?q=Patient&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response
{
    "results": [
        {
            "uuid": "19a9de73-4d0f-48e4-be7b-b35fe0f8586d",
            "display": "Patient condition",
            "name": "Patient condition",
            "description": "This attribute type will record the health conditon of the patient",
            "minOccurs": 0,
            "maxOccurs": 1,
            "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
            "datatypeConfig": "default",
            "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
            "handlerConfig": null,
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
                    "display": "admin",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
                            "resourceAlias": "user"
                        }
                    ]
                },
                "dateCreated": "2020-10-31T19:25:30.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visitattributetype/19a9de73-4d0f-48e4-be7b-b35fe0f8586d",
                    "resourceAlias": "visitattributetype"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```

* Quickly filter visit attribute types with a given search query. Returns a `404 Not Found` status if the visit attribute type not exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Visit attribute type.

## List visit attribute type by UUID

> List visit attribute type by UUID

```shell
GET /visitattributetype/:target_visit_attribute_type_uuid
```  

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visitattributetype/19a9de73-4d0f-48e4-be7b-b35fe0f8586d")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visitattributetype/19a9de73-4d0f-48e4-be7b-b35fe0f8586d", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a visit attribute type by its UUID. Returns a `404 Not Found` status if the visit attribute type not exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.
    
   
## Create a visit attribute type

> Create a visit attribute type

```shell
POST /visitattributetype
{
  "name": "Patient condition",
  "description": "This attribute type will record the health conditon of the patient",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.FreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 1,
  "datatypeConfig": "default"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Patient condition\",\r\n  \"description\": \"This attribute type will record the health conditon of the patient\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.FreeTextDatatype\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 1,\r\n  \"datatypeConfig\": \"default\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/visitattributetype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=A7DBC9603F0BAF39988C59B870111270")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=A7DBC9603F0BAF39988C59B870111270");

var raw = JSON.stringify({"name":"Patient condition","description":"This attribute type will record the health conditon of the patient","datatypeClassname":"org.openmrs.customdatatype.datatype.FreeTextDatatype","minOccurs":0,"maxOccurs":1,"datatypeConfig":"default"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/visitattributetype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* To Create a visit attribute type, you need to specify below attributes in the request body. If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource.OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single visit. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single visit (e.g., use 1 to prevent an attribute from being added to a visit multiple times)
    *preferredHandlerClassname* | `Handler` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise the framework will choose the best handler for the chosen DataType).To find which handlers to use for the Custom DataType, please refer here   
    *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
    *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting
   

## Update a visit attribute type

> Update a visit attribute type

```shell
POST /visitattributetype/:target_visit_attribute_type_uuid
{
  "name": "Patient condition modified",
  "description": "This attribute type will keep a record the health conditon of the patient",
  "minOccurs": 0,
  "maxOccurs": 2
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Patient condition modified\",\r\n  \"description\": \"This attribute type will keep a record the health conditon of the patient\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 2\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visitattributetype/44bacae8-9563-40da-869d-35fcdd652a21")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var raw = JSON.stringify({"name":"Patient condition modified","description":"This attribute type will keep a record the health conditon of the patient","minOccurs":0,"maxOccurs":2});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visitattributetype/44bacae8-9563-40da-869d-35fcdd652a21", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target visit attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if the visit attribute not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit attribute type 
    *description* | `String` | Description 
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource.OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly 
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single visit. Use `0` or `1` as the default value 
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single visit (e.g., use 1 to prevent an attribute from being added to a visit multiple times)
    *preferredHandlerClassname* | `Handler` |  Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise the framework will choose the best handler for the chosen DataType ).To find which handlers to use for the Custom DataType, please refer here   
    *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
    *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting
    
## Delete a visit attribute type

> Delete a visit attribute type

```shell
DELETE /visitattributetype/:target_visit_attribute_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visitattributetype/44bacae8-9563-40da-869d-35fcdd652a21?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visitattributetype/44bacae8-9563-40da-869d-35fcdd652a21?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target visit attribute type by its UUID. Returns a `404 Not Found` status if the visit attribute type not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.


