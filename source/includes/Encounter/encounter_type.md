# Encounter Type

## Encounter Type Overview

* Encounters represent an interaction between the patient and the healthcare system. Since there are a wide variety of ways in which these interactions may occur, OpenMRS allows you to categorize them by defining different types of encounter. For example, "Adult Primary Care Initial Visit" and "In-Between Visit Documentation" could be different types of encounters.

* You could define encounter type for locations such as Pharmacy, Lab, Consultation room, or for actions such as admission or discharge.

## Available operations for Encounter Type 

1. [List encounter types](#list-encounter-types)
2. [Create an encounter type](#create-an-encounter-type)
3. [Update an encounter type](#update-an-encounter-type)
4. [Delete an encounter type](#delete-an-encounter-type)


## List encounter types

> List encounter types

```shell
GET /encountertype?q=Admission
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype?q=Admission&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();


```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype?q=Admission&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "e22e39fd-7db2-45e7-80f1-60fa0d5a4378",
            "display": "Admission",
            "name": "Admission",
            "description": "Indicates that the patient has been admitted for inpatient care, and is not expected to leave the hospital unless discharged.",
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                    "display": "daemon",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/user/A4F30A1B-5EB9-11DF-A648-37A07F9C90FB"
                        }
                    ]
                },
                "dateCreated": "2013-08-01T18:27:27.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/e22e39fd-7db2-45e7-80f1-60fa0d5a4378"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

* Quickly filter encounter types with given query parameters. Returns a `404 Not Found` status if encounter types not exist. If the user not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter encounter type by its name

    
## Get encounter type by UUID.

> Get encounter type by UUID

```shell
GET /encountertype/:target_encounter_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/e22e39fd-7db2-45e7-80f1-60fa0d5a4378")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/e22e39fd-7db2-45e7-80f1-60fa0d5a4378", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an encounter type by its UUID. Returns a `404 Not Found` status if encounter type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an encounter type

> Create an encounter type

```shell
POST /encountertype
{
    "name": "Discharge",
    "description": "Attach encounters related to hospital dischargers"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Discharge\",\r\n    \"description\": \"Attach encounters related to hospital dischargers\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var raw = JSON.stringify({"name":"Discharge","description":"Attach encounters related to hospital dischargers"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* To create an encounter type, you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
* If the encounter name is already is in use then a `400 Bad Request` status is returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter type (Required)
    *description* | `String` | Description for the encounter type (Required)
   

## Update an encounter type

> Update an encounter type

```shell
POST /encountertype/:target_encounter_type_uuid
{
    "description": "Encounters related to discharge from hospital"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"description\": \"Encounters related to discharge from hospital\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/181820aa-88c9-479b-9077-af92f5364329")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var raw = JSON.stringify({"description":"Encounters related to discharge from hospital"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/181820aa-88c9-479b-9077-af92f5364329", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


*  Update a target encounter type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if encounter type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter type
    *description* | `String` | Description for the encounter type
    

    
## Delete an encounter type

> Delete an encounter type

```shell
DELETE /encountertype/:target_encounter_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/181820aa-88c9-479b-9077-af92f5364329?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encountertype/181820aa-88c9-479b-9077-af92f5364329?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));


```

* Delete or retire a target encounter type by its UUID. Returns a `404 Not Found` status if encounter type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

