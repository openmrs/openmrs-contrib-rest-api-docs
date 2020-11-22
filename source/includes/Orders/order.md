# Order

## Order Overview

An **Order** represents a request from a provider such as a lab test, procedure, referral, etc.

For example, a provider could order a Complete Blood Count laboratory panel for a patient.

An Order only records an intention, not whether or not the action is carried out. The results of an Order are typically recorded later as Observations.

## Available operations for Order type.

1. [List orders](#list-orders)
2. [Create an order](#create-an-order)
3. [Delete an order](#delete-an-order)

## List orders

> List orders

```shell
GET /openmrs/ws/rest/v1/order?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&caresetting=INPATIENT

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/order?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&caresetting=INPATIENT&limit=1&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```



```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/order?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&caresetting=INPATIENT&limit=1&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "8f9e24b4-0498-493c-b87c-ae1535551345",
            "orderNumber": "ORD-1",
            "accessionNumber": null,
            "patient": {
                "uuid": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
                "display": "1000C6 - Elizabeth Johnson",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/96be32d2-9367-4d1d-a285-79a5e5db12b8"
                    }
                ]
            },
            "concept": {
                "uuid": "5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
                "display": "Pulse",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                    }
                ]
            },
            "action": "NEW",
            "careSetting": {
                "uuid": "c365e560-c3ec-11e3-9c1a-0800200c9a66",
                "display": "Inpatient",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/caresetting/c365e560-c3ec-11e3-9c1a-0800200c9a66"
                    }
                ]
            },
            "previousOrder": null,
            "dateActivated": "2018-10-16T12:08:43.000+0000",
            "scheduledDate": null,
            "dateStopped": null,
            "autoExpireDate": null,
            "encounter": {
                "uuid": "69f83020-caf2-4c9e-bca7-89b8e62b52e1",
                "display": "Vitals 08/10/2016",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encounter/69f83020-caf2-4c9e-bca7-89b8e62b52e1"
                    }
                ]
            },
            "orderer": {
                "uuid": "f9badd80-ab76-11e2-9e96-0800200c9a66",
                "display": "UNKNOWN - Super User",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/provider/f9badd80-ab76-11e2-9e96-0800200c9a66"
                    }
                ]
            },
            "orderReason": null,
            "orderReasonNonCoded": null,
            "orderType": {
                "uuid": "52a447d3-a64a-11e3-9aeb-50e549534c5e",
                "display": "Test Order",
                "name": "Test Order",
                "javaClassName": "org.openmrs.TestOrder",
                "retired": false,
                "description": "Order type for test orders",
                "conceptClasses": [],
                "parent": null,
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/ordertype/52a447d3-a64a-11e3-9aeb-50e549534c5e"
                    },
                    {
                        "rel": "full",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/ordertype/52a447d3-a64a-11e3-9aeb-50e549534c5e?v=full"
                    }
                ],
                "resourceVersion": "1.10"
            },
            "urgency": "ROUTINE",
            "instructions": null,
            "commentToFulfiller": null,
            "display": "Pulse",
            "specimenSource": null,
            "laterality": null,
            "clinicalHistory": null,
            "frequency": null,
            "numberOfRepeats": null,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/order/8f9e24b4-0498-493c-b87c-ae1535551345"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/order/8f9e24b4-0498-493c-b87c-ae1535551345?v=full"
                }
            ],
            "type": "testorder",
            "resourceVersion": "1.10"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/order?patient=96be32d2-9367-4d1d-a285-79a5e5db12b8&caresetting=INPATIENT&limit=1&v=default&startIndex=1"
        }
    ]
}

```

* Fetch all non-retired orders that match any specified parameters otherwise fetch all non-retired orders. 
* If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `String` | Full or partial display name of order
    *patient* | `Patient UUID` | the patient for the order 
    *concept* | `Concept UUID` | UUID for the concept of the order; the item being requested (e.g., "serum creatinine") (Must be used with patient parameter not independently)
    *careSetting*|`String`| various levels of care-setting, for e.g.INPATIENT,OUTPATIENT etc. (Must be used with patient parameter not independently)
    *orderType* | `OrderType UUID` | the type of the order (Must be used with patient parameter not independently)
    
    *activatedOnOrBeforeDate* | `Date` | the activation date of the order (Must be used with patient parameter not independently)
    *activatedOnOrAfterDate* | `Date` | the start date of the order (Must be used with patient parameter not independently)


## Get a particular order

> Get a particular order

```shell
GET /order/:target_order_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/order")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/order", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a particular order. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.


## Create an order

> Create an order

```shell
POST /order
{
  "type":"testorder",
  "action": "new",
  "urgency": "ROUTINE",
  "dateActivated": "2018-10-16 12:08:43",
  "careSetting": "INPATIENT" ,
  "encounter": "69f83020-caf2-4c9e-bca7-89b8e62b52e1",
  "patient": "96be32d2-9367-4d1d-a285-79a5e5db12b8",
  "concept": "5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
  "orderer": "f9badd80-ab76-11e2-9e96-0800200c9a66"
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"type\": \"testorder\",\r\n    \"action\": \"new\",\r\n    \"urgency\": \"ROUTINE\",\r\n    \"dateActivated\": \"2018-10-16 12:08:43\",\r\n    \"careSetting\": \"INPATIENT\",\r\n    \"encounter\": \"69f83020-caf2-4c9e-bca7-89b8e62b52e1\",\r\n    \"patient\": \"96be32d2-9367-4d1d-a285-79a5e5db12b8\",\r\n    \"concept\": \"5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\",\r\n    \"orderer\": \"f9badd80-ab76-11e2-9e96-0800200c9a66\"\r\n}");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/order/")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=70434FCF03A8A6D351D3C9E97B7DF674")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var raw = JSON.stringify({"type":"testorder","action":"new","urgency":"ROUTINE","dateActivated":"2018-10-16 12:08:43","careSetting":"INPATIENT","encounter":"69f83020-caf2-4c9e-bca7-89b8e62b52e1","patient":"96be32d2-9367-4d1d-a285-79a5e5db12b8","concept":"5087AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA","orderer":"f9badd80-ab76-11e2-9e96-0800200c9a66"});

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/order", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To create a order, you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounter* | `Encounter UUID` | the encounter for this order (Required)
    *orderType* | `OrderType UUID` | the type of the order (Required)
    *action* | `String` | Possible actions are `NEW` (placing a new order), `REVISE` (revising an existing order), `DISCONTINUE` (request an active order to be stopped),`RENEW` (resume a prior order) (Required)
    *accessionNumber* | `String` | An optional identifier from the fulfiller (e.g., lab system) for the specimen or record associated with the order.
    *patient* | `Patient UUID` | the patient for the order (Required)
    *concept* | `Concept UUID` | UUID for the concept of the order; the item being requested (e.g., "serum creatinine") (Required)
    *careSetting*|`String`| various levels of care-setting, for e.g.INPATIENT,OUTPATIENT etc. (Required)
    *previousNumber* | `String` | when orders are revised, this links to the previous revision of the order
    *instructions* | `String` | the instructions for the order
    *urgency* | `Urgency` | `ROUTINE` (carry out order according to standard procedures), 
`STAT` (carry out order immediately), `ON_SCHEDULED_DATE` (carry out order at a specific time) (Required)
    *dateActivated* | `Date` | the start date of the order
    *dateStopped* | `Date` | the date of discontinuation
    

    

## Delete an order

> Delete an order

```shell
DELETE /order/:target_order_uuid?purge=true
```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=70434FCF03A8A6D351D3C9E97B7DF674");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/order/8f9e24b4-0498-493c-b87c-ae1535551345?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/order/8f9e24b4-0498-493c-b87c-ae1535551345?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=70434FCF03A8A6D351D3C9E97B7DF674")
  .build();
Response response = client.newCall(request).execute();

```


* Delete or void an order by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

