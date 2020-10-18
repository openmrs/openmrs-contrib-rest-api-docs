# Privilege

## Overview

A **Privilege** is an authorization to perform a particular action in the system. The list of available privileges are defined by the core system and by add-on modules (for example, **Delete Patients** and **Manage Encounter Types**), but you need to configure which roles have which privileges while you are configuring your system.

## Available operations.

1. [List privilege](#list-privileges)
2. [Create a privilege](#create-a-privilege)
3. [Update a privilege](#update-a-privilege)
4. [Delete a privilege](#delete-a-privilege)


### List privilege

```shell
    GET /privilege?v=full&limit=1
```

```response

{
    "results": [
         {
            "uuid": "24635eec-dd5a-11e6-9d9c-0242ac150002",
            "display": "Add Concept Proposals",
            "name": "Add Concept Proposals",
            "description": "Able to add concept proposals to the system",
            "retired": false,
            "auditInfo": {
                "creator": null,
                "dateCreated": null,
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrshttp://demo.openmrs.org/openmrshttp://demo.openmrs.org/openmrs/ws/rest/v1/privilege/24635eec-dd5a-11e6-9d9c-0242ac150002"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/privilege?v=full&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/privilege?v=full&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Fetch all privileges that match any specified parameters otherwise fetch all privileges. Returns a `200 OK` status with the privilege response. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    

* #### Get privilege by UUID

```shell
    GET /privilege/:target_privilege_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/privilege/fd40ed09-b499-405a-8b98-8154a6465e1a")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/privilege/fd40ed09-b499-405a-8b98-8154a6465e1a", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a privilege by its UUID. Returns a `404 Not Found` status if the privilege not exists. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    

### Create a privilege

```shell
POST /privilege
{
    "name": "Delete Patients",
    "description": "A privilege or permission to delete patients"
}
```

* To create a privilege, you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the privilege(Required)
    *description* | `String` | Description of the privilege(Required)

    

### Update a privilege

```shell
POST /privilege/:target_privilege_uuid
{
    "description": "A user who can delete all the encounter types"
}
```

* Update a privilege with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status, if the privilege does not exists. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned. Attempting to update a privilege's name will fail with the error code `400 Bad Request`.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *description* | `String` | Description of the privilege (Required)

    
### Delete a privilege

```console
   DELETE /privilege/:target_privilege_uuid?purge=true
```

* Delete a privilege by its UUID. Returns a `404 Not Found` status if the privilege not exists. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | `true` to delete the privilege from the system; if `false`, the request will have no effect
