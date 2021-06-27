# AutoGenerationOption

## AutoGenerationOption Overview

AutoGenerationOption is a Resource which encapsulates the options for Auto-Generating a Patient Identifier.

## Available operations for AutoGenerationOption

1. [List AutoGenerationOptions](#list-autogenerationoptions)
2. [Create an AutoGenerationOption](#create-an-autogenerationoption)
3. [Update an AutoGenerationOption](#update-an-autogenerationoption)
4. [Delete an AutoGenerationOption](#delete-an-autogenerationoption)

## List AutoGenerationOptions

> List AutoGenerationOptions

```shell
GET idgen/autogenerationoption?v=default
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/autogenerationoption?v=default
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

fetch("/openmrs/ws/rest/v1/idgen/autogenerationoption?v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "b57bda1d-dbe5-436e-af0f-331be90fee4e",
            "identifierType": {
                "uuid": "05a29f94-c0ed-11e2-94be-8c13b969e334",
                "display": "OpenMRS ID",
                "name": "OpenMRS ID",
                "description": "OpenMRS patient identifier, with check-digit",
                "format": null,
                "formatDescription": null,
                "required": true,
                "validator": "org.openmrs.module.idgen.validator.LuhnMod30IdentifierValidator",
                "locationBehavior": null,
                "uniquenessBehavior": null,
                "retired": false,
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334",
                        "resourceAlias": "patientidentifiertype"
                    },
                    {
                        "rel": "full",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334?v=full",
                        "resourceAlias": "patientidentifiertype"
                    }
                ],
                "resourceVersion": "2.0"
            },
            "location": null,
            "source": {
                "uuid": "691eed12-c0f1-11e2-94be-8c13b969e334",
                "name": "Generator for OpenMRS ID",
                "description": null,
                "baseCharacterSet": "0123456789ACDEFGHJKLMNPRTUVWXY",
                "prefix": null,
                "suffix": null,
                "firstIdentifierBase": "10000",
                "minLength": 6,
                "maxLength": null,
                "identifierType": {
                    "uuid": "05a29f94-c0ed-11e2-94be-8c13b969e334",
                    "display": "OpenMRS ID",
                    "name": "OpenMRS ID",
                    "description": "OpenMRS patient identifier, with check-digit",
                    "format": null,
                    "formatDescription": null,
                    "required": true,
                    "validator": "org.openmrs.module.idgen.validator.LuhnMod30IdentifierValidator",
                    "locationBehavior": null,
                    "uniquenessBehavior": null,
                    "retired": false,
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334",
                            "resourceAlias": "patientidentifiertype"
                        },
                        {
                            "rel": "full",
                            "uri": "http://localhost:8080/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334?v=full",
                            "resourceAlias": "patientidentifiertype"
                        }
                    ],
                    "resourceVersion": "2.0"
                },
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/identifiersource/691eed12-c0f1-11e2-94be-8c13b969e334",
                        "resourceAlias": "identifiersource"
                    }
                ],
                "type": "sequentialidentifiergenerator",
                "resourceVersion": "1.8"
            },
            "manualEntryEnabled": false,
            "automaticGenerationEnabled": true,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/autogenerationoption/b57bda1d-dbe5-436e-af0f-331be90fee4e",
                    "resourceAlias": "autogenerationoption"
                },
                {
                    "rel": "full",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/autogenerationoption/b57bda1d-dbe5-436e-af0f-331be90fee4e?v=full",
                    "resourceAlias": "autogenerationoption"
                }
            ],
            "resourceVersion": "1.8"
        }
    ]
}
```

Fetches list of AutoGenerationOptions. If not logged in to perform this action, a `401 Unauthorized` status is returned.

## Get AutoGenerationOption by UUID.

> Get AutoGenerationOption by UUID

```shell
GET idgen/autogenerationoption/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/autogenerationoption/:uuid
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

fetch("/openmrs/ws/rest/v1/idgen/autogenerationoption/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieves an AutoGenerationOption by its UUID. Returns a `404 Not Found` status if the object does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create an AutoGenerationOption

> Create an AutoGenerationOption

```shell
POST idgen/autogenerationoption
{
    "source": "691eed12-c0f1-11e2-94be-8c13b969e334",
    "identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334",
    "manualEntryEnabled": true,
    "automaticGenerationEnabled": true,
    "location": "2131aff8-2e2a-480a-b7ab-4ac53250262b"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"source\": \"691eed12-c0f1-11e2-94be-8c13b969e334\",\"identifierType\": \"05a29f94-c0ed-11e2-94be-8c13b969e334\",\"manualEntryEnabled\": true,\"automaticGenerationEnabled\": true,\"location\": \"2131aff8-2e2a-480a-b7ab-4ac53250262b\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/autogenerationoption")
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

var raw = JSON.stringify({"source": "691eed12-c0f1-11e2-94be-8c13b969e334","identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334","manualEntryEnabled": true,"automaticGenerationEnabled": true,"location": "2131aff8-2e2a-480a-b7ab-4ac53250262b"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/autogenerationoption", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can create new instance of AutoGenerationOptions by POSTing to the endpoint above with properties below.
If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*[source](#patientidentifiersource)* | `PatientIdentifierSource_UUID` | Option's IdentifierSource (Required)
*[identifierType](#patientidentifiertype)* | `PatientIdentifierType_UUID` | Option's IdentifierType (Required)
*manualEntryEnabled* | `Boolean` | Is manual entry enabled for this identifier generator (Required)
*automaticGenerationEnabled* | `Boolean` | Is auto generation enabled for this identifier generator (Required)
*[location](#location)* | `Location_UUID` | Location where these Options will be applicable (Optional)


## Update an AutoGenerationOption

> Update an AutoGenerationOption

```shell
POST idgen/autogenerationoption/:uuid
{
    "source": "691eed12-c0f1-11e2-94be-8c13b969e334",
    "manualEntryEnabled": true,
    "automaticGenerationEnabled": true,
    "location": "2131aff8-2e2a-480a-b7ab-4ac53250262b"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"source\": \"691eed12-c0f1-11e2-94be-8c13b969e334\",\"manualEntryEnabled\": true,\"automaticGenerationEnabled\": true,\"location\": \"2131aff8-2e2a-480a-b7ab-4ac53250262b\"}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/autogenerationoption/:uuid")
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

var raw = JSON.stringify({"source": "691eed12-c0f1-11e2-94be-8c13b969e334","manualEntryEnabled": true,"automaticGenerationEnabled": true,"location": "2131aff8-2e2a-480a-b7ab-4ac53250262b"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/autogenerationoption/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can update existing instance of AutoGenerationOptions by POSTing to the endpoint above with properties below.
If object with given UUID doesn't exist, a `404 Not Found` status is returned.
If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*[source](#patientidentifiersource)* | `PatientIdentifierSource_UUID` | Option's IdentifierSource (Required)
*manualEntryEnabled* | `Boolean` | Is manual entry enabled for this identifier generator (Required)
*automaticGenerationEnabled* | `Boolean` | Is auto generation enabled for this identifier generator (Required)
*[location](#location)* | `Location_UUID` | Location where these Options will be applicable (Optional)


## Delete an AutoGenerationOption

> Delete an AutoGenerationOption

```shell
DELETE idgen/autogenerationoption/:uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/autogenerationoption/:uuid?purge=true")
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

fetch("openmrs/ws/rest/v1/idgen/autogenerationoption/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Delete (purge) AutoGenerationOptions by their UUID. Returns a `404 Not Found` status if the object does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

This resource cannot be voided/retired.
