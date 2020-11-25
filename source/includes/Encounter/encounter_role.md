# Encounter Role

## Encounter Role Overview

* An Encounter role is specific to the [encounter](#encounters). While these could match up to existing organizational roles (e.g., "Nurse"), they don't have to (e.g., "Lead Surgeon").

## Available operation for Encounter Roles 

1. [List encounter roles](#list-encounter-roles)
2. [Create an encounter role](#create-a-encounter-role)
3. [Update an encounter role](#update-a-encounters-role)
4. [Delete an encounter role](#delete-a-encounters-role)


## List encounter roles

> List encounter roles

```shell
GET /encounterrole?q=Clinician&v=full
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounterrole?q=Clinician&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounterrole?q=Clinician&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "240b26f9-dd88-4172-823d-4a8bfeb7841f",
            "display": "Clinician",
            "name": "Clinician",
            "description": "Doctor or Nurse who is the primary provider for an encounter, and will sign the note",
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
                "dateCreated": "2013-08-02T05:20:48.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

* Quickly filter encounter roles with given query parameters. Returns a `404 Not Found` status if encounter roles not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter encounter role by its name

    
## Get encounter role by UUID.

> Get encounter role by UUID

```shell
GET /encounter/:target_encounter_role_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an encounter role by its UUID. Returns a `404 Not Found` status if encounter role not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an encounter role

> Create an encounter role

```shell
POST /encounterrole
{
    "name": "Clinician",
    "description": "A provider assisting the Lead Surgeon."
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Clinician\",\r\n    \"description\": \"A provider assisting the Lead Surgeon.\"\r\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounterrole")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var raw = JSON.stringify({"name":"Clinician","description":"A provider assisting the Lead Surgeon."});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounterrole", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create an encounter role, you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
* If the name is already in use then a `400 Bad Request ` status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter role (required)
    *description* | `String | Description for the encounter role (required)
   

## Update an encounter role

> Update an encounter role

```shell
POST /encounterrole/:target_encounter_role_uuid
{
    "description": "A surgeon who assisted the Lead Surgeon"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"description\": \"A surgeon who assisted the Lead Surgeon\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var raw = JSON.stringify({"description":"A surgeon who assisted the Lead Surgeon"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


*  Update a target encounter role with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if encounter role not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter role
    *description* | `String | Description for the encounter role
    

    
## Delete an encounter role

> Delete an encounter role

```shell
DELETE /encounterrole/:target_encounter_role_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=299EEB7913BE50BACA8D795EBE6D0094");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/encounterrole/240b26f9-dd88-4172-823d-4a8bfeb7841f?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Void a target encounter role by its UUID. Returns a `404 Not Found` status if encounter role not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

