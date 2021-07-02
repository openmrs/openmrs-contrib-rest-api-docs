# Visits Configuration

## Visits Configuration Overview

Visits introduce set of settings related to Visits Behavior. You can retrieve and update this configuration through REST API.

## Available operations for Visits Configuration

1. [Retrieve Configuration](#retrieve-configuration)
2. [Update Configuration](#update-configuration)

## Retrieve Configuration

> Retrieve Configuration

```shell
GET /visitsconfiguration
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visitsconfiguration")
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

fetch("/openmrs/ws/rest/v1/visitsconfiguration", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "visitEncounterHandler": "org.openmrs.api.handler.NoVisitAssignmentHandler",
    "enableVisits": true,
    "autoCloseVisitsTaskStarted": true,
    "visitTypesToAutoClose": [
        {
            "uuid": "48d69339-bb3a-489f-bf23-70e3da9cfc4d",
            "display": "Test",
            "name": "Test",
            "description": null,
            "retired": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "/ws/rest/v1/visittype/48d69339-bb3a-489f-bf23-70e3da9cfc4d",
                    "resourceAlias": "visittype"
                },
                {
                    "rel": "full",
                    "uri": "/ws/rest/v1/visittype/48d69339-bb3a-489f-bf23-70e3da9cfc4d?v=full",
                    "resourceAlias": "visittype"
                }
            ]
        }
    ]
}
```

Retrieves current configuration.

## Update Configuration

> Update Configuration

```shell
POST /visitsconfiguration
{
    "enableVisits": true,
    "visitEncounterHandler": "org.openmrs.api.handler.NoVisitAssignmentHandler",
    "autoCloseVisitsTaskStarted": true,
    "visitTypesToAutoClose": [
        {
            "uuid": "48d69339-bb3a-489f-bf23-70e3da9cfc4d"
        }
    ]
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"enableVisits\": true,\"visitEncounterHandler\":\"org.openmrs.api.handler.NoVisitAssignmentHandler\",\"autoCloseVisitsTaskStarted\": true,\"visitTypesToAutoClose\": [{\"uuid\": \"48d69339-bb3a-489f-bf23-70e3da9cfc4d\"}]}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visitsconfiguration")
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

var raw = JSON.stringify({"enableVisits": true,"visitEncounterHandler":"org.openmrs.api.handler.NoVisitAssignmentHandler","autoCloseVisitsTaskStarted": true,"visitTypesToAutoClose": [{"uuid": "48d69339-bb3a-489f-bf23-70e3da9cfc4d"}]});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visitsconfiguration", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Updates current configuration with the following properties:

### Attributes
    Parameter | Type | Description
    --- | --- | ---
    *enableVisits* | `Boolean` | Are visits enabled
    *visitEncounterHandler* | `String` | Class name of EncounterVisitHandler subclass
    *autoCloseVisitsTaskStarted* | `Boolean` | Should visits be automatically closed
    *[visitTypesToAutoClose](#visits-type)* | `Array[]: VisitType` | List of visit types to automatically close. Only UUID field, see an example.
