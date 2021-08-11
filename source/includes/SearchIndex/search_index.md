# Search Index

## Available operations for Search Index

1. [Update Search Index](#update-search-index)

## Update Search Index

> Update Search Index

```shell
POST /searchindexupdate
{
    "resource": "patient",
    "subResource": "patientidentifier",
    "uuid": "fd07779c-b8f1-4b90-b41b-45cf9bc538f8",
    "async": false
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"resource\": \"patient\",\"subResource\": \"patientidentifier\",\"uuid\": \"fd07779c-b8f1-4b90-b41b-45cf9bc538f8\",\"async\": false}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/searchindexupdate")
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

var raw = JSON.stringify({"resource": "patient","subResource": "patientidentifier","uuid": "fd07779c-b8f1-4b90-b41b-45cf9bc538f8","async": false});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/searchindexupdate", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Executes rebuild of search index.

You can execute one of three operations:

- rebuild whole search index by only passing "async" attribute

- rebuild search index for resource by passing "resource" and optionally "subResource" attributes.

- rebuild search index for one object by passing "uuid" attribute.

### Attributes
    Parameter | Type | Description
    --- | --- | ---
    *resource* | `String` | Resource name of type that you want to regenerate index for
    *subResource* | `String` | Resource name of subtype that you want to regenerate index for
    *uuid* | `UUID` | UUID of object that you want to regenerate index for
    *async* | `Boolean` | Should rebuilding index be executed asynchronously
