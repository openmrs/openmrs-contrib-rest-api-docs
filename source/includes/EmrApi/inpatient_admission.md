# Inpatient Admission

## Overview
Provides a means to retrieve inpatient admissions associated with active visits that meet the given request criteria.

## Available operations for Inpatient Admission

1. [Get Inpatient Admission](#get-inpatient-admission)

## Get Inpatient Admission

This endpoint returns paged data.  The maximum number of results for any paged response is controlled by the webservices.rest module configuration.

### Supported Parameters:

* `visitLocation`: optional location uuid.  If specified, limits the admissions to those associated with a visit at the given location or parent visit location
* `currentInpatientLocation`: optional list of location uuids.  If specified, limits the admissions to those where the patient is currently at one of the given locations
* `includeDischarged`: optional, defaults to false.  If true, includes patients who have active visits but whose most recent ADT encounter is a discharge
* `totalCount`: optional, defaults to false.  This is a standard REST parameter which, if passed with `true`, will included a `totalCount` property in the response.

> Get Inpatient Admission

```shell
GET /openmrs/ws/rest/v1/emrapi/inpatient/admission?visitLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&totalCount=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/emrapi/inpatient/admission?visitLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&totalCount=true")
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

fetch("/openmrs/ws/rest/v1/emrapi/inpatient/admission?visitLocation=b6fcd85f-5995-43c9-875f-3bb2299087ff&totalCount=true", requestOptions)
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
        "currentInpatientLocation": location,
        "adtEncounters": encounter[],
        "admissionEncounters": encounter[],
        "transferEncounters": encounter[],
        "dischargeEncounters": encounter[],
        "latestAdtEncounter": encounter,
        "admissionAndTransferEncounters": encounter[],
        "firstAdmissionOrTransferEncounter": encounter,
        "latestAdmissionOrTransferEncounter": encounter,
        "encounterAssigningToCurrentInpatientLocation": encounter,
        "discharged": boolean
    }
  ],
  "totalCount": integer
}
```

### Available representations

This endpoint supports all standard responses:  ref, default, full, and custom.  If no specific representation is requested, the default will be returned.

#### Full representation:

* visit: full
* all other properties: default

#### Default Representation:

* visit: default
* currentInpatientLocation: ref,
* firstAdmissionOrTransferEncounter: custom:(uuid,display,encounterDatetime,location:ref,encounterType:ref),
* latestAdmissionOrTransferEncounter: custom:(uuid,display,encounterDatetime,location:ref,encounterType:ref),
* encounterAssigningToCurrentInpatientLocation: custom:(uuid,display,encounterDatetime,location:ref,encounterType:ref),
* discharged: default

#### Ref Representation

All properties returned as `ref` representations

#### Custom Representation

Any custom representation is supported.