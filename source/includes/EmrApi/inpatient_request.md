# Inpatient Request

## Overview
Provides a means to retrieve inpatient requests (eg. requests for admission, discharge, or transfer) associated with active visits that meet the given request criteria.

## Available operations for Inpatient Request

1. [Get Inpatient Request](#get-inpatient-request)

## Get Inpatient Request

> Get Inpatient Request

```shell
GET /openmrs/ws/rest/v1/emrapi/inpatient/inpatient/request?dispositionType=ADMIT&visitLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&dispositionLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&totalCount=true&v=full
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/emrapi/inpatient/inpatient/request?dispositionType=ADMIT&visitLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&dispositionLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&totalCount=true&v=full")
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

fetch("/openmrs/ws/rest/v1/emrapi/inpatient/inpatient/request?dispositionType=ADMIT&visitLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&dispositionLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&totalCount=true&v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
  "results": [
    {
        "visit": visit,
        "patient": patient,
        "dispositionType": ADMIT | TRANSFER | DISCHARGE,
        "dispositionEncounter": encounter,
        "dispositionObsGroup": obs,
        "disposition": concept,
        "dispositionLocation": location
    }
  ],
  "totalCount": integer
}
```

This endpoint returns paged data.  The maximum number of results for any paged response is controlled by the webservices.rest module configuration.

### Supported Parameters:

* `visitLocation`: optional location uuid.  If specified, limits the requests to those associated with a visit at the given location or parent visit location
* `dispositionLocation`: optional list of location uuids.  If specified, limits the requests to those requesting one of the specified locations
* `dispositionType`: optional list of `ADMIT`, `TRANSFER` OR `DISCHAGE` allows indicating with specific types of requests should be returned
* `totalCount`: optional, defaults to false.  This is a standard REST parameter which, if passed with `true`, will included a `totalCount` property in the response.

### Available representations

This endpoint supports all standard responses:  ref, default, full, and custom.  If no specific representation is requested, the default will be returned.

#### Full representation:

* visit: `full`
* all other properties: `default`

#### Default Representation:

* visit: `default`
* all other properties: `ref`

#### Ref Representation

All properties returned as `ref` representations

#### Custom Representation

Any custom representation is supported.