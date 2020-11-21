# Encounter Role

## Encounter Role Overview

* An Encounter role is specific to the [encounter](encounter.md). While these could match up to existing organizational roles (e.g., "Nurse"), 
they don't have to (e.g., "Lead Surgeon").

## Available operation for Encounter Roles 

1. [List encounter roles](#list-encounter-roles)
2. [Create an encounter role](#create-a-encounter-role)
3. [Update an encounter role](#update-a-encounters-role)
4. [Delete an encounter role](#delete-a-encounters-role)


## List encounter roles

### List all non-voided encounter roles.

```console
GET /encounterrole?
    q=Clinician
```
    
    Quickly filter encounter roles with given query parameters. Returns a `404 Not Found` status if encounter roles not exist. 
     If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter encounter role by its name

    
### Get encounter role by UUID.

```console
GET /encounter/:target_encounter_role_uuid
```
    Retrieve an encounter role by its UUID. Returns a `404 Not Found` status if encounter role not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create an encounter role

```console
POST /encounterrole
{
    "name": "Clinician",
    "description": "A provider assisting the Lead Surgeon."
}
```
* To Create an encounter role, you need to specify below attributes in the request body. If you are not logged in to perform 
this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter role (required)
    *description* | `String | Description for the encounter role (required)
   

## Update an encounter role

```console
POST /encounterrole/:target_encounter_role_uuid
{
    "name": "Assisting Surgeon"",
    "description": "A surgeon who assisted the Lead Surgeon"
}
```
*  Update a target encounter role with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if encounter role not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the encounter role
    *description* | `String | Description for the encounter role
    

    
## Delete an encounter role

```console
DELETE /encounterrole/:target_encounter_role_uuid?purge=true
```
* Delete or Void a target encounter role by its UUID. Returns a `404 Not Found` status if encounter role not exists. If the user is
 not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

