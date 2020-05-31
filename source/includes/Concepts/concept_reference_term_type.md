# Concept Reference Term

## Overview

* Concept reference terms represent terms within external vocabularies (typically standardized terminologies like SNOMED, ICD, LOINC, etc.). OpenMRS concept can be mapped to these reference terms through [concept mappings](concept_mapping.md). 
  
## Available operations. 
1.  [List concept reference terms](#list-concept-reference-terms)
2.  [Create a concept reference term](#create-a-concept-reference-term)
3.  [Update a concept reference term](#update-a-concept-reference-term)
4.  [Delete a concept reference term](#delete-a-concept-reference-term)

### List concept reference terms

* #### List all concepts reference terms.

    Quickly filter concept reference term with given query parameters. Returns a `404 Not Found` status if concept reference term type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *codeOrName* | `String` |  Represents a name from a standard medical code
    *source* | `String` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (i.e., LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc.), but the concept source can also be a custom (i.e., org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database

    ```console
    GET /conceptreferenceterm?
      codeOrName=274663001
     ```

* #### Query concept reference term by UUID.

    Retrieve a concept reference term by its UUID. Returns a `404 Not Found` status if concept reference term not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /conceptreferenceterm/:target_concept_reference_term_type_uuid
    ```

### Create a concept reference term

* To Create an concept reference term, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the concept reference term
    *description* | `String` | A concept datatype prescribes the structured format by which you desire the data to be represented. In simple terms, the data type defines the type of data that the concept is intended to collect
    *code* | `String` | Represents a name from a standard medical code (required)
    *conceptSource* | `target_concept_source_UUID` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (i.e., LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc.), but the concept source can also be a custom (i.e., org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept reference term type

    ```console
        POST /conceptreferenceterm
        {
          "code": "274663001",
          "conceptSource": "1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD",
          "version": "1.0.0"
        }
    ```
### Update a concept reference term

*  Update a target concept reference term with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept reference term not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the concept reference term
    *description* | `String` | A concept datatype prescribes the structured format by which you desire the data to be represented. In simple terms, the datatype defines the type of data that the concept is intended to collect
    *code* | `String` | Represents a name from a standard medical code (required)
    *conceptSource* | `target_concept_source_UUID` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (i.e., LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc.), but the concept source can also be a custom (i.e., org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept reference term type

    ```console
        POST /conceptreferenceterm/:target_concept_reference_term_type_uuid
        {
          "code": "274663001",
          "conceptSource": "1ADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD",
          "version": "1.0.1"
        }
    ```

### Delete a concept reference term

* Delete or retire a target concept reference term by its UUID. Returns a `404 Not Found` status if concept reference term not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

    ```console
        DELETE /conceptreferenceterm/:target_concept_reference_term_type_uuid?purge=true
     ```
