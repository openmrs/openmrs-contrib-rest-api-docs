# Visits Type

## Visits Type Overview

* A Visit Type is a name and description of a kind of visit. 

* Every visit has a type. You should create visit types that match how your health site classifies visits, such as 
"Outpatient," "Hospitalization," "Dental," "Patient Education," or "TB Clinic.".

* It is mandatory to set up at least one visit type.

* Visit types will be shown as dropdown options when creating or editing a patient in Registration. 

* Visit types can be added via the OpenMRS admin screen(Administration > Visits > Manage Visit Types) or via SQL scripts. 

## Available operations for Visits Type

1. [List visits types](#list-visits-types)
2. [Create a visit type](#create-a-visit-type)
3. [Update a visit type](#update-a-visit-type)
4. [Delete a visit type](#delete-a-visit-type)


## List visits types

### List all non-retired visits types.

```console
GET /visittype?q="Search Query"
```
  
    Quickly filter visit types with a given search query. Returns a `404 Not Found` status if visit type not exists. 
    If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Visit Type.

    
### List visit type by UUID.

```console
GET /visittype/:target_visit_type_uuid
```
    Retrieve a visit type by its UUID. Returns a `404 Not Found` status if visit type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create a visit type

```console
POST /visittype
{
    "name": "Name for the visit type",
    "description": "Description for the visit type"
}
```
* To Create a visit type, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit type (Required)
    *description* | `Patient UUID` | Visit type resource UUID (Required)
   

## Update a visit type

```console
POST /type/:target_visit_type_uuid
{
    "name": "Modified name for the visit type",
    "description": "Modified description for the visit type"
}
```
*  Update a target visit type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if visit not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_visit_type_uuid` | Target visit type resource UUID
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit type (Required)
    *description* | `Patient UUID` | Visit type resource UUID (Required)
    
    
## Delete a visit type

```console
DELETE /visittype/:target_visit_type_uuid?purge=true
```
* Delete or Retire a target visit type by its UUID. Returns a `404 Not Found` status if visit not exists. If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

