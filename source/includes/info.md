# OpenMRS REST API

> Getting started with examples. 

```java

//before executing the examples, get the okttp dependency jar and import it the project.
//these code stubs will be elided from all the examples for clarity

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

            //handle exception here
        }
    }
}

```
Welcome to the OpenMRS REST API documentation! OpenMRS is a software
platform and a reference application which enables the design of a customized
medical records system with no programming knowledge (although medical and
systems analysis knowledge is required).

It is a common platform upon which medical informatics efforts in developing
countries can be built. The system is based on a conceptual database structure
which is not dependent on the actual types of medical information required to
be collected or on particular data collection forms and so can be customized
for different uses.

This document provides High level documentation of OpenMRS APIs with code
samples which are in the dark area to the right. If you find anything missing
or incorrect please consider proposing revision on [GitHub](https://github.com/openmrs/openmrs-contrib-rest-api-docs).

This documentation serves as a reference to the bespoke [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
API for [OpenMRS](https://openmrs.org/).

# Getting Started

If you are new to OpenMRS checkout the [Getting Started as a Developer Guide](https://wiki.openmrs.org/display/docs/Getting+Started+as+a+Developer)
from OpenMRS

# Current version

- By default, all requests to `/openmrs/ws/rest` receive the v1 version of the REST API.

- The OpenMRS REST Web Services module includes dynamically generated documentation.
  For example, see the
  [swagger documentation](https://demo.openmrs.org/openmrs/module/webservices/rest/apiDocs.htm) on the demo server (username **admin**, password **Admin123**).

# Purpose

- The purpose of this documentation is to provide a brief and good taste and experience of the APIs that are used in OpenMRS community to the new developers so that they can onboard in the projects within the organization easily.

- The documentation also aims to assist the existing developers in getting to know the APIs' conceptual context and how they help the consumers during the interaction in the real world.

# Schema


>Fetching concepts

```shell
curl -X GET "https://demo.openmrs.org/openmrs/ws/rest/v1/concept"
connection: keep-alive
content-length: 9731
content-type: application/json;charset=UTF-8
date: Wed, 20 Nov 2019 14:13:54 GMT
etag: "04c83ff0cf2cc35cf05a2075ad117df83"
server: nginx/1.10.3 (Ubuntu)
strict-transport-security: max-age=15768000
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/concept")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```

All API access is over HTTPS, and can be accessed from `https://demo.openmrs.org/openmrs/ws/rest/v1`. All data is sent and received as JSON.


# Resources

- OpenMRS objects (persons, patients, encounters, observations, etc.) are exposed by the REST Web Services
  modules as a REST resource, as documented here.

- Resources have a default representation, which returns key properties. Most resources can be fetched using a
  full representation (using the parameter `v=full`) that includes a more comprehensive list of properties.

# Subresources

- Some resources are not defined or do not make sense apart from their parent object. We refer
  to these as subresources.

- Examples of subresources are PersonNames, PersonAddresses, ConceptNames, etc.

- You can act on subresources under the parent's URL

### Examples

>Adding a person's name

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
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"givenName\": \"John\",\r\n  \"familyName\": \"Smith\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/person/070f0120-0283-4858-885d-a20d967729cf/name
")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```

#### Adding a person name.

>Editing a person's name

```shell
POST /openmrs/ws/rest/v1/person/:target_person_uuid/name/:target_name_uuid
{
  "givenName": "Johnny"
}
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"givenName\": \"Johnny\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/person/070f0120-0283-4858-885d-a20d967729cf/name/c280a829-7a86-47a5-b876-df8f53e89dac
")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```

#### Editing a person's name.

- A subresource can have only one parent.

- If it seems like a resource has two or more parents, then it is most likely a top-level resource.

- For example, "encounters" should not be a subresource of "patient" and "location" resources (answering questions of "all encounters of a patient" and "all encounters at a location").

#### Instead, these should be queries on the encounter resource:


###Get an encounter list for a specific patient.
>Get an encounter list for a specific patient

```shell
 GET /encounter?patient=:target_patient_uuid
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/encounter?patient=7379bf1c-b64f-4958-b27f-2a769d8d291c")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```


###Get an encounter list for a specific location.
>Get an encounter list for a specific location

```shell
 GET /encounter?location=:target_location_uuid
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/encounter?location=aff27d58-a15c-49a6-9beb-d30dcfc0c66e")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```


# Resources with subtypes

- Some resources can have subtypes. For example, the Order resource contains DrugOrder and TestOrder subtypes

- When creating a resource that has subtypes via a `POST`, you must specify which subtype of the resource you are creating,
  with a special t property of the resource.

### Examples

>POST examples on order resource

```shell
POST /openmrs/ws/rest/v1/order
{
  "type":"testorder",
  "encounter": "69f83020-caf2-4c9e-bca7-89b8e62b52e1",
  "action": "new",
  "urgency": "ROUTINE",
  "dateActivated": "2018-10-16 12:08:43"
}
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"type\":\"testorder\",\r\n  \"encounter\": \"69f83020-caf2-4c9e-bca7-89b8e62b52e1\",\r\n  \"action\": \"new\",\r\n  \"urgency\": \"ROUTINE\",\r\n  \"dateActivated\": \"2018-10-16 12:08:43\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/order")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```

- If you GET a resource that has subtypes, each result will be one of those subtypes,
  which you can see by looking at the special property of each result.

- You may query for only a certain subtype of a resource by providing a t query parameter.


###Get encounter orders of drug order subtype.
>Get encounter orders of drug order subtype

```shell
GET  /openmrs/ws/rest/v1/order?type=drugorder&v=full'
```
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/order?type=drugorder")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=6D8DA35A3C57ECF332AFACC843609A23")
  .build();
Response response = client.newCall(request).execute();
```
