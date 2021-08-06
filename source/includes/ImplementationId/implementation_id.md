# Implementation Id Configuration

## Available operations for Implementation Id Configuration

1. [Retrieve Configuration](#retrieve-configuration)
2. [Update Configuration](#update-configuration)

## Retrieve Configuration

> Retrieve Configuration

```shell
GET /implementationid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/implementationid")
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

fetch("/openmrs/ws/rest/v1/implementationid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "name": "test",
    "description": "recovering teest",
    "implementationId": "test",
    "passphrase": "test"
}
```

Retrieves current configuration.

## Update Configuration

> Update Configuration

```shell
POST /implementationid
{
    "name": "test",
    "description": "test",
    "implementationId": "test",
    "passphrase": "test"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"test\",\"description\": \"test\",\"implementationId\": \"test\",\"passphrase\": \"test\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/implementationid")
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

var raw = JSON.stringify({"name": "test","description": "test","implementationId": "test","passphrase": "test"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/implementationid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Updates current configuration with the following properties:

### Attributes
    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | A descriptive name for this implementation (e.g. AMRS installation in Eldoret, Kenya)
    *description* | `String` | Text describing this implementation. (e.g. Source for the AMPATH program in Kenya. Created by Paul Biondich)
    *implementationId* | `String` | This is the unique id for this implementation. Used as the HL7_CODE. Must be limited to 20 characters and numbers. The characters "^" and "|" are not allowed.
    *passphrase* | `String` | This text is a long text string that is used to validate who uses your implementation id. Multiple installations of openmrs can use the same implmentation id, but they must all know the passphrase. (Note that if an implementation id is shared, it is assumed that those installations are the same implementation).
