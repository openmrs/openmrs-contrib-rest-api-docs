# Encounters 

## Encounter Overview

* An encounter represents an interaction between a patient and the healthcare system at a single point in time. 
Common examples would be a patient seeing a doctor during a clinic visit, a patient going to the lab to have blood drawn for
 testing, or telephone call between a provider and the patient).

* Each Encounter has an encounter type, date/time, location, and provider.

* Encounters are classified into Encounter Types, which describe the type of interaction the Encounter represents – e.g., 
"HIV Initial", "Pediatric Follow Up", "Lab"). Implementations can define their own types of encounters.

* One or more encounters may be grouped within a **Visit** (e.g., an outpatient clinic visit or a hospitalization).

* Every Encounter can have 0 to n **Observations** associated with it.
 
* Every Encounter can have 0 to n **Orders** associated with it.

 
## Let's look at an example of Encounter

During a typical Amani Clinic Outpatient Visit, a patient checks in at registration is seen by a doctor and receives medicine dispensed in the pharmacy. This would be recorded as **one visit** containing three encounters, whose types are **Registration, 
Consultation and Dispensing**.

## Sub Resource types of Encounter

### Encounter Provider

* A Provider is a person who provides care or services to patients. 

* A provider may be a clinician like a doctor or a nurse, a social worker, or a lab tech. 

* Any healthcare worker that a patient can have an encounter with is a provider.

## Available operations for Encounter 

