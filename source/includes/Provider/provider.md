# Providers 

## Provider Overview

* A Provider is a person who provides care or services to patients. A provider may be a clinician like a doctor or a nurse, 
a social worker, or a lab tech. Generally speaking, any healthcare worker that a patient can have an encounter with is a provider.

* Providers may have full records in OpenMRS as persons, or they may just be a simple name and ID number.
 
## Sub Resource types of Provider

## Provider Attribute.

* If you wish to record extra information about providers, you can create Provider Attributes.

* Provider attributes exist specifically to allow implementations to extend the data model.

## Available operations for Provider. 

1. [List providers](#list-providers)
2. [Create a provider](#create-a-provider)
3. [Update a provider](#update-a-provider)
4. [Delete a provider](#delete-a-provider)
5. [List provider attribute sub resource](#list-provider-attribute-sub-resources)
6. [Create provider attribute sub resource with properties](#create-provider-attribute-sub-resource-with-properties)
7. [Update provider attribute sub resource](#update-provider-attribute-sub-resource)
6. [Delete provider attribute sub resource](#delete-provider-attribute-sub-resource)


## List providers

```shell
GET /provider?q=clerk&v=default
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider?q=clerk&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=83604888EAFD9CEC35D0D67CB4C80D28")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=83604888EAFD9CEC35D0D67CB4C80D28");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider?q=clerk&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response
{
    "results": [
        {
            "uuid": "f36c6f95-f157-4803-ad99-eb0bf8d05454",
            "display": "clerk - John Smith",
            "person": {
                "uuid": "007037a0-0500-11e3-8ffd-0800200c9a66",
                "display": "John Smith",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/person/007037a0-0500-11e3-8ffd-0800200c9a66"
                    }
                ]
            },
            "identifier": "clerk",
            "attributes": [],
            "retired": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/provider/f36c6f95-f157-4803-ad99-eb0bf8d05454"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/provider/f36c6f95-f157-4803-ad99-eb0bf8d05454?v=full"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```



* Quickly filter providers with given query parameters. Returns a `404 Not Found` status if provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Get provider by name
    *includeAll* | `Boolean` | If true, returns also retired Providers
    

    
## Query provider by UUID.

* Retrieve a provider by its UUID. Returns a `404 Not Found` status if provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
```shell
GET /provider/:target_provider_uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/f36c6f95-f157-4803-ad99-eb0bf8d05454")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=83604888EAFD9CEC35D0D67CB4C80D28")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=83604888EAFD9CEC35D0D67CB4C80D28");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f36c6f95-f157-4803-ad99-eb0bf8d05454", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```
   
## Create a provider

* To Create a provider, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[person](#person)* | `Person UUID` | Target person who will be a provider for OpenMRS (required)
    *identifier* | `String` | Value of the identifier.Identifier is used to virtually group providers in to groups (required)
    *[attributes](#list-provider-attribute-subresources)* | `Array[]: Attribute` |  List of provider attributes 
    *retired* | `Boolean` | Retired status for the provider.
    

```shell
POST /provider
{
  "person": "007037a0-0500-11e3-8ffd-0800200c9a66",
  "identifier": "doctor",
  "attributes": [
    {
      "attributeType": "12efe9f5-c460-40f1-b776-3a61669549e4",
      "value": "unknown location"
    }
  ],
  "retired": false
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"person\": \"007037a0-0500-11e3-8ffd-0800200c9a66\",\r\n  \"identifier\": \"doctor\",\r\n  \"attributes\": [\r\n    {\r\n      \"attributeType\": \"12efe9f5-c460-40f1-b776-3a61669549e4\",\r\n      \"value\": \"unknown\"\r\n    }\r\n  ],\r\n  \"retired\": false\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var raw = JSON.stringify({"person":"007037a0-0500-11e3-8ffd-0800200c9a66","identifier":"doctor","attributes":[{"attributeType":"12efe9f5-c460-40f1-b776-3a61669549e4","value":"unknown"}],"retired":false});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider", requestOptions)


```

## Update a provider

```shell
POST /provider/:target_provider_uuid
{
  "identifier": "Nurse"
}
```
    
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"identifier\": \"Nurse\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/7eec62f6-2b93-471e-a232-e0c9ed49f735")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var raw = JSON.stringify({"identifier":"Nurse"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/7eec62f6-2b93-471e-a232-e0c9ed49f735", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target provider with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if provider not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[person](#person)* | `Person UUID` | Target person who will be a provider for OpenMRS 
    *identifier* | `String` | Value of the identifier, identifier is used to virtually group providers in to groups 
    *[attributes](#list-provider-attribute-subresources)* | `Array[]: Attribute` |  List of provider attributes 
    *retired* | `Boolean` | Retired status for the provider.
    
## Delete a provider

```shell
DELETE /provider/:target_provider_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/7eec62f6-2b93-471e-a232-e0c9ed49f735?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/7eec62f6-2b93-471e-a232-e0c9ed49f735?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or retire a target provider by its UUID. Returns a `404 Not Found` status if provider not exists. If the user is logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’



## List provider attribute subresources

* Retrieve all **provider attribute** subresources of a **provider** resource by target_provider_uuid. Returns a `404 Not Found` status if provider attribute not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

## List provider attribute subresources by it's UUID and parent provider UUID.
   

```shell
GET /provider/:target_provider_uuid/attribute 
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```response

{
    "results": [
        {
            "display": "Provider Location: Unknown location",
            "uuid": "85db9ede-8866-41fe-bd01-62ccf9530516",
            "attributeType": {
                "uuid": "cff22d83-27e6-4195-8398-229853c1283f",
                "display": "Provider Location",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/providerattributetype/cff22d83-27e6-4195-8398-229853c1283f"
                    }
                ]
            },
            "value": "Unknown location",
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516?v=full"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```


 
* Retrieve a **provider attribute** subresources of a **provider** resource. Returns a `404 Not Found` status if the provider attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
```shell
GET /provider/:target_provider_uuid/attribute/:target_provider_attribute_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

## Create a provider attribute sub resource with properties

```shell
POST provider/:target_provider_uuid/attribute 
{
  "attributeType": "cff22d83-27e6-4195-8398-229853c1283f",
  "value": "Unknown location"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"attributeType\": \"cff22d83-27e6-4195-8398-229853c1283f\",\r\n  \"value\": \"Unknown location\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var raw = JSON.stringify({"attributeType":"cff22d83-27e6-4195-8398-229853c1283f","value":"Unknown location"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute", requestOptions)
  .then(response => response.text())


```


* To Create an attribute subresource for a specific provider resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[attributeType](#provider-attribute-type)* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type (required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (required)



## Update provider attribute subresource

```shell
POST provider/:target_provider_uuid/attribute/:target_provider_attribute_uuid
{
    "value": "Inpatient Ward"
}
```

```java

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var raw = JSON.stringify({"value":"Unknown location"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var raw = JSON.stringify({"value":"Unknown location"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Updates a provider attribute subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if the provider attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[attributeType](#provider-attribute-type)* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute



## Delete provider attribute subresource

* Delete or Retire a target provider attribute subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
 If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’. Purging will attempt to remove the provider attribute type from the system irreversibly. Provider attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

```shell
DELETE /provider/:target_provider_uuid/attribute/:target_provider_attribute_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=269840E88294F9C726CE86E71A579DE3");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66/attribute/85db9ede-8866-41fe-bd01-62ccf9530516", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```
