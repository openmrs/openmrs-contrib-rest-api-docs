# Concept Data Type

## Concept Data Type Overview

* Concept Data type defines the structured format you desired the data to be represented.

### Current types are as follows:
    
### 1. Numeric 
Any data represented numerically, also allows you to classify critical values and units, e.g., age, height, and liters consumed per day.

### 2. Coded 
Allows answers to be only those provided, since value determined by term dictionary lookup (i.e., term identifier) e.g., blood type can only be `“A,” “B,” "AB," or “O.”`.
    
### 3. Text
Open-ended responses.
    
### 4. N/A 
The standard datatype for any non-query-like concepts (answers or things), e.g., symptoms, diagnoses, findings, anatomy, misc.

### 5. Document
Pointer to a binary or text-based document (e.g., clinical document, RTF, XML, EKG, image, etc.) stored in complex_obs table.
 
### 6. Date 
Structured day, month, and year.

### 7. Time 
Structured time response.

### 8. DateTime 
Structured response including both the date and the time

### 9. Boolean 
Checkbox response, e.g., yes or no queries

### 10. Rule
Value derived from other data
 
### 11. Structured Numeric
Complex numeric values possible (ie, <5, 1-10, etc.).

### 12. Complex
Complex value, analogous to HL7 Embedded Datatype.


## Available operations for Concept Data Type. 

1. [List concept_data types](#list-concept-data-types)
4. [Delete a concept_data type](#delete-a-concept_data-type)


## List concept data types

## List all non-retired concept data types.

> List all non-retired concept data types

```shell
GET /conceptdatatype"
```    

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype?limit=1")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype?limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success response

```response
{
    "results": [
        {
            "uuid": "8d4a4488-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Numeric",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype/8d4a4488-c2cc-11de-8d13-0010c6dffd0f"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype?limit=1&startIndex=1"
        }
    ]
}
```
*  Get concept data types. Returns a `404 Not Found` status if concept data type not exists. 
    If the user is not logged in to perform this action, a `401 Unauthorized` status returned. 

    
## Get concept data type by UUID.

> Get concept data type by UUID

```shell
GET /conceptdatatype/:target_concept_data_type_uuid
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype/8d4a4488-c2cc-11de-8d13-0010c6dffd0f")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=C40164E7FA407F9E872B0BBDBB4582B0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=C40164E7FA407F9E872B0BBDBB4582B0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype/8d4a4488-c2cc-11de-8d13-0010c6dffd0f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

 * Retrieve a concept data type by its UUID. Returns a `404 Not Found` status if concept data type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    
## Delete a concept data type

> Delete a concept data type

```shell
DELETE /conceptdatatype/:target_concept_data_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype/8d4a4488-c2cc-11de-8d13-0010c6dffd0f?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=C40164E7FA407F9E872B0BBDBB4582B0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=C40164E7FA407F9E872B0BBDBB4582B0");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/conceptdatatype/8d4a4488-c2cc-11de-8d13-0010c6dffd0f?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or retire a target concept data type by its UUID. Returns a `404 Not Found` 
  status if concept data not exists. If the user is not logged in to perform this action, 
  a `401 Unauthorized` status returned.
* A `400 Bad Request` status is returned when the resource dosent support deletion. 

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