1. [List encounters](#list-encounters)
2. [Create an encounters](#create-a-encounters)
3. [Update an encounters](#update-a-encounters)
4. [Delete an encounters](#delete-a-encounters)
5. [List encounter provider sub resource](#list-encounter-provider-sub-resources)
6. [Create encounter provider  sub resource with properties](#create-encounter-provider-sub-resource-with-properties)
7. [Update encounter provider  sub resource](#update-encounter-provider-sub-resource)
6. [Delete encounter provider  sub resource](#delete-encounter-provider-sub-resource)


## List encounters

### List all non-voided encounters.

```console
GET /encounter?
patient=96be32d2-9367-4d1d-a285-79a5e5db12b8
&fromdate=2016-10-08
```
   
    Quickly filter encounters with given query parameters. Returns a `404 Not Found` status if Encounter not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Get encounter by Encounter UUID, Patient Identifier or name
    *patient* | `Patient UUID` | Get encounter(s) for a patient
    *encounterType* | `Encounter_Type UUID` | Filter by encounter type (must be used with patient)
    *order* | `Order UUID` | Filter to encounter(s) containing the specified order (must be used with patient)
    *obsConcept* | `Concept UUID` | Filter to encounter(s) containing observation(s) for the given concept (must be used with patient)
    *obsValues* | `String` | Filter to encounter(s) containing an observations with the given value (must be used with patient & obsConcept)
    *fromdate* | `Date or Timestamp (ISO 8601)` | Start date of the encounter (must be used with patient)
    *todate* | `Date or Timestamp (ISO 8601)` | End date of the encounter (must be used with patient)
    
    
### List encounter by UUID.

```console
GET /encounter/:target_encounter_uuid
```
    Retrieve an encounter by its UUID. Returns a `404 Not Found` status if Encounter not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an encounter

```console
POST /Encounter
{
  "encounterDatetime": "2019-10-16 12:08:43",
  "patient": "070f0120-0283-4858-885d-a20d967729cf",
  "encounterType": "e22e39fd-7db2-45e7-80f1-60fa0d5a4378",
  "location": "aff27d58-a15c-49a6-9beb-d30dcfc0c66e",
  "encounterProviders": [
    {
      "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
      "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
    }
  ]
}
```
* To Create an encounter you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounterDatetime* | `Date (ISO8601 Long)` | The date and time the encounter was created (required)
    *patient* | `Patient UUID` | The patient to whom the encounter applies
    *encounterType* | `EncounterType UUID` | The type of encounter – e.g., Initial visit, Return visit, etc. (required)
    *location* | `Location UUID` | The location at which the encounter occurred (required)
    *encounterProviders* | `Array of Provider UUID and associated Encounter Role UUID` | An array of providers and their role within the encounter. At least one provider is required    
    *obs* | `Array[]: Obs` | Array of observations and values for the encounter    
    *orders* | `Array[]: Order UUID` | List of orders created during the encounter    
    *form* | `Form UUID` | Target Form UUID to be filled for the encounter
    *visit* | `Visit UUID` | When creating an encounter for an existing visit, this specifies the visit
   

## Update an encounter


```console
POST /encounter/:target_encounter_uuid
{
  "encounterDatetime": "2019-10-16 12:08:43",
  "patient": "070f0120-0283-4858-885d-a20d967729cf",
  "encounterType": "e22e39fd-7db2-45e7-80f1-60fa0d5a4378",
  "location": "aff27d58-a15c-49a6-9beb-d30dcfc0c66e",
  "encounterProviders": [
    {
      "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
      "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
    }
  ]
}
```
*  Update a target encounter with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if Encounter not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounterDatetime* | `Date (ISO8601 Long)` | The date and time the encounter was created
    *patient* | `Patient UUID` | The patient to whom the encounter applies
    *encounterType* | `EncounterType UUID` | The type of encounter – e.g., Initial visit, Return visit, etc.
    *location* | `Location UUID` | The location at which the encounter occurred
    *encounterProviders* | `Array of Provider UUID and associated Encounter Role UUID` | An array of providers and their role within the encounter. At least one provider is required    
    *obs* | `Array[]: Obs` | Array of observations and values for the encounter    
    *orders* | `Array[]: Order UUID` | List of orders created during the encounter    
    *form* | `Form UUID` | Target Form UUID to be filled for the encounter
    *visit* | `Visit UUID` | When creating an encounter for an existing visit, this specifies the visit

    
## Delete an encounter

```console
  DELETE /encounter/:target_encounter_uuid?purge=true
```
* Delete or Void a target encounter by its UUID. Returns a `404 Not Found` status if Encounter not exists. If the user is not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

## List encounter provider subresources

### List all encounter provider subresources for a visit.

```console
GET /encounter/:target_encounter_uuid/encounterprovider 
```

    Retrieve all <b>encounter provider</b> sub resources of an  <b>encounter</b> resource by target_encounter_uuid. Returns a 
    `404 Not Found` status if encounter provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.


### List encounter provider subresources by it's UUID and parent encounter UUID.

```console
GET /encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
```
    
     Retrieve an <b>encounter provider</b> sub resources of a <b>encounter</b> resource. Returns a 
     `404 Not Found` status if encounter provider not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
## Create an encounter provider sub resource with properties

```console
POST encounter/:target_encounter_uuid/encounterprovider 
{
  "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
  "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
}
```
* To Create an attribute subresource for a specific visit resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *provider* | `Provider_Type UUID` | UUID of a provider currently registered in OpenMRS (required)
    *encounterRole* | `Encounter_Role UUID` | UUID of encounter role. This is the role provider will participate during this encounter (required)
    
 
 
## Update encounter provider subresource

```console
POST encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
{
  "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
  "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
}
```
* Updates an encounter provider subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if encounter provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *parent_uuid* | `Encounter UUID` | Target encounter resource UUID
    *uuid* | `Encounter_Provider UUID` | Target encounter provider resource UUID

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *provider* | `Provider UUID` | UUID of a provider currently registered in OpenMRS (required)
    *encounterRole* | `Encounter_Role UUID` | UUID of encounter role. This is the role provider will participate during this encounter (required)


## Delete encounter provider subresource

```console
DELETE /encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
```
* Delete or Voided a target encounter provider subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
 If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = 'true'. Purging will attempt to remove the encounter provider type from the system irreversibly. Encounter provider types that have been used (i.e., are referenced from existing data) cannot be purged.

