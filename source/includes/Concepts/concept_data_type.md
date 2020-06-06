# Concept Data Type

## Concept Data Type Overview

* Concept Data type defines the structured format you desired the data to be represented.

* The current types are as follows:
    
    1. Numeric – any data represented numerically, also allows you to classify critical values and units, e.g., age, height, and liters consumed per day
    2. Coded – allows answers to be only those provided, e.g., blood type can only be “A,” “B,” "AB," or “O.”
    3. Text – Open-ended responses
    4. N/A – the standard datatype for any non-query-like concepts (answers or things), e.g., symptoms, diagnoses, findings, anatomy, misc
    5. Document 
    6. Date – structured day, month, and year
    7. Time – structured time response
    8. DateTime – structured response including both the date and the time
    9. Boolean – checkbox response, e.g., yes or no queries
    10. Rule 
    11. Structured 


## Available operations for Concept Data Type. 

1. [List concept_data types](#list-concept-data-types)
4. [Delete a concept_data type](#delete-a-concept_data-type)


## List concept data types

### List all non-retired concept data types.

```console
GET /conceptdatatype"
```    
    Get concept data types. Returns a `404 Not Found` status if concept data type not exists. 
    If the user is not logged in to perform this action, a `401 Unauthorized` status returned. 

    
### Get concept data type by UUID.

```console
GET /conceptdatatype/:target_concept_data_type_uuid
```
    Retrieve a concept data type by its UUID. Returns a `404 Not Found` status if concept data type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    
## Delete a concept data type

```console
DELETE /conceptdatatype/:target_concept_data_type_uuid?purge=true
```
* Delete or retire a target concept data type by its UUID. Returns a `404 Not Found` 
  status if concept data not exists. If the user is not logged in to perform this action, 
  a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

