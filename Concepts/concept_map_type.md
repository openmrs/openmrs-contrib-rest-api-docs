# Concept Map Type

## Overview

* Concept Mappings are added to facilitate managing concept dictionaries and point to other concepts which have the same meaning. 
Mappings are useful when you need to receive or send information to external systems, letting you define how your system's 
concepts relate to external concepts such as standardized medical vocabularies (e.g., ICD, LOINC, SNOMED). 
  
* For example, add a mapping to a concept in the MCL dictionary. You can save the concept now and create some answers.

* Repeat the steps and create the concepts PLANNING PREGNANCY and CURRENTLY PREGNANT of Class Finding and Datatype Boolean. 
The last possible answer will be OTHER of Class Misc and Datatype N/A. After creating three new concepts, you can edit 
ANTENATAL VISIT REASON and add them as answers.

## Available operations. 

1. [List concept_map types](#list-concept-map-types)
2. [Create a concept_map_type](#create-a-concept-map-type)
3. [Update a concept_map type](#update-a-concept-map-type)
4. [Delete a concept_map type](#delete-a-concept-map-type)


### List concept map types

* #### List all non-retired concept map types.

    Quickly filter concept map types with a given search query.Returns a `404 Not Found` status if concept map type not exists. 
    If user not logged in to perform this action,a `401 Unauthorized` status returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of concept map Type.

    ```console
    GET /conceptmaptype?q="Search Query"
     ```

* #### List concept map type by UUID.

    Retrieve a concept map type by its UUID. Returns a `404 Not Found` status if concept map type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /conceptmaptype/:target_concept_map_type_uuid
    ```

### Create a concept map type

* To Create a concept map type you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept attribute type (Required)
    *description* | `String` | Description
    *isHidden* | `Boolean` | State to record concept map is hidden or not
    
    ```console
        POST /conceptmaptype
        {
          "name": "SAME-AS",
          "isHidden": false
        }
    ```
### Update a concept map type

*  Update a target concept map type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept map not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept attribute type (Required)
    *description* | `String` | Description
    *isHidden* | `Boolean` | State to record concept map is hidden or not
    
    ```console
        POST /conceptmaptype
        {
          "name": "SAME-AS",
          "isHidden": true
        }
    ```

### Delete a concept map type

* Delete or Retire a target concept map type by its UUID. Returns a `404 Not Found` status if concept map not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /conceptmaptype/:target_concept_map_type_uuid?purge=true
     ```
