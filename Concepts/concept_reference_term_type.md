# Concepts Reference Term Type

## Overview

* A concept term defines a medical coding term or OpenMRS concept dictionary term that could be mapped to a concept. 
A medical coding term is used to represent a name from a standard medical code (ie.  SNOMED, ICD10, LOINC, etc). OpenMRS 
concept dictionary terms are used to refer to concepts by concept_id or name of a concept in the concept dictionary (ie. CIEL, PIH, AMPATH, etc.).  
  
## Available operations. 
1.  [List concept reference term types](#list-concept-reference-term-types)
2.  [Create a concept reference term type](#create-a-concept-reference-term-type)
3.  [Update a concept reference term type](#update-a-concept-reference-term-type)
4.  [Delete a concept reference term type](#delete-a-concept-reference-term-type)

### List concept reference term types

* #### List all concepts reference term types.

    Quickly filter concept reference term types with given query parameters.Returns a `404 Not Found` status if concept 
    reference term type not exists. If user not logged in to perform this action,a `401 Unauthorized` status returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of oncepts reference term type object
    *codeOrName* | `String` |  Represents a name from a standard medical code
    *source* | `String` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (ie. LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc), but the concept source can also be a custom (ie. org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database

    ```console
    GET /conceptreferenceterm?
      codeOrName=274663001
     ```

* #### Query concept reference term type by UUID.

    Retrieve an concept reference term type by its UUID. Returns a `404 Not Found` status if concept reference term type not 
    exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /conceptreferenceterm/:target_concept_reference_term_type_uuid
    ```

### Create a concept reference term type

* To Create an concept reference term type you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the concept reference term type
    *description* | `String` | A concept datatype prescribes the structured format by which you desire the data to be represented. In simple terms, the datatype defines the type of data that the concept is intended to collect
    *code* | `String` | Represents a name from a standard medical code (required)
    *conceptSource* | `target_concept_source_UUID` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (ie. LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc), but the concept source can also be a custom (ie. org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept reference term type

    ```console
        POST /conceptreferenceterm
        {
          "code": "274663001",
          "conceptSource": "1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD",
          "version": "1.0.0"
        }
    ```
### Update a concept reference term type

*  Update a target concept reference term type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the concept reference term type
    *description* | `String` | A concept datatype prescribes the structured format by which you desire the data to be represented. In simple terms, the datatype defines the type of data that the concept is intended to collect
    *code* | `String` | Represents a name from a standard medical code (required)
    *conceptSource* | `target_concept_source_UUID` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (ie. LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc), but the concept source can also be a custom (ie. org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept reference term type

    ```console
        POST /conceptreferenceterm/:target_concept_reference_term_type_uuid
        {
          "code": "274663001",
          "conceptSource": "1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD",
          "version": "1.0.1"
        }
    ```

### Delete a concept reference term type

* Delete or retire a target concept reference term type by its UUID. Returns a `404 Not Found` status if concept reference 
term type not exists.If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

    ```console
        DELETE /conceptreferenceterm/:target_concept_reference_term_type_uuid?purge=true
     ```
