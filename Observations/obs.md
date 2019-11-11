# Observations 

## Overview

An Observation is one single piece of information that is recorded about a person at a moment in time.

Every observation has a Concept as its question, and depending on the datatype of the concept, it has a value that is a number, date, text, Concept, etc.

Most of the information you store in OpenMRS is in the form of Observations, and most Observations happen in an Encounter. When you enter a form in OpenMRS, typically one Encounter is created with anywhere between tens or hundreds of Observations.

Note that an individual Observation is valid only at one moment in time, and it does not carry forward. You may query the system for the last observation for pregnancy status but this does not tell you whether or not the patient is pregnant at any point after the moment of that observation.

Examples of observations include Serum Creatinine of 0.9mg/dL or Review of cardiopulmonary system is normal.
 
## Available operations. 

1. [List observations](#list-observations)
2. [Create an observation](#create-an-observation)
3. [Update an observation](#update-an-observation)
4. [Delete an observation](#delete-an-observation)

### List observations

* #### List all observations.
    
    Quickly filter observations with given query parameters. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *patient* | `target_patient_uuid` | patient resource UUID
    *concept* | `target_concept_uuid`| concept resource UUID (this parameter to be used with patient)

    ```console
    GET /obs?patient=070f0120-0283-4858-885d-a20d967729cf"
     ```
    
* #### Query observations by UUID.

    Retrieve an observation by its UUID.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.
    
    ```console
    GET /obs/:target_observation_uuid
    ```
   
### Create an observation

* To Create an observation you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *person* | `Person UUID` | the Person this Obs is acting on.
    *obsDateTime* | `String` | the time this Obs took place.
    *concept* | `String` | the coded value/name given to an obs when it is made.
    *location* | `String` | the location this Obs took place (was taken).
    *order* | `String` | the order of an Obs.
    *encounter* | `String` | what obs are collected and grouped together into. An encounter is a visit.
    *accessionNumber* | `String` | a unique identifier assigned to each Obs.
    *groupMembers* | `Array[]: Obs` |  a list of Obs grouped under this Obs
    *comment* | `String` | the comment written in an Obs.
    *value* | `String` | various values saved from a given Obs.
    *status* | ENUM | the status of the observation
    *interpretation* | ENUM | the enumerations related to the current state of being of an Obs
    *voided* | `Boolean` | whether the obs is voided or not
    
   
    ```console
    POST /obs
    {
      "person": {
        "uuid": "070f0120-0283-4858-885d-a20d967729cf",
        "display": "1001MH - John Smith",
        "links": [
          {
            "rel": "self",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/070f0120-0283-4858-885d-a20d967729cf"
          }
        ]
      },
      "obsDatetime": "2016-11-10T07:37:31.000+0000",
      "voided": false,
      "status": "PRELIMINARY",
      "interpretation": "NORMAL"
    }
    ```
### Update an observation

*  Update a target obs, this method only modifies properties in the request. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *person* | `Person UUID` | the Person this Obs is acting on.
    *obsDateTime* | `String` | the time this Obs took place.
    *concept* | `String` | the coded value/name given to an obs when it is made.
    *location* | `String` | the location this Obs took place (was taken).
    *order* | `String` | the order of an Obs.
    *encounter* | `String` | what obs are collected and grouped together into. An encounter is a visit.
    *accessionNumber* | `String` | a unique identifier assigned to each Obs.
    *groupMembers* | `Array[]: Obs` |  a list of Obs grouped under this Obs
    *comment* | `String` | the comment written in an Obs.
    *value* | `String` | various values saved from a given Obs.
    *status* | ENUM | the status of the observation
    *interpretation* | ENUM | the enumerations related to the current state of being of an Obs
    *voided* | `Boolean` | whether the obs is voided or not
   
    ```console
    POST /obs
    {
      "person": {
      "uuid": "070f0120-0283-4858-885d-a20d967729cf",
      "display": "1001MH - John Smith",
      "links": [
        {
          "rel": "self",
          "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/patient/070f0120-0283-4858-885d-a20d967729cf"
        }
      ]
      },
      "obsDatetime": "2016-11-10T07:37:31.000+0000",
      "voided": true,
      "status": "PRELIMINARY",
      "interpretation": "ABNORMAL"
    }
    ```
    
### Delete an observation

* Delete or void a target observation. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

    ```console
    DELETE /obs/:target_obs_uuid?purge=true
     ```