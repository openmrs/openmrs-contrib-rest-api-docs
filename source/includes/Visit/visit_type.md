# Visits Type

## Visits Type Overview

* A Visit Type is a name and description of a kind of visit. 

* Every visit has a type. You should create visit types that match how your health site classifies visits, such as "Outpatient," "Hospitalization," "Dental," "Patient Education," or "TB Clinic.".

* It is mandatory to set up at least one visit type.

* Visit types will be shown as dropdown options when creating or editing a patient in Registration. 

* Visit types can be added via the OpenMRS admin screen(Administration > Visits > Manage Visit Types) or via SQL scripts. 

## Available operations for Visits Type

1. [List visits types](#list-visits-types)
2. [Create a visit type](#create-a-visit-type)
3. [Update a visit type](#update-a-visit-type)
4. [Delete a visit type](#delete-a-visit-type)


## list visits types

> list visits types

```shell
GET /visittype?q=Facility&v=full
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visittype?q=Facility&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visittype?q=Facility&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

>Success Response

```response

{
    "results": [
        {
            "uuid": "7b0f5697-27e3-40c4-8bae-f4049abfb4ed",
            "display": "Facility Visit",
            "name": "Facility Visit",
            "description": "Patient visits the clinic/hospital (as opposed to a home visit, or telephone contact)",
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                    "display": "daemon",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/user/A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                            "resourceAlias": "user"
                        }
                    ]
                },
                "dateCreated": "2013-08-02T00:39:43.000+0000",
                "changedBy": {
                    "uuid": "A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                    "display": "daemon",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/user/A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                            "resourceAlias": "user"
                        }
                    ]
                },
                "dateChanged": "2017-01-18T08:53:57.000+0000"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visittype/7b0f5697-27e3-40c4-8bae-f4049abfb4ed",
                    "resourceAlias": "visittype"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```
    
* Quickly filter visit types with a given search query. Returns a `404 Not Found` status if visit type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Visit Type.

## List visit type by UUID.

> List visit type by UUID

```shell
GET /visittype/:target_visit_type_uuid
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visittype/7b0f5697-27e3-40c4-8bae-f4049abfb4ed")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visittype/7b0f5697-27e3-40c4-8bae-f4049abfb4ed", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a visit type by its UUID. Returns a `404 Not Found` status if visit type not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
   
## Create a visit type

> Create a visit type

```shell
POST /visittype
{
    "name": "Facility Visit",
    "description": "Patient visits the clinic/hospital (as opposed to a home visit, or telephone contact)"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Facility Visit\",\r\n    \"description\": \"Patient visits the clinic/hospital (as opposed to a home visit, or telephone contact)\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visittype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var raw = JSON.stringify({"name":"Facility Visit","description":"Patient visits the clinic/hospital (as opposed to a home visit, or telephone contact)"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visittype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a visit type, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit type (Required)
    *description* | `String` | Description of the visit type
   

## Update a visit type

> Update a visit type

```shell
POST /type/:target_visit_type_uuid
{
    "name": "Facility Visit",
    "description": "Modified description"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Facility Visit\",\r\n    \"description\": \"Modified description\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visittype/62e364c3-8eb0-46e9-b420-9463a4efdcc9")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var raw = JSON.stringify({"name":"Facility Visit","description":"Modified description"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visittype/62e364c3-8eb0-46e9-b420-9463a4efdcc9", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target visit type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if visit not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

        
### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit type
    *description* | `Patient UUID` | Visit type resource UUID
    
    
## Delete a visit type

> Delete a visit type

```shell
DELETE /visittype/:target_visit_type_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visittype/62e364c3-8eb0-46e9-b420-9463a4efdcc9?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();
```
```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visittype/62e364c3-8eb0-46e9-b420-9463a4efdcc9?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target visit type by its UUID. Returns a `404 Not Found` status if visit not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’


