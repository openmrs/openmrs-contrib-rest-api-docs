# Concept Source Type

## Overview

* A concept maps with the concept source type in openMRS. 

* Concept can have any number of mappings to any number of other vocabularies. 

* Other vocabularies are called "concept sources" in OpenMRS (ie. LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc), but the concept 
source can also be a custom (ie. org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). 

* Every concept can define a string for its mapping in any "concept source" defined in the database

## Available operations. 

1. [List concept_source types](#list-concept-source-types)
2. [Create a concept_source](#create-a-concept_source-type)
3. [Update a concept_source type](#update-a-concept_source-type)
4. [Delete a concept_source type](#delete-a-concept_source-type)


### List concept source types

* #### List all non-retired concept source types.
    
    Quickly filter concept source types with a given search query.Returns a `404 Not Found` status if concept source type not exists. 
    If user not logged in to perform this action,a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of concept source Type.

    ```console
    GET /conceptsource?q="Search Query"
     ```
    
* #### List concept source type by UUID.

    Retrieve a concept source type by its UUID. Returns a `404 Not Found` status if concept source type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /conceptsource/:target_concept_source_type_uuid
    ```
   
### Create a concept source type

* To Create a concept source type you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept source type (Required)
    *description* | `String` | Description for the concept source type resource (Required)
    *hl7Code* | `String` | The 5-20 character code defined for this source by governing bodies. Alternatively, this could be the "Implementation Id" code used by another OpenMRS installation to define its concepts and forms
    *uniqueId* | `String` | A globally unique id to for the concept source
   
    ```console
        POST /conceptsource
        {
          "name": "SNOMED CT",
          "description": "SNOMED Preferred mapping",
          "hl7Code": "SCT"
        }
    ```
### Update a concept source type

*  Update a target concept source  type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept source not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept source type
    *description* | `String` | Description for the concept source type resource
    *hl7Code* | `String` | The 5-20 character code defined for this source by governing bodies. Alternatively, this could be the "Implementation Id" code used by another OpenMRS installation to define its concepts and forms
    *uniqueId* | `String` | A globally unique id to for the concept source
    
    ```console
       POST /conceptsource
       {
         "name": "SNOMED CTS",
         "description": "SNOMED Preferred mapping",
         "hl7Code": "SCT"
       }
    ```
    
### Delete a concept source  type

* Delete or Retire a target concept source  type by its UUID. Returns a `404 Not Found` status if concept source not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /conceptsource/:target_concept_source_type_uuid?purge=true
     ```
