# EMRAPI Configuration

## EMR API Configuration Overview

The EMR API module provides several high-level APIs and configuration settings.  The configuration endpoint provided by the `emrapi` module enables RESTful access to these configuration values.

## Available operations for EMRAPI Configuration

1. [Get EMRAPI Configuration](#get-emrapi-configuration)

## Get EMRAPI Configuration

> Get EMRAPI configuration

```shell
GET /openmrs/ws/rest/v1/emrapi/configuration
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/emrapi/configuration")
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

fetch("/openmrs/ws/rest/v1/emrapi/configuration", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
  "metadataSourceName": string,
  "orderingProviderEncounterRole": encounterRole,
  "supportsTransferLocationTag": locationTag,
  "unknownLocation": location,
  "denyAdmissionConcept": concept,
  "admissionForm": form,
  "exitFromInpatientEncounterType": encounterType,
  "extraPatientIdentifierTypes": patientIdentifierType[],
  "consultFreeTextCommentsConcept": concept,
  "sameAsConceptMapType": conceptMapType,
  "testPatientPersonAttributeType": personAttributeType,
  "admissionDecisionConcept": concept,
  "supportsAdmissionLocationTag": locationTag,
  "checkInEncounterType": encounterType,
  "transferWithinHospitalEncounterType": encounterType,
  "suppressedDiagnosisConcepts": concept[],
  "primaryIdentifierType": patientIdentifierType,
  "nonDiagnosisConceptSets": concept[],
  "fullPrivilegeLevel": role,
  "unknownProvider": provider,
  "diagnosisSets": concept[],
  "personImageDirectory": string,
  "visitNoteEncounterType": encounterType,
  "consultEncounterType": encounterType,
  "diagnosisMetadata": {
    "diagnosisCertaintyConcept": concept,
    "diagnosisOrderConcept": concept,
    "codedDiagnosisConcept": concept,
    "nonCodedDiagnosisConcept": concept,
    "diagnosisSetConcept": concept
  },
  "narrowerThanConceptMapType": conceptMapType,
  "clinicianEncounterRole": encounterRole,
  "conceptSourcesForDiagnosisSearch": conceptSource[],
  "patientDiedConcept": concept,
  "emrApiConceptSource": conceptSource,
  "lastViewedPatientSizeLimit": integer,
  "identifierTypesToSearch": patientIdentifierType[],
  "telephoneAttributeType": personAttributeType,
  "checkInClerkEncounterRole": encounterRole,
  "dischargeForm": form,
  "unknownCauseOfDeathConcept": concept,
  "visitAssignmentHandlerAdjustEncounterTimeOfDayIfNecessary": boolean,
  "atFacilityVisitType": visitType,
  "visitExpireHours": integer,
  "admissionEncounterType": encounterType,
  "dispositions": [
    {
      "uuid": string,
      "name": string,
      "conceptCode": string,
      "type: string,
      "careSettingTypes": string[],
      "encounterTypes": string[],
      "excludedEncounterTypes": string[],
	  "keepsVisitOpen": boolean,
	  "actions": string[],
	  "additionalObs": [
	    {
	      "label": string,
	      "conceptCode: string,
	      "params: map<string, string>
	    }
	  ],
    }
  ],
  "dispositionDescriptor": {
    "admissionLocationConcept": concept,
    "dateOfDeathConcept": concept,
    "dispositionConcept": concept,
    "internalTransferLocationConcept": concept,
    "dispositionSetConcept": concept
  },
  "highPrivilegeLevel": role,
  "supportsLoginLocationTag": locationTag,
  "unknownPatientPersonAttributeType": personAttributeType,
  "supportsVisitsLocationTag": locationTag,
  "transferForm": form
}
```

### Supported Parameters:

* `v`: optional, defaults to `ref`.  This allows specifying the desired representation of ref | default | full | custom

The endpoint supports all standard representations (ref, default, full, and custom).  If no representation is specified, the `ref` is returned.  
For any given representation, all properties are returned with the given representation.  
A custom representation can be used to retrieve only specific properties of interest, and specific data within those representations.
