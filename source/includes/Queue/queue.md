# Queue

## Queue Overview

* A queue in OpenMRS represents a line of patients waiting for a particular service in a specific location. For example, queues might be used for services such as triage, clinical consultation, lab or pharmacy.

## Available operations for Queues

1. [List queues](#list-queues)
2. [Create queue](#create-queue)
3. [Update queue](#update-queue)
4. [Void queue](#void-queue)

## List queues

> List queues

```shell
GET /
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue)
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

fetch("/openmrs/ws/rest/v1/queue, requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response
{
    "results": [
        {
            "uuid": "4890b934-73c3-4c91-a93b-ce48f728b520",
            "display": "Clinical consultation",
            "name": "Clinical consultation",
            "description": "Clinical consultation",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/4890b934-73c3-4c91-a93b-ce48f728b520"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/4890b934-73c3-4c91-a93b-ce48f728b520?v=full"
                }
            ]
        },
        {
            "uuid": "ae0e1ad7-08ba-4a3d-aeed-a757591faf83",
            "display": "Triage service",
            "name": "Triage service",
            "description": "Triage service",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/ae0e1ad7-08ba-4a3d-aeed-a757591faf83"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/ae0e1ad7-08ba-4a3d-aeed-a757591faf83?v=full"
                }
            ]
        },
        {
            "uuid": "501b135b-1733-445e-9616-a4a05cee1bdd",
            "display": "Lab service",
            "name": "Lab service",
            "description": "Lab service",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/501b135b-1733-445e-9616-a4a05cee1bdd"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/501b135b-1733-445e-9616-a4a05cee1bdd?v=full"
                }
            ]
        }
    ]
}
```

- If user not logged in to perform this action, a `401 Unauthorized` status returned.

## List queue by UUID

> List queue by UUID

```shell
GET /queue/:target_queue_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/36475629-6652-44e9-a42b-c2b3b7438f72")
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
  method: "GET",
  headers: requestHeaders,
  redirect: "follow",
};

fetch(
  "/openmrs/ws/rest/v1/queue/36475629-6652-44e9-a42b-c2b3b7438f72",
  requestOptions
)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

- Retrieve a queue by its UUID. Returns a `404 Not Found` if queue to be retrieved not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.

## Create queue

> Create queue

```shell
POST /queue
{
  "name": "Triage queue",
  "description": "This triage queue description",
  "service": {
    "uuid": "d3db3805-2b90-4330-9064-eb6d42cbf582"
  },
  "location": {
    "uuid": "8d6c993e-c2cc-11de-8d13-0010c6dffd0f"
  }
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
 .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n  \"name\": \"Triage queue\",\n  \"description\": \"This triage queue description\",\n  \"service\": {\n    \"uuid\": \"d3db3805-2b90-4330-9064-eb6d42cbf582\"\n  },\n  \"location\": {\n    \"uuid\": \"8d6c993e-c2cc-11de-8d13-0010c6dffd0f\"\n  }\n}");
Request request = new Request.Builder()
 .url("/openmrs/ws/rest/v1/queue")
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

var raw = JSON.stringify({
  name: "Triage queue",
  description: "This triage queue description",
  service: {
    uuid: "d3db3805-2b90-4330-9064-eb6d42cbf582",
  },
  location: {
    uuid: "8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
  },
});

var requestOptions = {
  method: "POST",
  headers: requestHeaders,
  body: raw,
  redirect: "follow",
};

fetch("/openmrs/ws/rest/v1/queue", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

- To create a queue you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the queue
    *description* | `String` | Description of the queue
    *service* | `Concept_UUID` |Concept UUID describing this queue/service
    *[location](#location)* | `Location UUID` | Location resource UUID

## Update queue

> Update queue

```shell
POST /queue/:target_queue_uuid
{
  "name": "TRIAGE QUEUE (updated)",
  "description": "Queue for patients waiting for triage(updated)"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n  \"name\": \"TRIAGE QUEUE (updated)\",\n  \"description\": \"Queue for patients waiting for triage(updated)\"\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/c298d3e1-6def-422a-9d0a-e18906a4ae73")
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

var raw = JSON.stringify({
  name: "TRIAGE QUEUE (updated)",
  description: "Queue for patients waiting for triage(updated)",
});

var requestOptions = {
  method: "POST",
  headers: requestHeaders,
  body: raw,
  redirect: "follow",
};

fetch(
  "/openmrs/ws/rest/v1/queue/c298d3e1-6def-422a-9d0a-e18906a4ae73",
  requestOptions
)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

- Updates the queue record. Only modifies the properties specified in the request. Returns a 404 Not found status if the queue(to be updated) doesn't exist. If not authenticated, 401 Unauthorized status is returned.

### Attributes

| Parameter | Type         | Description                 |
| --------- | ------------ | --------------------------- |
| UUID      | `Queue UUID` | UUID of queue to be updated |

## Delete queue

> Delete the target queue

```shell
DELETE /queue/<UUID>?purge=false
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/c298d3e1-6def-422a-9d0a-e18906a4ae73?purge=false")
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
  method: "DELETE",
  headers: requestHeaders,
  redirect: "follow",
};

fetch(
  "/openmrs/ws/rest/v1/queue/c298d3e1-6def-422a-9d0a-e18906a4ae73?purge=false",
  requestOptions
)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

- Voids or delete the target queue. Returns a 404 Not found status if the queue(to be voided) doesn't exist. If not authenticated, 401 Unauthorized status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    UUID   | `Queue UUID` | Queue resource UUID           
