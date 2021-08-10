# Drugs

## Available operations for Drugs

1. [List drugs](#list-drugs)
2. [Create a drug](#create-a-drug)
3. [Update a drug](#update-a-drug)
4. [Delete a drug](#delete-a-drug)


## List drugs

> List drugs

```shell
GET /drug
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/drug")
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

fetch("/openmrs/ws/rest/v1/drug", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


> Success Response

```response
{
    "results": [
        {
            "display": "test",
            "uuid": "1d0050db-bd0b-42fb-9e60-cd50c177e922",
            "name": "test",
            "description": null,
            "retired": false,
            "dosageForm": null,
            "maximumDailyDose": null,
            "minimumDailyDose": null,
            "concept": {
                "uuid": "08e5f67d-b63e-4f99-a09b-e6193125cf77",
                "display": "drug test",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/concept/08e5f67d-b63e-4f99-a09b-e6193125cf77",
                        "resourceAlias": "concept"
                    }
                ]
            },
            "combination": false,
            "strength": null,
            "drugReferenceMaps": [],
            "ingredients": [],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/drug/1d0050db-bd0b-42fb-9e60-cd50c177e922",
                    "resourceAlias": "drug"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/drug/1d0050db-bd0b-42fb-9e60-cd50c177e922?v=full",
                    "resourceAlias": "drug"
                }
            ],
            "resourceVersion": "1.12"
        }
    ]
}
```


Quickly filter drugs with given query parameters. Add parameter `includeAll=true` to also retrieve retired drugs.
If not logged in to perform this action, a `401 Unauthorized` status is returned.


### Query Parameters

| Parameter    | Type           | Description                           |
| ------------ | ---------------| ------------------------------------- |
| _q_          | `Search Query` | Filter drugs by their name |
| _includeAll_ | `Boolean`      | If true, returns also retired drugs  |


## Get a drug by UUID.

> Get a drug by UUID

```shell
GET /drug/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/drug/:uuid")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
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

fetch("/openmrs/ws/rest/v1/drug/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

* Retrieve a drug by its UUID. Returns a `404 Not Found` status if the drug does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a drug

> Create a drug

```shell
{
    "concept": "08e5f67d-b63e-4f99-a09b-e6193125cf77",
    "combination": true,
    "name": "drug name",
    "minimumDailyDose": 1,
    "maximumDailyDose": 5,
    "dosageForm": "08e5f67d-b63e-4f99-a09b-e6193125cf77"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"concept\": \"08e5f67d-b63e-4f99-a09b-e6193125cf77\",\"combination\": true,\"name\": \"drug name\",\"minimumDailyDose\": 1,\"maximumDailyDose\": 5,\"dosageForm\": \"08e5f67d-b63e-4f99-a09b-e6193125cf77\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/drug")
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

var raw = JSON.stringify({"concept": "08e5f67d-b63e-4f99-a09b-e6193125cf77","combination": true,"name": "drug name","minimumDailyDose": 1,"maximumDailyDose": 5,"dosageForm": "08e5f67d-b63e-4f99-a09b-e6193125cf77"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/drug", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To create a drug you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
  
### Attributes

Parameter | Type | Description
--- | --- | ---
*concept* | `Concept_UUID` | Concept describing this drug
*combination* | `Boolean` | Is this drug a combination
*name* | `String` | Name of a drug
*minimumDailyDose* | `Double` | Minimum drug daily dose
*maximumDailyDose* | `Double` | Maximum drug daily dose
*dosageForm* | `Concept_UUID` | Concept describing dosage form of this drug


## Update a drug

> Update a drug by its UUID

```shell
{
    "concept": "08e5f67d-b63e-4f99-a09b-e6193125cf77",
    "combination": true,
    "name": "drug name",
    "minimumDailyDose": 1,
    "maximumDailyDose": 5,
    "dosageForm": "08e5f67d-b63e-4f99-a09b-e6193125cf77"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"concept\": \"08e5f67d-b63e-4f99-a09b-e6193125cf77\",\"combination\": true,\"name\": \"drug name\",\"minimumDailyDose\": 1,\"maximumDailyDose\": 5,\"dosageForm\": \"08e5f67d-b63e-4f99-a09b-e6193125cf77\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/drug/:uuid")
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

var raw = JSON.stringify({"concept": "08e5f67d-b63e-4f99-a09b-e6193125cf77","combination": true,"name": "drug name","minimumDailyDose": 1,"maximumDailyDose": 5,"dosageForm": "08e5f67d-b63e-4f99-a09b-e6193125cf77"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/drug/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To update a drug you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*concept* | `Concept_UUID` | Concept describing this drug
*combination* | `Boolean` | Is this drug a combination
*name* | `String` | Name of a drug
*minimumDailyDose* | `Double` | Minimum drug daily dose
*maximumDailyDose* | `Double` | Maximum drug daily dose
*dosageForm* | `Concept_UUID` | Concept describing dosage form of this drug



## Delete a drug

> Delete a drug by its UUID

```shell
DELETE /drug/:uuid?purge=true
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/drug/:uuid?purge=true")
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

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/drug/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


Delete or retire a drug by its UUID. Returns a `404 Not Found` status if the drug does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

| Parameter | Type      | Description                                       |
| --------- | --------- | ------------------------------------------------- |
| _purge_   | `Boolean` | The resource will be retired unless purge = ‘true’ |

