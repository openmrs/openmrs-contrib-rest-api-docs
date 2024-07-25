# Visit Queue Entry

## Visit Qeueue Entry Overview

- A visit queue entry in OpenMRS represents a time when a patient is actively interacting with the healthcare system and is waiting for a particular service, attending a service or finished receiving a service.

- A visit queue entry belongs to a visit, has priority and status

- Lets look at an example of a visit queue entry

At Amani Clinic, a patient might be checked-in at registration and added to the queue. After registration, the patient might be sent to triage to get their vitals taken. This will be recorded as a **visit-queue-entry** of the triage queue, where the priority might be `Not urgent` and the status `Waiting for Triage`.

## Available operations for Visit Queue Entries

1. [List visit queue entries](#list-visit-queue-entries)
2. [Visit Queue entries count](#visit-queue-entries-count)
3. [Create visit queue entry](#create-visit-queue-entry)
4. [Update visit queue entry](#update-visit-queue-entry)
5. [Delete visit queue entry](#delete-visit-queue-entry)
6. [Get average wait time](#get-average-wait-time)
7. [Generate queue number](#generate-queue-number)

## List visit queue entries

> List visit queue entries

```shell
GET /visit-queue-entry
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit-queue-entry")
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

fetch("/openmrs/ws/rest/v1/visit-queue-entry", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

> Success Response

```response
{
  "results": [
    {
      "uuid": "f1f9f637-da70-4fa6-9acb-2c031920ab7e",
      "visit": {
        "uuid": "2df63fbd-5531-47a9-9407-21bef4e92e39",
        "display": "Outpatient @ Unknown Location - 01/02/2023 09:28",
        "links": [
          {
            "rel": "self",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit/2df63fbd-5531-47a9-9407-21bef4e92e39"
          }
        ]
      },
      "queueEntry": {
        "uuid": "d0908ab4-fd94-4044-8e61-16d7e0080035",
        "display": "EFEDHA EFEDHA EFEDHA",
        "priorityComment": null,
        "sortWeight": 0.0,
        "startedAt": "2023-02-02T13:47:38.000+0300",
        "endedAt": null,
        "queue": {
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
        },
        "status": {
          "uuid": "167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
          "display": "Waiting",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/concept/167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
            }
          ]
        },
        "patient": {
          "uuid": "c26cba50-a351-11eb-aa9b-0242512be084",
          "display": "MGPMN4 - EFEDHA EFEDHA EFEDHA",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patient/c26cba50-a351-11eb-aa9b-0242512be084"
            }
          ]
        },
        "priority": {
          "uuid": "001d751b-bc13-42f4-abc5-b8ab1959dddd",
          "display": "Not Urgent",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/concept/001d751b-bc13-42f4-abc5-b8ab1959dddd"
            }
          ]
        },
        "locationWaitingFor": null,
        "providerWaitingFor": null,
        "links": [
          {
            "rel": "self",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/501b135b-1733-445e-9616-a4a05cee1bdd/entry/d0908ab4-fd94-4044-8e61-16d7e0080035"
          },
          {
            "rel": "full",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/501b135b-1733-445e-9616-a4a05cee1bdd/entry/d0908ab4-fd94-4044-8e61-16d7e0080035?v=full"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit-queue-entry/f1f9f637-da70-4fa6-9acb-2c031920ab7e"
        },
        {
          "rel": "full",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit-queue-entry/f1f9f637-da70-4fa6-9acb-2c031920ab7e?v=full"
        }
      ]
    },
    {
      "uuid": "97f00db6-92b1-44fb-9637-bf8b9e5d8b7d",
      "visit": {
        "uuid": "a6faf259-27da-4252-b85a-81ea63161c89",
        "display": "Outpatient @ Unknown Location - 15/03/2023 14:11",
        "links": [
          {
            "rel": "self",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit/a6faf259-27da-4252-b85a-81ea63161c89"
          }
        ]
      },
      "queueEntry": {
        "uuid": "9090e7a1-7454-48f4-9e02-ef96f1c16985",
        "display": "JOSHUA JOSHUA JOSHUA",
        "priorityComment": null,
        "sortWeight": null,
        "startedAt": "2023-03-15T14:11:50.000+0300",
        "endedAt": null,
        "queue": {
          "uuid": "67f984ae-f0d9-4e78-89f3-e8a15b722d49",
          "display": "Triage",
          "name": "Triage",
          "description": "Triage is for getting patient vitals",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/67f984ae-f0d9-4e78-89f3-e8a15b722d49"
            },
            {
              "rel": "full",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/67f984ae-f0d9-4e78-89f3-e8a15b722d49?v=full"
            }
          ]
        },
        "status": {
          "uuid": "167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
          "display": "Waiting",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/concept/167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
            }
          ]
        },
        "patient": {
          "uuid": "68208b38-a351-11eb-aa9b-0242512be084",
          "display": "MGLKHU - JOSHUA JOSHUA JOSHUA",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patient/68208b38-a351-11eb-aa9b-0242512be084"
            }
          ]
        },
        "priority": {
          "uuid": "001d751b-bc13-42f4-abc5-b8ab1959dddd",
          "display": "Not Urgent",
          "links": [
            {
              "rel": "self",
              "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/concept/001d751b-bc13-42f4-abc5-b8ab1959dddd"
            }
          ]
        },
        "locationWaitingFor": null,
        "providerWaitingFor": null,
        "links": [
          {
            "rel": "self",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/67f984ae-f0d9-4e78-89f3-e8a15b722d49/entry/9090e7a1-7454-48f4-9e02-ef96f1c16985"
          },
          {
            "rel": "full",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/queue/67f984ae-f0d9-4e78-89f3-e8a15b722d49/entry/9090e7a1-7454-48f4-9e02-ef96f1c16985?v=full"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit-queue-entry/97f00db6-92b1-44fb-9637-bf8b9e5d8b7d"
        },
        {
          "rel": "full",
          "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit-queue-entry/97f00db6-92b1-44fb-9637-bf8b9e5d8b7d?v=full"
        }
      ]
    }
  ]
}


