# OpenMRS REST API

* Welcome to the OpenMRS REST API documentation! OpenMRS is a software
platform and a reference application which enables the design of a customized
medical records system with no programming knowledge (although medical and
systems analysis knowledge is required).

* It is a common platform upon which medical informatics efforts in developing
countries can be built. The system is based on a conceptual database structure
which is not dependent on the actual types of medical information required to
be collected or on particular data collection forms and so can be customized
for different uses.

* This document provides High level documentation of OpenMRS APIs with code
samples which are in the dark area to the right. If you find anything missing
or incorrect please consider proposing revision on [GitHub](https://github.com/openmrs/openmrs-contrib-rest-api-docs).

This documentation serves as a reference to the bespoke [REST API](https://en.wikipedia.org/wiki/Representational_state_transfer) for [OpenMRS](https://openmrs.org/).

## Purpose

- The purpose of this documentation is to provide a brief and good taste and experience of the APIs that are used in OpenMRS community to the new developers so that they can onboard in the projects within the organization easily.

- The documentation also aims to assist the existing developers in getting to know the APIs' conceptual context and how they help the consumers during the interaction in the real world.

# Getting Started

* If you are new to OpenMRS checkout the [Getting Started as a Developer Guide](https://wiki.openmrs.org/display/docs/Getting+Started+as+a+Developer)
from OpenMRS.

* For getting a detailed technical API documentation for the REST Module, checkout this wiki [here](https://wiki.openmrs.org/display/docs/REST+Web+Services+API+For+Clients)

## Current version

* By default, all requests to `/openmrs/ws/rest` receive the v1 version of the REST API.

* The OpenMRS REST Web Services module includes dynamically generated documentation.
  For example, see the
  [swagger documentation](/openmrs/module/webservices/rest/apiDocs.htm) on the demo server (username **admin**, password **Admin123**).


## Schema

* All API access is over HTTPS, and can be accessed from `/openmrs/ws/rest/v1`. All data is sent and received as JSON.
* The Data-Model behind the OpenMRS RestAPI can be accessed [here](https://docs.openmrs.org/datamodel/) 


## Getting Started with examples

### 1. Instructions for all the examples


* Before executing the examples, make sure that resources corresponding to the UUID's used in the examples are present on the demo server or any server you are testing these examples onto. 



> Java Code Stubs 


```stubs


import okhttp3.MediaType;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.RequestBody;
import okhttp3.Response;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try {
	    	
	        // the examples go here
		
        } catch (IOException exception) {

            // handle exception here
        }
    }
}

```



### 2. Getting Started with Java Code samples

* Before executing the Java examples, get the okttp dependency jar and import it the project.

* These code stubs will be elided from all the java examples for clarity

* Before executing the examples, append the base server url before the examples for e.g.
  change
 `Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/role?limit=1&v=default")` as
 
 `Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default")
 ` or any other base server URL you are testing these examples onto.

### 3. Getting Started with JavaScript Code samples

* The easiest way to run these examples would be by using the browser console, after opening the base url you are testing the examples onto.

* Before executing the examples, append the base server url before the examples for e.g.
  change
 `fetch("/openmrs/ws/rest/v1/role?limit=1&v=default", requestOptions)` 
  as
 
 `fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default", requestOptions)` 
  or any other base server URL you are testing these examples onto.



# Terms

## Resources

> Querying a resource(`Role`) 

```shell
GET /role?v=default&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/role?limit=1&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/role?limit=1&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* OpenMRS objects (persons, patients, encounters, observations, etc.) are exposed by the REST Web Services modules as a REST resource, as documented here are referred to as **Resources**.

* Resources have a default representation, which returns key properties. Most resources can be fetched using a full representation (using the parameter `v=full`) that includes a more comprehensive list of properties.

### For Instance Querying a Resource


## Subresources

> Accessing a Subresource under parent URL

```shell
POST /openmrs/ws/rest/v1/person/:target_person_uuid/name
{
  "givenName": "John",
  "familyName": "Smith"
}
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"givenName\": \"John\",\r\n  \"familyName\": \"Smith\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/person/070f0120-0283-4858-885d-a20d967729cf/name")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=A1644AD703C71E603C4E87B79291D075")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=A1644AD703C71E603C4E87B79291D075");

var raw = JSON.stringify({"givenName":"John","familyName":"Smith"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/person/070f0120-0283-4858-885d-a20d967729cf/name", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Some resources are not defined or do not make sense apart from their parent object. We refer
  to these as subresources.These subresources can be accessed under the parent's URL.

* A subresource can have only one parent.If it seems like a resource has two or more parents, then it is most likely a top-level resource.

* For example, "encounters" should not be a subresource of "patient" and "location" resources (answering questions of "all encounters of a patient" and "all encounters at a location").Instead, these should be queries on the encounter resource:

* Examples of subresources are PersonNames, PersonAddresses, ConceptNames, etc.


## Resources with subtypes

* Some resources can have subtypes. For example, the Order resource contains DrugOrder and TestOrder subtypes.

* When creating a resource that has subtypes via a `POST`, you must specify which subtype of the resource you are creating, with a special t property of the resource.

### Usage Examples of Resources with SubTypes

> Usage Examples of Resources(`Order`) with SubTypes

```shell
POST /openmrs/ws/rest/v1/order
{
  "type":"testorder",
  "action": "new",
  "urgency": "ROUTINE",
  "dateActivated": "2018-10-16 12:08:43",
  "careSetting": "INPATIENT" ,
  "encounter": "69f83020-caf2-4c9e-bca7-89b8e62b52e1",
  "patient": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
  "concept": "5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
  "orderer": "f9badd80-ab76-11e2-9e96-0800200c9a66"
}
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"type\":\"testorder\",\r\n  \"action\": \"new\",\r\n  \"urgency\": \"ROUTINE\",\r\n  \"dateActivated\": \"2018-10-16 12:08:43\",\r\n  \"careSetting\": \"INPATIENT\" ,\r\n  \"encounter\": \"69f83020-caf2-4c9e-bca7-89b8e62b52e1\",\r\n  \"patient\": \"96be32d2-9367-4d1d-a285-79a5e5db12b8\",\r\n  \"concept\": \"5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\r\n  \"orderer\": \"f9badd80-ab76-11e2-9e96-0800200c9a66\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/order")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=A1644AD703C71E603C4E87B79291D075")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=A1644AD703C71E603C4E87B79291D075");

var raw = JSON.stringify({"type":"testorder","action":"new","urgency":"ROUTINE","dateActivated":"2018-10-16 12:08:43","careSetting":"INPATIENT","encounter":"69f83020-caf2-4c9e-bca7-89b8e62b52e1","patient":"96be32d2-9367-4d1d-a285-79a5e5db12b8","concept":"5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","orderer":"f9badd80-ab76-11e2-9e96-0800200c9a66"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/order", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

### Querying Resources with subtypes


> Querying Resources with subtypes (drug order)

```shell
GET  /openmrs/ws/rest/v1/order?type=drugorder&v=full
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/order?type=drugorder&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A1644AD703C71E603C4E87B79291D075")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=A1644AD703C71E603C4E87B79291D075");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/order?type=drugorder&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* If you `GET` a resource that has subtypes, each result will be one of those subtypes,
  which you can see by looking at the special property of each result.

* You may query for only a certain subtype of a resource by providing a t query parameter.


### Querying Resources with subtypes (drug order)
