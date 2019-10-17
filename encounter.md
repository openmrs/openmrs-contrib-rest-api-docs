# Encounters 

## Overview

* A patient visits a health center or hospital. For each electronic form completed for a patient, a new encounter is created.
Forms could be completed by different departments (ie.  drug pickup, visit with an HIV clinician, Diabetes visit, food package received), 
and will have an associated encounter_type (ie. ART Drug Regimen Pickup, Adult intake, food assistance, lab test, etc).  

* Each Encounter will have a unique encounter_id and encounter_type.  

* Each encounter has an encounter type, date/time, location and provider.

* The metadata that describes a kind of encounter is an Encounter Type. These are displayed in the user interface, 
and you may also search against them.

* A **Visit** can be associated with one or more Encounters.

* Every encounter can have 0 to n **Observations** associated with it.
 
* Every encounter can have 0 to n **Orders** associated with it.

 
### Let’s look at an example.

During a typical Amani Clinic Outpatient Visit, a patient checks in at registration, is seen by a doctor, and receives medicine 
dispensed in the pharmacy. This would be recorded as **one visit** containing three encounters, whose types are **Registration, 
Consultation, and Dispensing**.

## Sub Resource types

### Encounter Provider.

* A Provider is a person who provides care or services to patients. 

* A provider may be a clinician like a doctor or nurse, a social worker, or a lab tech. 

* Any healthcare worker that a patient can have an encounter with is a provider.

## Available operations. 

1. [List encounters](#list-encounters)
2. [Create an encounters](#create-a-encounters)
3. [Update an encounters](#update-a-encounters)
4. [Delete an encounters](#delete-a-encounters)
5. [List encounter provider sub resource](#list-encounter-provider-sub-resources)
6. [Create encounter provider  sub resource with properties](#create-encounter-provider-sub-resource-with-properties)
7. [Update encounter provider  sub resource](#update-encounter-provider-sub-resource)
6. [Delete encounter provider  sub resource](#delete-encounter-provider-sub-resource)


### List encounters

* #### List all non-retired encounters.
    
    Quickly filter encounters with given query parameters.Returns a `404 Not Found` status if encounter not exists. If user not logged 
    in to perform this action,a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Get encounter by Encounter Id, Patient Identifier or name
    *patient* | `Patient UUID` | Get encounter by target_patient_uuid
    *encounterType* | `Encounter_Type UUID` | Encounter type uuid. Must be used with patient
    *order* | `Order UUID` | Filter by target_order_uuid. Must be used with patient
    *obsConcept* | `Obs UUID` | Filter by target_obs_uuid. Must be used with patient
    *obsValues* | `String` | Filter vy value of the obs object. Must be used with patient & obsConcept.
    *fromdate* | `Date (ISO8601 Long)` | Start date of the encounter type. Must be used with patient
    *todate* | `Date (ISO8601 Long)` | End date of the encounter type. Must be used with patient
    

    ```console
    GET /encounter?
      q=John
      &fromdate=2016-10-08T04:09:23.000Z
     ```
    
* #### List encounter by UUID.

    Retrieve an encounter by its UUID. Returns a `404 Not Found` status if encounter not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /encounter/:target_encounter_uuid
    ```
   
### Create an encounter

* To Create an encounter you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounterDatetime* | `Date (ISO8601 Long)` | The date and time the encounter was created (required)
    *patient* | `Patient UUID` | Patient type resource UUID (required)
    *encounterType* | `EncounterType UUID` | Encounter type resource UUID (required)
    *location* | `Location UUID` | Location resource UUID (required)
    *encounterProviders* | `Array[]: Providers` | Array of Providers already registred in OpenMRS    
    *obs* | `Array[]: Obs` | Array of observations and values for the encounter.    
    *orders* | `Array[]: Order UUID` | List of orders created during the encounter    
    *form* | `FormType UUID` | Form type to be filled for the encounter
    *visit* | `Visit UUID` | If allocating an encounter for an already existing visit should specify the target visit UUID 
   
    ```console
        POST /encounter
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
### Update an encounter

*  Update a target encounter with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if encounter not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_encounter_uuid` | Target encounter resource UUID
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounterDatetime* | `Date (ISO8601 Long)` | The date and time the encounter was created (required)
    *patient* | `Patient UUID` | Patient type resource UUID (required)
    *encounterType* | `EncounterType UUID` | Encounter type resource UUID (required)
    *location* | `Location UUID` | Location resource UUID (required)
    *encounterProviders* | `Array[]: Providers` | Array of Providers already registered in OpenMRS    
    *obs* | `Array[]: Obs` | Array of observations and values for the encounter.    
    *orders* | `Array[]: Order UUID` | List of orders created during the encounter    
    *form* | `FormType UUID` | Form type to be filled for the encounter
    *visit* | `Visit UUID` | If allocating an encounter for an already existing visit should specify the target visit UUID 
    
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
    
### Delete an encounter

* Delete or Retire a target encounter by its UUID. Returns a `404 Not Found` status if encounter not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /encounter/:target_encounter_uuid?purge=true
     ```
### List encounter provider sub resources

* #### List all encounter provider sub resources for a visit.

    Retrieve all <b>encounter provider</b> sub resources of an  <b>encounter</b> resource by target_encounter_uuid.Returns a 
    `404 Not Found` status if encounter provider not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

    ```console
        GET /encounter/:target_encounter_uuid/encounterprovider 
    ```

* #### List encounter provider sub resources by it's UUID and parent encounter UUID.
    
     Retrieve an <b>encounter provider</b> sub resources of a <b>encounter</b> resource.Returns a 
     `404 Not Found` status if encounter provider not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
    ```console
        GET /encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
    ```
### Create an encounter provider sub resource with properties

* To Create an attribute sub resource for a specific visit resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *provider* | `Provider_Type UUID` | UUID of a provider currently registered in OpenMRS (required)
    *encounterRole* | `Encounter_Role UUID` | UUID of encounter role. This is the role provider will participate during this encounter (required)
    
    ```console
        POST encounter/:target_encounter_uuid/encounterprovider 
        {
          "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
          "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
        }
    ```
 
 
### Update encounter provider sub resource

* Updates an encounter provider sub resource value with given uuid, this method will only modify value of the sub resource.Returns 
a `404 Not Found` status if encounter provider not exists.If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *parent_uuid* | `target_encounter_uuid` | Target encounter resource UUID
    *uuid* | `target_encounter_provider_uuid` | Target encounter provider resource UUID

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *provider* | `Provider_Type UUID` | UUID of a provider currently registered in OpenMRS (required)
    *encounterRole* | `Encounter_Role UUID` | UUID of encounter role. This is the role provider will participate during this encounter (required)

    ```console
        POST encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
        {
          "provider": "bb1a7781-7896-40be-aaca-7d1b41d843a6",
          "encounterRole": "240b26f9-dd88-4172-823d-4a8bfeb7841f"
        }
    ```
### Delete encounter provider sub resource

* Delete or Retire a target encounter provider sub resource by its UUID.Returns a `404 Not Found` status if attribute not exists. 
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’. Purging will attempt to irreversibly remove the encounter provider type from the system. Encounter provider types that have been used (i.e., are referenced from existing data) cannot be purged.
    
     ```console
        DELETE /encounter/:target_encounter_uuid/encounterprovider/:target_encounter_provider_uuid
     ```