```

- Quickly filter visit queue entries with given query parameters. Returns a `404 Not Found` status if visit queue entry does not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *[location](#location)* | `Location UUID` | Get visits for this location
    *[patient](#patients)* | `Patient UUID` | Patient resource UUID (Required)
    status | String | The status of the visit queue entry eg waiting
    service | String | The service of the visit queue entry eg Triage

## Visit queue entry count

> Get visit queue entries count

```shell
GET /queue/:target_queue_uuid/count
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/36475629-6652-44e9-a42b-c2b3b7438f72/count")
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
  "/openmrs/ws/rest/v1/queue/36475629-6652-44e9-a42b-c2b3b7438f72/count",
  requestOptions
)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

- Gets the count of all active visit queue entries in a given queue.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    status | String | The status of the visit queue entry eg Waiting for Triage

## List visit queue entry by UUID

> List visit queue entry by UUID

```shell
GET /queue/:target_queue_uuid/entry/:target_queue_entry_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/36475629-6652-44e9-a42b-c2b3b7438f72/entry/e6f8062c-0e9e-4377-8a34-1e72b67b5a31")
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
  "/openmrs/ws/rest/v1/queue/36475629-6652-44e9-a42b-c2b3b7438f72/entry/e6f8062c-0e9e-4377-8a34-1e72b67b5a31",
  requestOptions
)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

- Retrieves visit queue entry record by UUID. Returns a 404 Not found status if the visit queue entry(to be retrieved) doesn't exist. If not authenticated, 401 Unauthorized status is returned.

## Create visit queue entry

> Create visit queue entry

```shell
POST /visit-queue-entry
{
    "visit": {
        "uuid": "0582ac9b-ac00-43c1-bd97-0cb55db00d87"
    },
    "queueEntry": {
        "status": {
            "uuid": "167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
        },
        "priority": {
            "uuid": "001d751b-bc13-42f4-abc5-b8ab1959dddd"
        },
        "queue": {
            "uuid": "4890b934-73c3-4c91-a93b-ce48f728b520"
        },
        "patient": {
            "uuid": "35da7b7a-a352-11eb-aa9b-0242512be084"
        },
        "startedAt": "2023-03-06T11:22:49.856Z"
    }
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"visit\": {\n        \"uuid\": \"0582ac9b-ac00-43c1-bd97-0cb55db00d87\"\n    },\n    \"queueEntry\": {\n        \"status\": {\n            \"uuid\": \"167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\"\n        },\n        \"priority\": {\n            \"uuid\": \"001d751b-bc13-42f4-abc5-b8ab1959dddd\"\n        },\n        \"queue\": {\n            \"uuid\": \"4890b934-73c3-4c91-a93b-ce48f728b520\"\n        },\n        \"patient\": {\n            \"uuid\": \"35da7b7a-a352-11eb-aa9b-0242512be084\"\n        },\n        \"startedAt\": \"2023-03-06T11:22:49.856Z\"\n    }\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit-queue-entry")
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
    "visit": {
        "uuid": "0582ac9b-ac00-43c1-bd97-0cb55db00d87"
    },
    "queueEntry": {
        "status": {
            "uuid": "167407AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
        },
        "priority": {
            "uuid": "001d751b-bc13-42f4-abc5-b8ab1959dddd"
        },
        "queue": {
            "uuid": "4890b934-73c3-4c91-a93b-ce48f728b520"
        },
        "patient": {
            "uuid": "35da7b7a-a352-11eb-aa9b-0242512be084"
        },
        "startedAt": "2023-03-06T11:22:49.856Z"
    }
});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visit-queue-entry", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a visit queue entry you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[visit](#visits)* | `Visit UUID` | Visit resource UUID (Required)
    status | `Concept UUID` | Concept UUID associated with status(Required)
    priority | `Concept UUID` | Concept UUID associated with priority(Required)
    *[queue](#queue)* | `Queue UUID` | Queue resource UUID(Required)
    *startedAt* | `Date (ISO8601 Long)` | Start date of the visit queue entry
    *[patient](#patients)* | `Patient UUID` | Patient resource UUID (Required)

## Update visit queue entry

> Update visit queue entry

```shell
POST /queue/:target_queue_uuid/entry/:target_queue_entry_uuuid
{
  "endedAt": "2022-02-10 16:18:21",
  "priorityComment": "Needs urgent attention (updated)",
  "sortWeight": 1
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n  \"endedAt\": \"2022-02-10 16:18:21\",\n  \"priorityComment\": \"Needs urgent attention (updated)\",\n  \"sortWeight\": 1\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/e25e7498-eb9c-429e-bf7b-954d053b6fde/entry/0c380542-c018-4b8a-94d8-e923df32231f")
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
  "endedAt": "2022-02-10 16:18:21",
  "priorityComment": "Needs urgent attention (updated)",
  "sortWeight": 1
});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/queue/e25e7498-eb9c-429e-bf7b-954d053b6fde/entry/0c380542-c018-4b8a-94d8-e923df32231f", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a visit queue with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if visit queue entry not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    priorityComment | String | Comment on the priority
    *endedAt* | `Date (ISO8601 Long)` | End date of the visit
    sortWeight | Integer | Useful in sorting priority of patients, defaults to 1


## Delete visit queue entry

> Delete visit queue entry

```shell
DELETE /queue/:target_queue_uuid/entry/:target_queue_entry_uuid?purge=false
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue/2e26a5d7-c8d5-4700-a721-4ff0b7e5169e/entry/6f80c533-90c2-4eba-9825-e0c25e160bf5?purge=true")
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

fetch("/openmrs/ws/rest/v1/queue/2e26a5d7-c8d5-4700-a721-4ff0b7e5169e/entry/6f80c533-90c2-4eba-9825-e0c25e160bf5?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target visit queue entry by its UUID. Returns a `404 Not Found` status if visit queue entry does not exists. If the user is not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    queueUUid | `Queue UUID` | Queue resource UUID
    queueEntryUuid | `Queue Entry UUID`| Queue Entry resource uuid


## Get average wait time

> Get average wait time

```shell
GET /queue-metrics/:target_queue_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue-metrics?queue=73619fba-3f89-4a78-9188-5bd88fcb3e20")
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

fetch("/openmrs/ws/rest/v1/visit?includeInactive=true&fromStartDate=2016-10-08T04:09:23.000Z&v=default&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "queue": "Triage",
    "averageWaitTime": 10.0
}

```

* Quickly get the average wait time of each service/queue with given query parameters. Returns a `404 Not Found` status if the queue does not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *[queue](#queue)* | `Queue UUID` | Get average wait time for queue (Required)

## Generate queue number 

> Generate queue number

```shell
POST /queue-entry-number?location=target_location_uuid&queue=target_queue_uuid&visit=target_visit_uuid&visitAttributeType=target_visit_attribute_type_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/queue-entry-number?location=14bb1bfe-a095-11ed-a8fc-0242ac120002&queue=73619fba-3f89-4a78-9188-5bd88fcb3e20&visit=ea5fb718-c099-4dcd-b6d1-8799887b59f1&visitAttributeType=4890b934-73c3-4c91-a93b-ce48f728b520")
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

var raw = JSON.stringify();

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visit", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To generate a queue number you need to pass the following parameters. If you are not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[location](#location)* | `Location UUID` | Location resource UUID (Required)
    *[queue](#queue)* | `Queue UUID` | Queue resource UUID (Required)
    *[visit](#visits)* | `Visit UUID` | Visit resource UUID (Required)
    *[visitAttributeType](#visits-attribute-type)* | `Visit attribute type UUID` | Visit attribute type resource UUID (Required)
