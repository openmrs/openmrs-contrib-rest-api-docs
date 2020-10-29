# Person Attribute Type

## Person Attribute Type Overview

* Person attributes provide a mechanism for implementations to add custom attributes to their person records. A Person Attribute Type defines one of these custom attributes, including its data type and search behavior.

* For example, creating a Person Attribute Type for civil status (whether or not someone is single or married) would allow an implementation to record this information for each person in their system.

## Available operations.

1. [List person attribute types](#list-person-attribute-types)
2. [Create a person attribute type](#create-a-person-attribute-type)
3. [Update a person attribute type](#update-a-person-attribute-type)
4. [Delete a person attribute type](#delete-a-person-attribute-type)



## List all non-retired person attribute types.

> List all non-retired person attribute types

```shell
GET /personattributetype?q=race&v=default
```

> Success Response

```response

{
    "results": [
        {
            "uuid": "8d871386-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Race",
            "name": "Race",
            "description": "Group of persons related by common descent or heredity",
            "format": "java.lang.String",
            "foreignKey": 0,
            "sortWeight": 6.0,
            "searchable": false,
            "editPrivilege": null,
            "retired": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/8d871386-c2cc-11de-8d13-0010c6dffd0f"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/8d871386-c2cc-11de-8d13-0010c6dffd0f?v=full"
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
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype?q=race&v=default")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype?q=race&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Quickly filter person attribute types with a given search query. If the request is not authenticated or the authenticated user does not have appropriate permissions, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter person attributes by its name(partial search is not supported)


## Get person attribute type by UUID.

> Get person attribute type by UUID

```shell
GET /personattributetype/:target_person_attribute_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/8d871386-c2cc-11de-8d13-0010c6dffd0f")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/8d871386-c2cc-11de-8d13-0010c6dffd0f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a person attribute type by its UUID. Returns a `404 Not Found` status if the person attribute type does not exist. If the user not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a person attribute type

> Create a person attribute type

```shell
POST /personattributetype
{
    "name": "Edit Civil Status",
    "description": "Able to manage the civil status of persons",
    "format": "org.openmrs.Concept",
    "foreignKey": 1054,
    "searchable": false,
    "editPrivilege": "24635eec-dd5a-11e6-9d9c-0242ac150002"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Edit Civil Status\",\r\n    \"description\": \"Able to manage the civil status of persons\",\r\n    \"format\": \"org.openmrs.Concept\",\r\n    \"foreignKey\": 1054,\r\n    \"searchable\": false,\r\n    \"editPrivilege\": \"24635eec-dd5a-11e6-9d9c-0242ac150002\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=F8F836D691AB75C7845C6B658D0018E2")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=F8F836D691AB75C7845C6B658D0018E2");

var raw = JSON.stringify({"name":"Edit Civil Status","description":"Able to manage the civil status of persons","format":"org.openmrs.Concept","foreignKey":1054,"searchable":false,"editPrivilege":"24635eec-dd5a-11e6-9d9c-0242ac150002"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a person attribute type you need to specify below attributes in the request body. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the person attribute type (Required)
    *description* | `String` | Description (Required)
    *format* | `Java Class` | The Java class the PersonAttributeType  
    *foreignKey* | `Number` | The internal identifier (foreign key) to a Concept that defines the possible values for this attribute
    *sortWeight* | `Number` | The order this PersonAttributeType will appear in when searched
    *searchable* | `Boolean` | True if this person attributes should be used to find patients. The default value is false.
    *[editPrivilege](#privilege)* | `Privilege` | The privilege required to make changes to this type,we can pass in `UUID` of an existing privilege or pass in whole new privilege object.  


## Update a person attribute type

> Update a person attribute type

```shell
POST /personattributetype
{
    "name": "Manage Civil Status"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Manage Civil Status\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/aa7569c5-f81f-4e63-ab1f-810103f297ba")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=F8F836D691AB75C7845C6B658D0018E2")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=F8F836D691AB75C7845C6B658D0018E2");

var raw = JSON.stringify({"name":"Manage Civil Status"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/aa7569c5-f81f-4e63-ab1f-810103f297ba", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))


```


*  Update a target person attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if the person attribute does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the person attribute type (Required)
    *description* | `String` | Description (Required)
    *format* | `Java Class` | The Java class the PersonAttributeType  
    *foreignKey* | `Number` | The internal identifier (foreign key) to a Concept that defines the possible values for this attribute
    *sortWeight* | `Number` | The order this PersonAttributeType will appear in when searched
    *searchable* | `Boolean` | True if this person attributes should be used to find patients. The default value is false.
    *[editPrivilege](#privilege)* | `Privilege` | The privilege required to make changes to this type,we can pass in `UUID` of an existing privilege or pass in whole new privilege object.  


## Delete a person attribute type

> Delete a person attribute type

```shell
DELETE /personattributetype/:target_person_attribute_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/8d8718c2-c2cc-11de-8d13-0010c6dffd0f?purge=true")
  .method("DELETE", body)
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
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/personattributetype/8d8718c2-c2cc-11de-8d13-0010c6dffd0f?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a person attribute type by its UUID. Returns a `404 Not Found` status if the person attribute type does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

