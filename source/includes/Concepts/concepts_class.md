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


```shell

    GET /conceptclass/:target_concept_class_uuid
```

## List concept class type by UUID.


  * Retrieve a concept class by its UUID. Returns a `404 Not Found` status if concept class type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.

### Create a concept class

```console
        POST /conceptclass
        {
          "name": "Procedure",
          "description": "Describes a clinical procedure"
        }
```
* To Create a concept class, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept class (Required)
    *description* | `String` | Description

    
### Update a concept class

```console
        POST /conceptclass
        {
          "name": "Procedure",
          "description": "Describes a clinical procedure"
        }
```
*  Update a target concept class with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept class not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept class (Required)
    *description* | `String` | Description

    

### Delete a concept class

```console
        DELETE /conceptclass/:target_concept_class_uuid?purge=true
```

* Delete or Retire a target concept class by its UUID. Returns a `404 Not Found` status if concept class not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    