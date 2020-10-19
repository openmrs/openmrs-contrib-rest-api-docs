# Role

## Role Overview

A **Role** represents a group of privileges in the system. Roles may inherit privileges from other roles, and users may have one or more roles.

## Available operations for Role.

1. [List roles](#list-roles)
2. [Create a role](#create-a-role)
3. [Update a role](#update-a-role)
4. [Delete a role](#delete-a-role)


## List roles

```shell
GET /role?v=default&limit=1
```
> Success Response

```response

{
    "results": [
        {
            "uuid": "774b2af3-6437-4e5a-a310-547554c7c65c",
            "display": "Anonymous",
            "name": "Anonymous",
            "description": "Privileges for non-authenticated users.",
            "retired": false,
            "privileges": [],
            "inheritedRoles": [],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c?v=full"
                }
            ],
            "resourceVersion": "1.8"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default&startIndex=1"
        }
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role?limit=1&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Fetch all the roles that match any specified parameters otherwise fetch all roles. Returns a `200 OK` status with the role response. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


* ## Get a role by UUID.

```shell
GET /role/:target_role_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1A5193DBE052C38DC303BAD947A05A83");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/role/774b2af3-6437-4e5a-a310-547554c7c65c", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*Retrieve a role by its UUID. Returns a `404 Not Found` status if the role does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a role

```shell
POST /role
{
  "name": "Clinician",
  "description": "A provider assisting the Lead Surgeon.",
  "privileges": [{
      "name": "Delete Patients",
      "description": "Able to delete patients"
  }]
}
```

* To create a role, you need to specify below attributes in the request body. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *privileges* | `Array[] : privileges` | An array of the privilege resource
    *inheritedRoles* | `Array[] : inheritedRoles` | An array of the inheritedRoles type

## Update a role

```console
POST /role
{
  "name": "Configures Forms",
  "description": "Manages forms and attaches them to the UI"
}
```

*  Update a role with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if the role does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *privileges* | `Array[] : privileges` | An array of the privilege resource
    *inheritedRoles* | `Array[] : inheritedRoles` | An array of the inheritedRoles type


## Delete a role

```console
DELETE /role/:target_role_uuid?purge=true
```

* Delete a role by its UUID. Returns a `404 Not Found` status if the role does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | must be `true` to delete the role from the system; if `false`, the request will have no effect

