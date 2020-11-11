# Provider Attribute Type

## Provider Attribute Overview

* If you wish to record extra information about providers, you can create Provider Attributes and assign them to Provider Types as a subresource.

## Available operations for Provider Attribute type.

1. [List provider attribute types](#list-provider-attribute-types)
2. [Create a provider attribute type](#create-a-provider-attribute-type)
3. [Update a provider attribute type](#update-a-provider-attribute-type)
4. [Delete a provider attribute type](#delete-a-provider-attribute-type)


## List provider attribute types

> List provider attribute types

```shell
GET /providerattributetype?q=Location&v=full
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/providerattributetype?q=Location&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/providerattributetype?q=Location&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "02b23eb5-d3d1-416d-b5c7-565acb6bc0cb",
            "display": "Provider Location",
            "name": "Provider Location",
            "description": "This attribute type will record the loication of the provider",
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
                "dateCreated": "2020-11-05T20:31:46.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```

* Quickly filter provider attribute types with a given search query. Returns a `404 Not Found` status if the provider attribute type not exists.
* If the user is not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of provider attribute type.


## List provider attribute type by UUID


> List provider attribute type by UUID

```shell
GET /providerattributetype/:target_provider_attribute_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Retrieve a provider attribute type by its UUID. Returns a `404 Not Found` status if the provider attribute type not exists. 
* If the user is not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.


## Create a provider attribute type

> Create a provider attribute type

```shell
POST /providerattributetype
{
  "name": "Provider Location",
  "description": "This attribute type will record the location of the provider",
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
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Provider Location\",\r\n  \"description\": \"This attribute type will record the location of the provider\",\r\n  \"datatypeClassname\": \"org.openmrs.customdatatype.datatype.FreeTextDatatype\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 1,\r\n  \"datatypeConfig\": \"default\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/providerattributetype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var raw = JSON.stringify({"name":"Provider Location","description":"This attribute type will record the location of the provider","datatypeClassname":"org.openmrs.customdatatype.datatype.FreeTextDatatype","minOccurs":0,"maxOccurs":1,"datatypeConfig":"default"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/providerattributetype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

* To Create a provider attribute type, you need to specify below attributes in the request body. If user not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the provider attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single provider. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single provider (e.g., use 1 to prevent an attribute from being added to a provider multiple times)
    *preferredHandlerClassname* | `Handler` | Specifies the Java class to be used when handling this provider attribute type. The java class must implement [`CustomDataTypeHandler`](https://docs.openmrs.org/doc/org/openmrs/customdatatype/CustomDatatypeHandler.html). If not specified, the system will try to choose the best handler for the chosen datatype.
    *datatypeConfig* | `String` | Provides ability to define custom data types configuration for OpenMRS
    *handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list, and this configuration would tell the handler the possible choices in the list for this specific attribute type


## Update a provider attribute type

> Update a provider attribute type

```shell
POST /providerattributetype/:target_provider_attribute_type_uuid
{
  "name": "Provider Location Attribute",
  "minOccurs": 0,
  "maxOccurs": 2
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Provider Location Attribute\",\r\n  \"minOccurs\": 0,\r\n  \"maxOccurs\": 2\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5");

var raw = JSON.stringify({"name":"Provider Location Attribute","minOccurs":0,"maxOccurs":2});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


*  Update a target provider attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`status if the provider attribute not exists. 
* If the user is not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the provider attribute type 
    *description* | `String` | Description 
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single provider. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single provider (e.g., use 1 to prevent an attribute from being added to a provider multiple times)
    *preferredHandlerClassname* | `Handler` | Specifies the Java class to be used when handling this provider attribute type. The java class must implement [`CustomDataTypeHandler`](https://docs.openmrs.org/doc/org/openmrs/customdatatype/CustomDatatypeHandler.html). If not specified, the system will try to choose the best handler for the chosen datatype.
    *datatypeConfig* | `String` | Provides ability to define custom data types configuration for OpenMRS
    *handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list, and this configuration would tell the handler the possible choices in the list for this specific attribute type


## Delete a provider attribute type

> Delete a provider attribute type

```shell
DELETE /providerattributetype/:target_provider_attribute_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=02524DC1695063DAFFC0E2B0FA3087A5");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/providerattributetype/02b23eb5-d3d1-416d-b5c7-565acb6bc0cb?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a provider attribute type by its UUID. Returns a `404 Not Found` status if the provider attribute type not exists. If the user is not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

