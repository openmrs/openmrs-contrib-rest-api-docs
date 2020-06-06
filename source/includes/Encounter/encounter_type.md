# Encounter Type

## Encounter Type Overview

* Encounters represent an interaction between the patient and the healthcare system. Since there are a wide variety of ways in which these interactions may occur, OpenMRS allows you to categorize them by defining different types of encounter. For example, 
 "Adult Primary Care Initial Visit" and "In-Between Visit Documentation" could be different types of encounters.

* You could define encounter type for locations such as Pharmacy, Lab, Consultation room, or for actions such as admission or discharge.

## Available operations for Encounter Type 

1. [List encounter types](#list-encounter-types)
2. [Create an encounter type](#create-an-encounter-type)
3. [Update an encounter type](#update-an-encounter-type)
4. [Delete an encounter type](#delete-an-encounter-type)


## List encounter types

### List all  not-retired encounter types.

```console
GET /encountertype?
    q=Admission
```

    Quickly filter encounter types with given query parameters. Returns a `404 Not Found` status if encounter types not exist. 
    If the user not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter encounter type by its name

    
### Get encounter type by UUID.

```console
GET /encountertype/:target_encounter_type_uuid
```

    Retrieve an encounter type by its UUID. Returns a `404 Not Found` status if encounter type not exists. If the user is not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an encounter type

```console
POST /encountertype
{
    "name": "Discharge",
    "description": "Attach encounters related to hospital dischargers"
}
```
* To create an encounter type, you need to specify below attributes in the request body. If you are not logged in to perform 
this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter type (required)
    *description* | `String` | Description for the encounter type (required)
   

## Update an encounter type

```console
POST /encountertype/:target_encounter_type_uuid
{
    "name": "Discharge",
    "description": "Encounters related to hospital dischargers"
}
```
*  Update a target encounter type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if encounter type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter type
    *description* | `String` | Description for the encounter type
    

    
## Delete an encounter type

```console
DELETE /encountertype/:target_encounter_type_uuid?purge=true
```
* Delete or retire a target encounter type by its UUID. Returns a `404 Not Found` status if encounter type not exists. If the user is 
 not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

