# Field Type

## Field Type Overview

* The Field type defined the type of fields on a [form](#forms) resource. A [form](#forms) can have many 0 to n fields associated with it in a hierarchical manner. This Field type resource governs what data is collected from a [form](#forms).
* for e.g. such as concept, database element, set of concepts etc.

## Available operations for field Type 

1. [List field types](#list-field-types)
2. [Create an field type](#create-an-field-type)
3. [Update an field type](#update-an-field-type)
4. [Delete an field type](#delete-an-field-type)


## List field types

> List field types

```shell
GET /fieldtype?
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/fieldtype?v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/fieldtype?v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "8d5e7d7c-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Concept",
            "name": "Concept",
            "description": "",
            "isSet": false,
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
                    "display": "admin",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002"
                        }
                    ]
                },
                "dateCreated": "2005-02-22T00:00:00.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/fieldtype/8d5e7d7c-c2cc-11de-8d13-0010c6dffd0f"
                }
            ],
            "resourceVersion": "1.8"
        },
        {
            "uuid": "8d5e8196-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Database element",
            "name": "Database element",
            "description": "",
            "isSet": false,
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
                    "display": "admin",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002"
                        }
                    ]
                },
                "dateCreated": "2005-02-22T00:00:00.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/fieldtype/8d5e8196-c2cc-11de-8d13-0010c6dffd0f"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

* Quickly filter field types with given query parameters. Returns a `404 Not Found` status if field types not exist. If the user not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Description
    --- | ---
    *limit* | use this parameter to limit the number of results to be returned. 
    *startIndex* | the offset where to start the query.
    *v* | the required representation to return (i.e., ref, default, full or custom ).
    *q* | the search query based on the name of the field type.

    
## Get field type by UUID.

> Get field type by UUID

```shell
GET /fieldtype/:target_field_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/fieldtype/8d5e86fa-c2cc-11de-8d13-0010c6dffd0f")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/fieldtype/8d5e86fa-c2cc-11de-8d13-0010c6dffd0f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an field type by its UUID. Returns a `404 Not Found` status if field type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an field type

> Create an field type

```shell
POST /fieldtype
{
    "name": "Concept",
    "description": "fields storing info related to concepts",
    "isSet": true
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"Concept\",\"description\": \"fields storing info related to concepts\",\"isSet\": true}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/fieldtype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var raw = JSON.stringify({"name": "Concept","description": "fields storing info related to concepts","isSet": true});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/fieldtype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create an field type, you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
* A `400 Bad Request ` Status is returned if any duplicate name is used in the creation of new field Type.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the field type (required)
    *description* | `String` | Description for the field type (required)
    *isSet* | `Boolean` | Is field type a set
   

## Update an field type

> Update an field type

```shell
POST /fieldtype/:target_field_type_uuid
{
    "name": "Concept",
    "description": "fields storing info related to concepts",
    "isSet": true
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"Concept\",\"description\": \"fields storing info related to concepts\",\"isSet\": true}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/fieldtype/8d5e7d7c-c2cc-11de-8d13-0010c6dffd0f")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var raw = JSON.stringify({"name": "Concept","description": "fields storing info related to concepts","isSet": true});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/fieldtype/8d5e7d7c-c2cc-11de-8d13-0010c6dffd0f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


*  Update a target field type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if field type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the field type
    *description* | `String` | Description for the field type
    *isSet* | `Boolean` | Is field type a set
    

    
## Delete an field type

> Delete an field type

```shell
DELETE /fieldtype/:target_field_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/fieldtype/8d5e7d7c-c2cc-11de-8d13-0010c6dffd0f?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/fieldtype/8d5e7d7c-c2cc-11de-8d13-0010c6dffd0f?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or retire a target field type by its UUID. Returns a `404 Not Found` status if field type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

