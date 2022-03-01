# System Setting

## System Setting Overview

* System Settings are used to store module and system-wide settings. They primarily consist of a property name and a value and a description explaining how this property is being used.

* System Settings are configuration variables that can be modified without restarting or recompiling the application. They're useful when module code needs to refer to a value that's unique to a particular installation, such as a concept ID number or a file path.

* some examples : 
     * system-wide setting: `Default Location` which specifies the name of the location to use as a system default. 
     * module-specific system setting: `Require Email as Username` is a system setting under the user module which accepts boolean type as a valid value. 


## Available operations for systemsetting type.

1. [List System Settings](#list-system-settings)
2. [Create a System Setting](#create-a-system-setting)
3. [Update a System Setting](#update-a-system-setting)
4. [Delete a System Setting](#delete-a-system-setting)

## List System Settings

> List system settings

```shell
GET /systemsetting?limit=1&v=full
```


```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting?limit=1&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/systemsetting?limit=1&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "7ada585f-e2cc-456f-8fb2-67af52389293",
            "property": "addresshierarchy.addressToEntryMapUpdaterLastStartTime",
            "value": null,
            "description": "The module uses this field to store when the AddressToEntryMapUpdater task was last started; DO NOT MODIFY",
            "display": "Addresshierarchy - Address To Entry Map Updater Last Start Time = null",
            "datatypeClassname": null,
            "datatypeConfig": null,
            "preferredHandlerClassname": null,
            "handlerConfig": null,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/systemsetting/7ada585f-e2cc-456f-8fb2-67af52389293"
                }
            ],
            "resourceVersion": "1.9"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/systemsetting?limit=1&v=full&startIndex=1"
        }
    ]
}

```




* Fetch all non-retired System Settings that match any specified parameters otherwise fetch all non-retired System Settings. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *limit* | `integer`| use this parameter to limit the number of results to be returned 
    *startIndex*| `integer` | the offset where to start the query
    *v* | `String` | the required representation to return (i.e., ref, default, full or custom )
    *q* | `String` | the search query


## Get a particular System Setting

> Get a particular system setting

```shell
GET /systemsetting/:target_systemsetting_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting/addresshierarchy.allowFreetext")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/systemsetting/addresshierarchy.allowFreetext", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a particular System Setting. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.
* Settings can be obtained by UUID or by name.


## Create a System Setting

> Create a system setting

```shell

POST /systemsetting
{
  "property": "property name",
  "description": "dummy description",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.FreeTextDatatype",
  "datatypeConfig": "default",
  "preferredHandlerClassname":"org.openmrs.web.attribute.handler.FreeTextTextareaHandler",
  "handlerConfig": null,
  "value": "dummy value"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"property\": \"property name\",\r\n  \"description\": \"dummy description\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.FreeTextDatatype\",\r\n  \"datatypeConfig\": \"default\",\r\n  \"preferredHandlerClassname\":\"org.openmrs.web.attribute.handler.FreeTextTextareaHandler\",\r\n  \"handlerConfig\": null,\r\n  \"value\": \"dummy value\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();

```
```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var raw = JSON.stringify({"property":"property name","description":"dummy description","datatypeClassname":"org.openmrs.customdatatype.datatype.FreeTextDatatype","datatypeConfig":"default","preferredHandlerClassname":"org.openmrs.web.attribute.handler.FreeTextTextareaHandler","handlerConfig":null,"value":"dummy value"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/systemsetting/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a System Setting, you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *property* | `String` | the property name for this System Setting, names can be up to 255 chars, must be unique, and follow a convention of module ID followed by category & name lower camelCase separated by periods for e.g., addresshierarchy.allowFreetext.
    *description* | `String` | a description for the usage of this property.
    *datatypeClassname* | `String` | Data type for this System Setting.OpenMRS provides Custom data type resource, which gives flexibility to select the data type accordingly.
    *datatypeConfig* | `String` | An optional identifier from the fulfiller e.g., lab
    *preferredHandlerClassname*  | `String` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise, the framework will choose the best handler for the chosen DataType).
    *handlerConfig*  | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting.
    *value* | `String` | the value assigned to this system setting. 
    
## Update a System Setting

> Updating system setting

```shell

POST /systemsetting/:target_systemsetting_uuid
{
  "property": "property name",
  "description": "dummy description",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.FreeTextDatatype",
  "datatypeConfig": "default",
  "preferredHandlerClassname":"org.openmrs.web.attribute.handler.FreeTextTextareaHandler",
  "handlerConfig": null,
  "value": "dummy value"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"property\": \"property name\",\r\n  \"description\": \"dummy description\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.FreeTextDatatype\",\r\n  \"datatypeConfig\": \"default\",\r\n  \"preferredHandlerClassname\":\"org.openmrs.web.attribute.handler.FreeTextTextareaHandler\",\r\n  \"handlerConfig\": null,\r\n  \"value\": \"dummy value\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting/443b909a-82d7-4842-bf6a-f4e773ddcad8")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var raw = JSON.stringify({"property":"property name","description":"dummy description","datatypeClassname":"org.openmrs.customdatatype.datatype.FreeTextDatatype","datatypeConfig":"default","preferredHandlerClassname":"org.openmrs.web.attribute.handler.FreeTextTextareaHandler","handlerConfig":null,"value":"dummy value"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/systemsetting/443b909a-82d7-4842-bf6a-f4e773ddcad8", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Update a System Setting with given UUID, this method only modifies properties in the request. If the user not logged in to perform this action, a `401 Unauthorized` status returned.
* in order to use the examples we should first create a custom system setting and then try and modify it since some of the system settings are read only and might return an error `400 bad request`. 

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *property* | `String` | the property name for this System Setting, names can be up to 255 chars, must be unique, and follow a convention of module ID followed by category & name lower camelCase separated by periods for e.g., addresshierarchy.allowFreetext.
    *description* | `String` | a description for the usage of this property.
    *datatypeClassname* | `String` | Data type for this System Setting.OpenMRS provides Custom data type resource, which gives flexibility to select the data type accordingly.
    *datatypeConfig* | `String` | An optional identifier from the fulfiller e.g., lab
    *preferredHandlerClassname*  | `String` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise, the framework will choose the best handler for the chosen DataType).
    *handlerConfig*  | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting.
    *value* | `String` | the value assigned to this system setting.


## Delete a System Setting

> Delete a system setting

```shell
DELETE /systemsetting/:target_systemsetting_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting/7ada585f-e2cc-456f-8fb2-67af52389293?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/systemsetting/7ada585f-e2cc-456f-8fb2-67af52389293?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or void a System Setting by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

