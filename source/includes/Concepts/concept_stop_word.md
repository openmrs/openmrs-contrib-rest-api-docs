# Concept Stop Word

## Available Operations for Concept Stop Word

1. [List Stop Words](#list-stop-words)
2. [Create a Stop Word](#create-a-stop-word)
3. [Update a Stop Word](#update-a-stop-word)
4. [Delete a Stop Word](#delete-a-stop-word)

## List Stop Words

> List Stop Words
```shell
GET /conceptstopword
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptstopword")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");
var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/conceptstopword", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "f5f45540-e2a7-11df-87ae-18a905e044dc",
            "display": "A",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f45540-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f469ae-e2a7-11df-87ae-18a905e044dc",
            "display": "AND",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f469ae-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f47070-e2a7-11df-87ae-18a905e044dc",
            "display": "AT",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f47070-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f476c4-e2a7-11df-87ae-18a905e044dc",
            "display": "BUT",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f476c4-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f47d04-e2a7-11df-87ae-18a905e044dc",
            "display": "BY",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f47d04-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f4834e-e2a7-11df-87ae-18a905e044dc",
            "display": "FOR",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f4834e-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f48a24-e2a7-11df-87ae-18a905e044dc",
            "display": "HAS",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f48a24-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f49064-e2a7-11df-87ae-18a905e044dc",
            "display": "OF",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f49064-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f496ae-e2a7-11df-87ae-18a905e044dc",
            "display": "THE",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f496ae-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        },
        {
            "uuid": "f5f49cda-e2a7-11df-87ae-18a905e044dc",
            "display": "TO",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/conceptstopword/f5f49cda-e2a7-11df-87ae-18a905e044dc",
                    "resourceAlias": "conceptstopword"
                }
            ]
        }
    ]
}
```

Fetch all Concept Stop Words. Returns a `200 OK` status with the Concept Stop Words response.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

## List Concept Stop Word by UUID.

> List Concept Stop Word by UUID
```shell
GET /conceptstopword/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptstopword/:uuid")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");
var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/conceptstopword/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieve a Concept Stop Word by its UUID. Returns a `404 Not Found` status if stop word does not exist.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

## Create a Stop Word

> Create a Stop Word

```shell
POST /conceptstopword
{
    "value": "AND",
    "locale": "en"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"value\": \"AND\",\"locale\": \"en\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptstopword")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");
var raw = JSON.stringify({"value": "AND","locale": "en"});
var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/conceptstopword", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a Concept Stop Word you need to specify the below properties in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *value* | `String` | Word text
    *locale* | `String` | Language code of the value string


## Update a Stop Word

> Update a Stop Word

```shell
POST /conceptstopword/:uuid
{
    "value": "AND",
    "locale": "en"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"value\": \"AND\",\"locale\": \"en\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptstopword/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");
var raw = JSON.stringify({"value": "AND","locale": "en"});
var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/conceptstopword/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Update a Concept Stop Word. This method only modifies properties specified in the request. Returns a `404 Not found` if stop word does not exist. If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

### Properties

    Parameter | Type | Description
    --- | --- | ---
    *value* | `String` | Word text
    *locale* | `String` | Language code of the value string


## Delete a Stop Word

> Delete a Stop Word

```shell
DELETE /conceptstopword/:uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/conceptstopword/:uuid?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");
var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/conceptstopword/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Deletes a Concept Stop Word by its UUID. Returns a `404 Not Found` status if stop word does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

This resource doesn't support voiding/retiring.
