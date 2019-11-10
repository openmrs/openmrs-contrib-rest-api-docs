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
    
    Quickly filter observations with given query parameters. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.
    
    ```console
    GET /obs
     ```
    
* #### Query observations by UUID.

    Retrieve an observation by its UUID. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.
    
    ```console
    GET /observation/:target_observation_uuid
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
    *valueCodedName* | `String` | the order of an Obs.
    *comment* | `String` | the order of an Obs.
    *voided* | `String` | the order of an Obs.
    *value* | `String` | v
    *valueModifier* | `String` | 
    *formFieldPath* | `String` |
    *formFieldNamespace* | `String` | 
    *status* | ENUM | 
    *interpretation* | ENUM | the enumerations related to the current state of being of an Obs
    
   
    ```console
        POST /provider
        {
          "person": "007037a0-0500-11e3-8ffd-0800200c9a66",
          "identifier": "doctor",
          "attributes": [
            {
              "attributeType": "target_attributeType_uuid",
              "value": "value_for_attribute"
            }
          ],
          "retired": false
        }
    ```
### Update an observation

*  Update a target obs, this method only modifies properties in the request. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *person* | `Person UUID` | Target person who will be a provider for OpenMRS (required)
    *identifier* | `String` | Value of the identifier.Identifier is used to virtually group providers in to groups (required)
    *attributes* | `Array[]: Attribute` |  List of provider attributes 
    *retired* | `Boolean` | Retired status for the provider.
    
    ```console
        POST /provider/:target_provider_uuid
        {
          "person": "007037a0-0500-11e3-8ffd-0800200c9a66",
          "identifier": "doctor",
          "attributes": [
            {
              "attributeType": "target_attributeType_uuid",
              "value": "value_for_attribute"
            }
          ],
          "retired": false
        }
    ```
    
### Delete an observation

* Delete or retire a target observation. Returns `404 Not Found` status if the observation does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

    ```console
        DELETE /obs/:target_obs_uuid?purge=true
     ```