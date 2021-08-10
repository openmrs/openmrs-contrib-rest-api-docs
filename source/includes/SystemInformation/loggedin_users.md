# Logged in Users

## Logged in Users Overview

OpenMRS REST API allows you to query list of logged in usernames.

## List Logged in Users

> List Logged in Users

```shell
GET /loggedinusers
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/loggedinusers")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/loggedinusers", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
> Success Response

```response
[
    "admin"
]
```

* Fetch list of logged in usernames.
* If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.
