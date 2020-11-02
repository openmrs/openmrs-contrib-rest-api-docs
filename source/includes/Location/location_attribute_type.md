# Location Attribute Type

## Location Attribute Overview

* If you wish to record extra information about locations, you can create Location Attributes and assign them to Location Types. 

## Available operations for Location Attribute 

1. [List location attribute types](#list-location-attribute-types)
2. [Create a location attribute type](#create-a-location-attribute-type)
3. [Update a location attribute type](#update-a-location-attribute-type)
4. [Delete a location attribute type](#delete-a-location-attribute-type)


### List location attribute types

### List all non-retired location attribute types.

```shell
GET /locationattributetype?q=humidity
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype?q=humidity&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype?q=humidity&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));


```

```response

{
    "results": [
        {
            "uuid": "e2844ee5-bfdd-4d07-bfc4-2afaf6bfe60c",
            "display": "humidity",
            "name": "humidity",
            "description": "This attribute type will record the humidity of the location",
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
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002"
                        }
                    ]
                },
                "dateCreated": "2020-11-02T20:08:50.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype/e2844ee5-bfdd-4d07-bfc4-2afaf6bfe60c"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```

* Quickly filter location attribute types with a given search query. Returns a `404 Not Found` status if the location attribute type not exists.If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Location attribute type.


### List location attribute type by UUID.

```console
GET /locationattributetype/:target_location_attribute_type_uuid
```
    Retrieve a location attribute type by its UUID. Returns a `404 Not Found` status if the location attribute type not exists. If the 
    user not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a location attribute type

```shell
POST /locationattributetype
{
  "name": "humidity",
  "description": "This attribute type will record the humidity of the location",
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
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"humidity\",\r\n  \"description\": \"This attribute type will record the humidity of the location\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.LongFreeTextDatatype\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 1,\r\n  \"datatypeConfig\": \"default\",\r\n  \"preferredHandlerClassname\": \"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler\",\r\n  \"handlerConfig\": null\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var raw = JSON.stringify({"name":"humidity","description":"This attribute type will record the humidity of the location","datatypeClassname":"org.openmrs.customdatatype.datatype.LongFreeTextDatatype","minOccurs":0,"maxOccurs":1,"datatypeConfig":"default","preferredHandlerClassname":"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler","handlerConfig":null});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};


```


* To Create a location attribute type, you need to specify below attributes in the request body. If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the location attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single location. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single location (e.g., use 1 to prevent an attribute from being added to a location multiple times)
    *preferredHandlerClassname* | `Handler` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise the framework will choose the best handler for the chosen DataType,). To find which handlers to use for the Custom DataType, please refer here   
    *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
    *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting

## Update a location attribute type

```shell
POST /locationattributetype/:target_location_attribute_type_uuid
{
  "minOccurs": 0,
  "maxOccurs": 2
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 2\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype/e2844ee5-bfdd-4d07-bfc4-2afaf6bfe60c")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var raw = JSON.stringify({"minOccurs":0,"maxOccurs":2});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype/e2844ee5-bfdd-4d07-bfc4-2afaf6bfe60c", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Update a target location attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if the location attribute not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

      Parameter | Type | Description
      --- | --- | ---
      *name* | `String` | Name of the location attribute type 
      *description* | `String` | Description
      *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
      *minOccurs* | `Number` | Minimum number of times this value can be specified for a single location. Use `0` or `1` as the default value
      *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single location (e.g., use 1 to prevent an attribute from being added to a location multiple times)
      *preferredHandlerClassname* | `Handler` |  Handler subresource for the Custom Data Type used. Can optionally define a specific handler class want to use (otherwise the framework will choose the best handler for the chosen DataType). To find which handlers to use for the Custom DataType, please refer here   
      *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
      *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting



## Delete a location attribute type

```shell
DELETE /locationattributetype/:target_location_attribute_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype/e2844ee5-bfdd-4d07-bfc4-2afaf6bfe60c?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationattributetype/e2844ee5-bfdd-4d07-bfc4-2afaf6bfe60c?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target location attribute type by its UUID. Returns a `404 Not Found` status if the location attribute type not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’. Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

