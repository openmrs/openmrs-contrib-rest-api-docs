# Alert

## Alert Overview

Alert is a notification that selected users receive on the main page of Legacy UI.

## Available operations for Alert

1. [List alerts](#list-all-alerts)
2. [Create an alert](#create-an-alert)
3. [Update an alert](#update-an-alert)
4. [Delete an alert](#delete-an-alert)

## List all alerts

> Get all alerts

```shell
GET alert?v=default
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/alert?v=default
&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/alert?v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
  "results": [
    {
      "uuid": "b4f9a6a0-2791-4106-ba94-28cb84d5aaae",
      "display": "There was an error starting the module: Reference Demo Data Module",
      "alertId": 6,
      "text": "There was an error starting the module: Reference Demo Data Module",
      "satisfiedByAny": true,
      "dateToExpire": "2021-06-15T00:00:00.000+0200",
      "alertRead": true,
      "recipients": [
        {
          "uuid": "c3e9fe79-9af1-4d6f-9113-5ded3db4582d",
          "display": "Super User (admin)",
          "links": [
            {
              "rel": "self",
              "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert/b4f9a6a0-2791-4106-ba94-28cb84d5aaae/recipient/c3e9fe79-9af1-4d6f-9113-5ded3db4582d",
              "resourceAlias": "recipient"
            }
          ]
        }
      ],
      "links": [
        {
          "rel": "self",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert/b4f9a6a0-2791-4106-ba94-28cb84d5aaae",
          "resourceAlias": "alert"
        },
        {
          "rel": "full",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert/b4f9a6a0-2791-4106-ba94-28cb84d5aaae?v=full",
          "resourceAlias": "alert"
        }
      ],
      "resourceVersion": "1.8"
    },
    {
      "uuid": "bf40f1e9-16cb-452e-bf2c-0f9c0863d3e4",
      "display": "There was an error starting the module: Attachments",
      "alertId": 7,
      "text": "There was an error starting the module: Attachments",
      "satisfiedByAny": true,
      "dateToExpire": "2021-06-15T21:33:19.000+0200",
      "alertRead": true,
      "recipients": [
        {
          "uuid": "6dabf122-75f7-4dba-a12f-28ced570d922",
          "display": "Super User (admin)",
          "links": [
            {
              "rel": "self",
              "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert/bf40f1e9-16cb-452e-bf2c-0f9c0863d3e4/recipient/6dabf122-75f7-4dba-a12f-28ced570d922",
              "resourceAlias": "recipient"
            }
          ]
        }
      ],
      "links": [
        {
          "rel": "self",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert/bf40f1e9-16cb-452e-bf2c-0f9c0863d3e4",
          "resourceAlias": "alert"
        },
        {
          "rel": "full",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert/bf40f1e9-16cb-452e-bf2c-0f9c0863d3e4?v=full",
          "resourceAlias": "alert"
        }
      ],
      "resourceVersion": "1.8"
    }
  ],
  "links": [
    {
      "rel": "next",
      "uri": "http://localhost:8080/openmrs/ws/rest/v1/alert?v=default&startIndex=50",
      "resourceAlias": null
    }
  ]
}
```

You can add an `includeExpired=true` parameter to return also expired Alerts.
If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

| Parameter        | Type           | Description                           |
| ---------------- | -------------- | ------------------------------------- |
| _includeExpired_ | `Boolean`      | Include expired alerts                |


## Create an alert

> Create an alert

```shell
{
    "text": "New alert",
    "satisfiedByAny": true,
    "dateToExpire": null,
    "recipients": [
        {
            "recipient": "c98a1558-e131-11de-babe-001e378eb67e"
        }
    ]
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"text\": \"New alert\",\"satisfiedByAny\": true,\"dateToExpire\": null,\"recipients\": [{\"recipient\": \"c98a1558-e131-11de-babe-001e378eb67e\"}]}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/alert")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"text": "New alert","satisfiedByAny": true,"dateToExpire": null,"recipients": [{"recipient": "c98a1558-e131-11de-babe-001e378eb67e"}]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/alert", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can create a new alert with its recipients by using User's UUID as recipient's field value.
If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter                   | Type                   | Description
--------------------------- | ---------------------- | ----
*text*                      | `String`               | Text of the alert
*satisfiedByAny*            | `Boolean`              | If true, this alert will be marked as read if only one of its recipients has read it
*dateToExpire*              | `Date`                 | Date when the alert will become expired
*recipients*                | `Array[] : recipient`  | List of alert's recipients

## Update an alert using its UUID

> Update an alert

```shell
{
    "text": "Updated alert"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"text\": \"Updated alert\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/alert/:alert_uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"text":"Updated alert"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/alert/:alert_uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Update an alert with given UUID. Returns a `404 Not Found` status if the alert does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter                   | Type                   | Description
--------------------------- | ---------------------- | ----
*text*                      | `String`               | Text of the alert
*satisfiedByAny*            | `Boolean`              | If true, this alert will be marked as read if only one of its recipients has read it
*dateToExpire*              | `Date`                 | Date when the alert will become expired
*recipients*                | `Array[] : recipient`  | List of alert's recipients

## Delete an alert

> Delete an alert using its UUID

```shell
DELETE /alert/:alert_uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/alert/:alert_uuid?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/alert/:alert_uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Deletes (purges) an alert by its UUID. Returns a `404 Not Found` status if the user does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

Voiding alerts is not supported.
