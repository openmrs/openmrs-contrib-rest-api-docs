# PatientIdentifierType

## PatientIdentifierType Overview
Administrators define what types of identifiers they will collect. These range from National ID numbers, to driver's license numbers, to per-hospital medical record numbers.


## Available operations for PatientIdentifierType

1. [List PatientIdentifierType resources](#list-patientidentifiertype-resource)
2. [Create a patientIdentifierType record](#create-a-patientidentifierType)
3. [Update a patientIdentifierType record](#update-a-patientIdentifierType)
4. [Delete a patientIdentifierType record](#delete-a-patientIdentifierType)

## List PatientIdentifierType resource

> List PatientIdentifierType resource

```shell
GET /patientidentifiertype?v=default&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patientidentifiertype?v=default&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patientidentifiertype?v=default&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
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
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334",
                    "resourceAlias": "patientidentifiertype"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334?v=full",
                    "resourceAlias": "patientidentifiertype"
                }
            ],
            "resourceVersion": "2.0"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patientidentifiertype?limit=1&v=default&startIndex=1",
            "resourceAlias": null
        }
    ]
}

```

* Fetch all non-retired patientIdentifierTypes resources that match any specified parameters otherwise fetch all non-retired patients. Returns a `200 OK` status with the patientIdentifierType response. If the user is not logged in a `401 Unauthorized` status is returned.


## Get patientIdentifierType by UUID.

> Get patientIdentifierType by UUID

```shell
GET /patientidentifiertype/:target_patientIdentifierType_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a patientIdentifierType by its UUID. Returns a `404 Not Found` status if patientIdentifierType does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a patientIdentifierType

> Create a patientIdentifierType

```shell
POST /patientidentifiertype
{
    "name": "Wilson Hosp MRN",
    "description": "Wilson Hospital Medical Record Number",
    "format": "\\d{1,10}-\\d",
    "formatDescription": "Up to ten digts followed by a hyphen and another digit",
    "required": false,
    "validator": "org.openmrs.patient.impl.LuhnIdentifierValidator",
    "locationBehavior": "NOT_USED",
    "uniquenessBehavior": null
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"Wilson Hosp MRN\",\r\n    \"description\": \"Wilson Hospital Medical Record Number\",\r\n    \"format\": \"\\\\d{1,10}-\\\\d\",\r\n    \"formatDescription\": \"Up to ten digts followed by a hyphen and another digit\",\r\n    \"required\": false,\r\n    \"validator\": \"org.openmrs.patient.impl.LuhnIdentifierValidator\",\r\n    \"locationBehavior\": \"NOT_USED\",\r\n    \"uniquenessBehavior\": null\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patientidentifiertype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();


```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var raw = JSON.stringify({"name":"Wilson Hosp MRN","description":"Wilson Hospital Medical Record Number","format":"\\d{1,10}-\\d","formatDescription":"Up to ten digts followed by a hyphen and another digit","required":false,"validator":"org.openmrs.patient.impl.LuhnIdentifierValidator","locationBehavior":"NOT_USED","uniquenessBehavior":null});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patientidentifiertype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a patientIdentifierType you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

Parameter | Type | Description
--- | --- | ---
*name* | string | label for the identifier (Required)
*description* | string | a small description about the patientIdentifier
*format* | string | a regular expression defining what the identifier text should contain
*formatDescription* | string | an optional description of the regular expression,(used to explain the requirements of the regular expression in terms a user would understand). For example, a regular expression like `\d{4,8}` could have a description like "Must be a number between 4 and 8 digits in length."
*required* | boolean | a true/false whether every patient must have this type
*validator* | string | full class name of an [IdentifierValidator](https://docs.openmrs.org/doc/org/openmrs/patient/IdentifierValidator.html) (e.g., [`org.openmrs.patient.impl.LuhnIdentifierValidator`](https://docs.openmrs.org/doc/org/openmrs/patient/impl/LuhnIdentifierValidator.html))

*locationBehavior* | "REQUIRED" or "NOT USED" | behavior of the location with respect to the identifier,"REQUIRED" if a location must be associated with the identifier; "NOT_USED" if the identifier does require a location
 
*uniquenessBehavior* | string | specify the uniqueness of the behaviour, it can be either Unique, Non Unique or Location.


## Update a patientIdentifierType

> Update a patientIdentifierType

```shell
POST /patientidentifertype/:target_patientidentifiertype_uuid
{
    "format": "\\d{1,10}-",
    "formatDescription": "Up to ten digts followed by a hyphen"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"format\": \"\\\\d{1,10}-\",\r\n    \"formatDescription\": \"Up to ten digts followed by a hyphen\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var raw = JSON.stringify({"format":"\\d{1,10}-","formatDescription":"Up to ten digts followed by a hyphen"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Update a target patientIdentifierType with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if patientIdentifierType not exists. If user not logged in to perform this action, a `401 Unauthorized status returned`.



## Delete a patientIdentifierType

> Delete a patientIdentifierType

```shell
DELETE /patientidentifiertype/:target_patientidentifiertype_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=33B84B3BEA8E81E9D22D5A722815E010");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or retire a target patientIdentifierType by its UUID. Returns a `404 Not Found` status if patientIdentifierType not exists. If user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = 'true'

