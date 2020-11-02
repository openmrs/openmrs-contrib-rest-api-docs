# Location Tag Type

## Location Tag Overview

* Tags are strings attached to an entity (like tagging of blog entries) to form a folksonomy and/or to categorize data. 

* Location Tags are being used to tag locations, which enables the system to act based on the presence of tags on specific locations. 

* You should not use locations to represent logical ideas like `All-District Hospitals`. They should be modeled using LocationTags.

* For example, location tags may be used to control which locations are included in a choice list or to define which locations included in a report.

## Available operations for Location Tag

1. [List location tags](#list-location-tags)
2. [Create a location tag](#create-a-location-tag)
3. [Update a location tag](#update-a-location-tag)
4. [Delete a location tag](#delete-a-location-tag)


## List location tags

```shell
GET /locationtag?q=visit&v=full
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag?q=visit&v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag?q=visit&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


> Success Response

```response

{
    "results": [
        {
            "uuid": "37dd4458-dc9e-4ae6-a1f1-789c1162d37b",
            "display": "Visit Location",
            "name": "Visit Location",
            "description": "Visits are only allowed to happen at locations tagged with this location tag or at locations that descend from a location tagged with this tag.",
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                    "display": "daemon",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/user/A4F30A1B-5EB9-11DF-A648-37A07F9C90FB"
                        }
                    ]
                },
                "dateCreated": "2013-08-01T23:45:29.000+0000",
                "changedBy": {
                    "uuid": "A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                    "display": "daemon",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/user/A4F30A1B-5EB9-11DF-A648-37A07F9C90FB"
                        }
                    ]
                },
                "dateChanged": "2017-01-18T08:54:00.000+0000"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/37dd4458-dc9e-4ae6-a1f1-789c1162d37b"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}

```

    Quickly filter location tags with a given search query. Returns a `404 Not Found` status if the location tag not exists.
    If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Location location tag type.


## List location tag by UUID.

```shell
GET /locationtag/:target_location_tag_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/37dd4458-dc9e-4ae6-a1f1-789c1162d37b")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/37dd4458-dc9e-4ae6-a1f1-789c1162d37b", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a location tag by its UUID. Returns a `404 Not Found` status if the location tag type not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a location tag

```shell
POST /locationtag
{
  "name": "Visit Location",
  "description": "Visits are only allowed to happen at locations tagged with this location tag.",
  "retired": false
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"name\": \"Visit Location\",\r\n  \"description\": \"Visits are only allowed to happen at locations tagged with this location tag.\",\r\n  \"retired\": false\r\n  }\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var raw = JSON.stringify({"name":"Visit Location","description":"Visits are only allowed to happen at locations tagged with this location tag.","retired":false});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a location tag, you need to specify below attributes in the request body. If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the location tag  (Required)
    *description* | `String` | Description (Required)
    *retired* | `Boolean` | Retired status of the location tag
    *retiredReason* | `String` | For location tags that are retired, this may contain an explanation of why the location tag was retired.


## Update a location tag

```shell
POST /locationtag/:target_location_tag_uuid
{
  "retired": true
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"retired\": true\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/8d4626ca-7abd-42ad-be48-56767bbcf272")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var raw = JSON.stringify({"retired":true});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/8d4626ca-7abd-42ad-be48-56767bbcf272", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


*  Update a target location tag with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if the location tag not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

      Parameter | Type | Description
      --- | --- | ---
      *name* | `String` | Name of the location tag type
      *description* | `String` | Description
      *retired* | `Boolean` | Retired status of the location tag
      *retiredReason* | `String` | For location tags that are retired, this may contain an explanation of why the location tag was retired.


## Delete a location tag

```shell
DELETE /locationtag/:target_location_tag_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/c0b3c7f7-6dec-4c6c-9363-813f755b96e5?purge =true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=177F9C2E5ED43272221D31E103D6B704");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/c0b3c7f7-6dec-4c6c-9363-813f755b96e5?purge =true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or Retire a target location tag type by its UUID. Returns a `404 Not Found` status if the location tag not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’. Purging will attempt to remove the tag from the system irreversibly. Location tags types that have been used (i.e., are referenced from existing data) cannot be purged.

