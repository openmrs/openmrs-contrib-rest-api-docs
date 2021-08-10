# Locale and Theme Configuration

## Locale and Theme Configuration Overview

You can set default theme and default locale via REST API.

## Available operations for Locale and Theme Configuration

1. [Retrieve Configuration](#retrieve-configuration)
2. [Update Configuration](#update-configuration)

## Retrieve Configuration

> Retrieve Configuration

```shell
GET /localeandthemeconfiguration
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/localeandthemeconfiguration")
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

fetch("/openmrs/ws/rest/v1/localeandthemeconfiguration", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "defaultLocale": "en_GB",
    "defaultTheme": "green"
}
```

Retrieves current configuration.

## Update Configuration

> Update Configuration

```shell
POST /localeandthemeconfiguration
{
    "defaultLocale": "en_GB",
    "defaultTheme": "green"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"defaultLocale\": \"en_GB\",\"defaultTheme\": \"green\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/localeandthemeconfiguration")
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

var raw = JSON.stringify({"defaultLocale": "en_GB","defaultTheme": "green"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/localeandthemeconfiguration", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Updates current configuration with the following properties:

### Attributes
    Parameter | Type | Description
    --- | --- | ---
    *defaultLocale* | `String` | Default Locale for OpenMRS instance. Has to be a valid language code. For example: en, en_GB, es
    *defaultTheme* | `String` | Default Theme for OpenMRS instance. For example: "orange", "purple", "green", and "legacy"
