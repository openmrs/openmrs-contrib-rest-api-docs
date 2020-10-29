# Concept Class

## Overview

* The concept's class provides a useful way to narrow down the scope of the information that the concept is intended to capture.  
* In this way, the class is helpful for data extraction.  This classification details how a concept will be represented 
(i.e. as a question or an answer) when the information is stored.
* OpenMRS contains several default classes to use when defining concepts, but implementation sites may also create additional custom concept classes for use. 
* examples of some concept classes are `Procedure`: `describes a clinical procedure`, `diagnosis`:`conclusion drawn through findings` e.t.c

## Available operations. 

1. [List concept classes](#list-concept-classes)
2. [Create a concept class](#create-a-concept-class)
3. [Update a concept class](#update-a-concept-class)
4. [Delete a concept class](#delete-a-concept-class)


## List concept classes

## List all non-retired concept classes.

>List all non-retired concept classes

```shell
GET /conceptclass?limit=1
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass?limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=4C92FA7F3401680513E023F3832D82FF")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=4C92FA7F3401680513E023F3832D82FF");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass?limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "8d4907b2-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Test",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass?limit=1&startIndex=1"
        }
    ]
}
```

   * List all concept classes with a given search query. Returns a `404 Not Found` status if concept classes not exist. 
    If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

## List concept class type by UUID.

> List concept class type by UUID

```shell
GET /conceptclass/:target_concept_class_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8d4907b2-c2cc-11de-8d13-0010c6dffd0f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```



  * Retrieve a concept class by its UUID. Returns a `404 Not Found` status if concept class type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.

## Create a concept class

> Create a concept class 

```shell
POST /conceptclass
{
  "name": "Procedure",
  "description": "Describes a clinical procedure"
}
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n          \"name\": \"Procedure\",\r\n          \"description\": \"Describes a clinical procedure\"\r\n        }");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B")
  .build();
Response response = client.newCall(request).execute();

```
```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B");

var raw = JSON.stringify({"name":"Procedure","description":"Describes a clinical procedure"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* To Create a concept class, you need to specify below attributes in the request body. If you are not logged in to perform this action,a `401 Unauthorized` status returned.
* A `400 Bad Request` status is returned if the new concept class name is already used for some other concept class. type

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept class (Required)
    *description* | `String` | Description

    
## Update a concept class

> Update a concept class

```shell
POST /conceptclass/:target_concept_class_uuid
{
  "name": "Procedure",
  "description": "Updating the dummy description"
}
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8afb1247-9c8c-48c4-9253-946ffd44bc8a")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B");

var raw = JSON.stringify({"name":"Procedure","description":"Updating the dummy description"});

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8afb1247-9c8c-48c4-9253-946ffd44bc8a", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))


```

*  Update a target concept class with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if concept class not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept class (Required)
    *description* | `String` | Description

    

## Delete a concept class

> Delete a concept class 

```shell
DELETE /conceptclass/:target_concept_class_uuid?purge=true

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8afb1247-9c8c-48c4-9253-946ffd44bc8a?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=FD046011463ABEF58A36F3C87DADC88B");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptclass/8afb1247-9c8c-48c4-9253-946ffd44bc8a?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or Retire a target concept class by its UUID. Returns a `404 Not Found` status if concept class not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    