# Visits 

## Visits Overview 

* A Visit in OpenMRS represents precisely what it sounds like: a time when a patient is actively interacting with the 
the healthcare system, typically at a location.

* The metadata differentiating different types of visits is a Visit Type. Visit Types displayed in the user interface, also can be searched against.

* A visit contains encounters, which store more granular data about treatments or services.

## Let's look at an example of Visits

At the Amani Clinic, a patient might typically check-in at registration, be seen by a doctor, and receives medication <b> dispensed </b> in the pharmacy. This would be recorded as one <b> visit </b> of <b> visit type of Outpatient </b>, and contain <b> three encounters (Registration, Consultation, and Dispensing) </b>.

## Visits Sub Resource types

### Visits Attribute

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types.

* Visit attributes exists specifically to allow implementations to extend the data model.

## Available operations for Visits

1. [List visits](#list-visits)
2. [Create visit](#create-visit)
3. [Update visit](#update-visit)
4. [Delete visit](#delete-visit)
5. [List attribute subresource](#list-attribute-subresources)
6. [Create attribute subresource with properties](#create-an-attribute-subresource-with-properties)
7. [Update attribute subresource](#update-attribute-subresource)
6. [Delete attribute subresource](#delete-attribute-subresource)

## List visits

> List visits

```shell
GET /visit?includeInactive=true&fromStartDate=2016-10-08T04:09:23.000Z&v=default&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit?includeInactive=true&fromStartDate=2016-10-08T04:09:23.000Z&v=default&limit=1")
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
    "results": [
        {
            "uuid": "36475629-6652-44e9-a42b-c2b3b7438f72",
            "display": "Facility Visit @ Unknown Location - 18/01/2017 06:35",
            "patient": {
                "uuid": "c0cbe231-deb8-4cfa-89b4-8fb4570685fc",
                "display": "100DWN - Anthony López",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/patient/c0cbe231-deb8-4cfa-89b4-8fb4570685fc",
                        "resourceAlias": "patient"
                    }
                ]
            },
            "visitType": {
                "uuid": "7b0f5697-27e3-40c4-8bae-f4049abfb4ed",
                "display": "Facility Visit",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visittype/7b0f5697-27e3-40c4-8bae-f4049abfb4ed",
                        "resourceAlias": "visittype"
                    }
                ]
            },
            "indication": null,
            "location": {
                "uuid": "8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
                "display": "Unknown Location",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/location/8d6c993e-c2cc-11de-8d13-0010c6dffd0f",
                        "resourceAlias": "location"
                    }
                ]
            },
            "startDatetime": "2017-01-18T06:35:03.000+0000",
            "stopDatetime": "2017-01-18T08:20:03.000+0000",
            "encounters": [
                {
                    "uuid": "bc8098b3-2da2-450d-be67-54024dcc5c2c",
                    "display": "Visit Note 18/01/2017",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encounter/bc8098b3-2da2-450d-be67-54024dcc5c2c",
                            "resourceAlias": "encounter"
                        }
                    ]
                },
                {
                    "uuid": "cb35367a-5e98-4be6-9e97-ac575a29b194",
                    "display": "Vitals 18/01/2017",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/encounter/cb35367a-5e98-4be6-9e97-ac575a29b194",
                            "resourceAlias": "encounter"
                        }
                    ]
                }
            ],
            "attributes": [],
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit/36475629-6652-44e9-a42b-c2b3b7438f72",
                    "resourceAlias": "visit"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit/36475629-6652-44e9-a42b-c2b3b7438f72?v=full",
                    "resourceAlias": "visit"
                }
            ],
            "resourceVersion": "1.9"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit?includeInactive=true&fromStartDate=2016-10-08T04%3A09%3A23.000Z&v=default&limit=1&startIndex=1",
            "resourceAlias": null
        }
    ]
}

```
    
* Quickly filter visits with given query parameters. Returns a `404 Not Found` status if visit not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *[patient](#patients)* | `Patient UUID` | Get visits for this patient
    *[location](#location)* | `Location UUID` | Get visits for this location
    *includeInactive* | `Boolean` | Active/Inactive status of visit
    *fromStartDate* | `Date (ISO8601 Long)` | Start date of the visit

## List visit by UUID.

> List visit by UUID

```shell
GET /visit/:target_visit_uuid
```
    
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit/36475629-6652-44e9-a42b-c2b3b7438f72")
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

fetch("/openmrs/ws/rest/v1/visit/36475629-6652-44e9-a42b-c2b3b7438f72", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a visit by its UUID. Returns a `404 Not Found` status if visit not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
      
## Create visit
 
> Create visit

```shell
POST /visit
{
    "patient": "0dfa22b0-6b35-4594-8c3c-7589ad40ed44",
    "visitType": "7b0f5697-27e3-40c4-8bae-f4049abfb4ed",
    "startDatetime": "2016-10-08T04:09:25.000Z",
    "location": "aff27d58-a15c-49a6-9beb-d30dcfc0c66e",
    "indication": null,
    "encounters": [
        "37ecb524-6c5a-4793-a449-cab1be102199"
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"patient\": \"0dfa22b0-6b35-4594-8c3c-7589ad40ed44\",\r\n    \"visitType\": \"7b0f5697-27e3-40c4-8bae-f4049abfb4ed\",\r\n    \"startDatetime\": \"2016-10-08T04:09:25.000Z\",\r\n    \"location\": \"aff27d58-a15c-49a6-9beb-d30dcfc0c66e\",\r\n    \"indication\": null,\r\n    \"encounters\": [\r\n        \"37ecb524-6c5a-4793-a449-cab1be102199\"\r\n    ]\r\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit")
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

var raw = JSON.stringify({"patient":"0dfa22b0-6b35-4594-8c3c-7589ad40ed44","visitType":"7b0f5697-27e3-40c4-8bae-f4049abfb4ed","startDatetime":"2016-10-08T04:09:25.000Z","location":"aff27d58-a15c-49a6-9beb-d30dcfc0c66e","indication":null,"encounters":["37ecb524-6c5a-4793-a449-cab1be102199"]});

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

* To Create a visit you need to specify below attributes in the request body. If you are not logged in to perform this action, a `401 Unauthorized` status returned.


### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[patient](#patients)* | `Patient UUID` | Patient resource UUID (Required)
    *[visitType](#visits-type)* | `Patient UUID` | Visit type resource UUID (Required)
    *startDatetime* | `Date (ISO8601 Long)` | Start date of the visit
    *[location](#location)* | `Location UUID` | Location resource UUID 
    *indication* | `string` | Any indication of the visit    
    *stopDatetime* | `Date (ISO8601 Long)` | End date of the vist    
    *encounters(#encounters)* | `Array[]: Encounter UUID` | Encounter resources UUID    
    *attributes(#visits-attribute-type)* | `Array[]: Attribute` | List of visit attributes  
   
## Update visit

> Update visit

```shell
POST /visit/:target_visit_uuid
{
    "startDatetime": "2019-10-08T04:09:25.000Z"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"startDatetime\": \"2019-10-08T04:09:25.000Z\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit/c298d3e1-6def-422a-9d0a-e18906a4ae73")
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

var raw = JSON.stringify({"startDatetime":"2019-10-08T04:09:25.000Z"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/visit/c298d3e1-6def-422a-9d0a-e18906a4ae73", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target visit with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` status if visit not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[patient](#patients)* | `Patient UUID` | Patient resource UUID
    *[visitType](#visits-type)* | `Patient UUID` | Visit type resource UUID
    *startDatetime* | `Date (ISO8601 Long)` | Start date of the visit
    *[location](#location)* | `Location UUID` | Location resource UUID 
    *indication* | `string` | Any indication of the visit    
    *stopDatetime* | `Date (ISO8601 Long)` | End date of the vist    
    *encounters(#encounters)* | `Array[]: Encounter UUID` | Encounter resources UUID    
    *attributes(#visits-attribute-type)* | `Array[]: Attribute` | List of visit attributes  
        
## Delete visit

> Delete visit

```shell
DELETE /visit/:target_visit_uuid?purge=true
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/visit/c298d3e1-6def-422a-9d0a-e18906a4ae73?purge=true")
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

fetch("/openmrs/ws/rest/v1/visit/c298d3e1-6def-422a-9d0a-e18906a4ae73?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target visit by its UUID. Returns a `404 Not Found` status if visit not exists. If the user is not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

## List attribute subresources
```console
GET /visit/:target_visit_uuid/attribute 
```
* ### List all attribute subresources for a visit.

    Retrieve all <b>attribute</b> sub resources of a  <b>visit</b> resource by target_visit_uuid.Returns a 
    `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.


```console
GET /visit/:target_visit_uuid/attribute/:target_attribute_uuid
```
* ### List attribute subresources by it's UUID and parent visit UUID.
    
     Retrieve an <b>attribute</b> sub resources of a <b>visit</b> resource.Returns a 
     `404 Not Found` status if attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.

## Create an attribute subresource with properties
```console
POST visit/:target_visit_uuid/attribute 
{
    "attributeType": "target_attribute_type_uuid",
    "value": "value_for_the_attriute"
}
```
* To Create an attribute subresource for a specific visit resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute

## Update attribute subresource
```console
POST visit/:target_visit_uuid/attribute/:target_attribute_uuid
{
    "attributeType": "target_attribute_type_uuid",
    "value": "modified_attriute_value"
} 
```
* Updates an attribute subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Attribute_Type resource UUID
    *updated value* | `Depends on Attribute_Type Selected` | Updated value for the attribute

## Delete attribute subresource
```console
DELETE /visit/:target_visit_uuid/attribute/:target_attribute_uuid
```
* Delete or Retire a target attribute subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
