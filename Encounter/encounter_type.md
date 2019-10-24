# Encounter Type

## Overview

* A visit can be associated with one or more encounters. OpenMRS allows you to define multiple encounter types.

* You could define encounter type for locations such as Pharmacy, Lab, Consultation room or for actions such as admission or discharge.

## Available operations. 

1. [List encounter types](#list-encounter-types)
2. [Create an encounter type](#create-a-encounter-type)
3. [Update an encounter type](#update-a-encounters-type)
4. [Delete an encounter type](#delete-a-encounters-type)


### List encounter types

* #### List all non-voided encounter types.
    
    Quickly filter encounter types with given query parameters.Returns a `404 Not Found` status if encounter types not exists. 
    If user not logged in to perform this action,a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter encounter type by it's name (i.e., no apostrophe)

    ```console
    GET /encountertype?
      q=Admission
     ```
    
* #### Get encounter type by UUID.

    Retrieve an encounter type by its UUID. Returns a `404 Not Found` status if encounter type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /encountertype/:target_encounter_type_uuid
    ```
   
### Create an encounter type

* To Create an encounter type you need to specify below attributes in the request body. If you are not logged in to perform 
this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter type (required)
    *description* | `String | Description for the encounter type (required)
   
    ```console
        POST /encountertype
        {
          "name": "Discharge",
          "description": "Attach encounters related to hospital dischargers"
        }
    ```
### Update an encounter type

*  Update a target encounter type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if encounter type not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter type
    *description* | `String | Description for the encounter type
    
    ```console
        POST /encountertype/:target_encounter_type_uuid
        {
          "name": "Discharge",
          "description": "Encounters related to hospital dischargers"
        }
    ```
    
### Delete an encounter type

* Delete or Void a target encounter type by its UUID. Returns a `404 Not Found` status if encounter type not exists.If user 
 not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

    ```console
        DELETE /encountertype/:target_encounter_type_uuid?purge=true
     ```
````
