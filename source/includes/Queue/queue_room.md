# Queue Room

## Queue Room Overview

* A Queue Room in OpenMRS represents a physical location in a hospital where a service is provided. Patients wait to go in and receive a specific service in the queue room one at a time.

## Available operations for Queue Room
1. [List queue room](#list-queue-room)
2. [Create queue room](#create-queue-room)
3. [Update queue room](#update-queue-room)
4. [Delete queue room](#delete-queue-room)
5. [Add provider to queue room](#add-provider-to-queue-room)

## List queue room

> List queue room

```shell
GET /queueroom
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queueroom?location=14bb1bfe-a095-11ed-a8fc-0242ac120002&queue=4890b934-73c3-4c91-a93b-ce48f728b520")
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

fetch("/openmrs/ws/rest/v1/queueroom?location=14bb1bfe-a095-11ed-a8fc-0242ac120002&queue=4890b934-73c3-4c91-a93b-ce48f728b520", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
  "results": [
    {
      "uuid": "6543436d-ba98-4f18-9207-7019dc6b3227",
      "display": "Room 1",
      "name": "Room 1",
      "description": "Room 1",
      "links": [
        {
          "rel": "self",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queueroom/6543436d-ba98-4f18-9207-7019dc6b3227"
        },
        {
          "rel": "full",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queueroom/6543436d-ba98-4f18-9207-7019dc6b3227?v=full"
        }
      ]
    },
    {
      "uuid": "7a552e16-f7f6-4558-9422-069cbc79ab19",
      "display": "Room 2",
      "name": "Room 2",
      "description": "Room 2",
      "links": [
        {
          "rel": "self",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queueroom/7a552e16-f7f6-4558-9422-069cbc79ab19"
        },
        {
          "rel": "full",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queueroom/7a552e16-f7f6-4558-9422-069cbc79ab19?v=full"
        }
      ]
    }
  ]
}

```

* Quickly filter queue rooms with given query parameters. Returns a `404 Not Found` status if queue room does not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *[queue](#queues)* | `Queue UUID` | Get rooms for this queue (Required)
    *[location](#location)* | `Location UUID` | Get rooms for this location (Required)

## List queue room by UUID

> List queue room by UUID

```shell
GET /queueroom/:target_queue_room_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queueroom/7a552e16-f7f6-4558-9422-069cbc79ab19")
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

fetch("/openmrs/ws/rest/v1/queueroom/7a552e16-f7f6-4558-9422-069cbc79ab19", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a queue room by its UUID. Returns a `404 Not Found` status if queue room does not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.

## Create queue room

> Create queue room

```shell
POST /queueroom
{
    "name": "Room 1",
    "description": "Room 1",
    "queue": {
        "uuid": "8764727d-cb3c-4af7-8ffa-ca32bc21f626"
    }
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"name\": \"Room 1\",\n    \"description\": \"Room 1\",\n    \"queue\": {\n        \"uuid\": \"8764727d-cb3c-4af7-8ffa-ca32bc21f626\"\n    }\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queueroom")
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
    "name": "Room 1",
    "description": "Room 1",
    "queue": {
        "uuid": "8764727d-cb3c-4af7-8ffa-ca32bc21f626"
    }
});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/queueroom", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a queue room you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

  Parameter | Type | Description
  --- | --- | ---
  *name* | `String` | Name of the queue room (Required)
  *description* | `String` | Description (Required)
  *[queue](#queue)* | `Queue UUID` | Queue resource UUID (Required) 

## Update queue room

> Update queue room

```shell
POST /queueroom/:target_queue_room_uuid
{
    "name": "Room 1 rename",
    "description": "Room 1",
    "queue": {
        "uuid": "73619fba-3f89-4a78-9188-5bd88fcb3e20"
    }
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"name\": \"Room 1\",\n    \"description\": \"Room 1\",\n    \"queue\": {\n        \"uuid\": \"8764727d-cb3c-4af7-8ffa-ca32bc21f626\"\n    }\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queueroom")
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
    "name": "Room 1",
    "description": "Room 1",
    "queue": {
        "uuid": "8764727d-cb3c-4af7-8ffa-ca32bc21f626"
    }
});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/queueroom", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Update a target queue room with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if queue room does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

  Parameter | Type | Description
  --- | --- | ---
  *name* | `String` | Name of the queue room
  *description* | `String` | Description
  *[queue](#queue)* | `Queue UUID` | Queue resource UUID 

## Delete queue room

> Delete queue room

```shell
DELETE /queueroom/:target_queue_room_uuid?purge=false
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queueroom/c298d3e1-6def-422a-9d0a-e18906a4ae73?purge=false")
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

fetch("/openmrs/ws/rest/v1/queueroom/c298d3e1-6def-422a-9d0a-e18906a4ae73?purge=false", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target queue room by its UUID. Returns a `404 Not Found` status if queue room does not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

## Add provider to queue room

> Add provider to queue room

```shell
POST /roomprovidermap
{
    "queueRoom": {
        "uuid": "0dfa22b0-6b35-4594-8c3c-7589ad40ed44"
    },
    "provider": {
        "uuid": "7b0f5697-27e3-40c4-8bae-f4049abfb4ed"
    }
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"queueRoom\": {\n        \"uuid\": \"0dfa22b0-6b35-4594-8c3c-7589ad40ed44\"\n    },\n    \"provider\": {\n        \"uuid\": \"7b0f5697-27e3-40c4-8bae-f4049abfb4ed\"\n    }\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/roomprovidermap")
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
    "queueRoom": {
        "uuid": "0dfa22b0-6b35-4594-8c3c-7589ad40ed44"
    },
    "provider": {
        "uuid": "7b0f5697-27e3-40c4-8bae-f4049abfb4ed"
    }
});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/roomprovidermap", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To add a provider to a queue room you need to specify the attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.


### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[queueRoom](#queueroom)* | `Queue Room UUID` | Queue room resource UUID (Required)
    *[provider](#providers)* | `Provider UUID` | Provider resource UUID (Required)