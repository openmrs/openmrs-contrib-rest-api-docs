# Concept Data Type

## Overview

* Concept Data type defines the structured format you desired the data to be represented as.

* The current types are as follows:
    
    1. Numeric – any data represented numerically, also allows you to classify critical values and units, e.g. age, height, and liters consumed per day.
    2. Coded – allows answers to be only those provided, e.g. Blood type can only be “A,” “B,” and “O”
    3. Text – Open ended responses
    4. N/A – the standard datatype for any non-query-like concepts, e.g. symptoms, diagnoses, findings, anatomy, misc, etc.
    5. Document 
    6. Date – structured day, month, and year
    7. Time – structured time response
    8. DateTime – structured response including both the date and the time
    9. Boolean – checkbox response, e.g. yes or no queries
    10. Rule 
    11. Structured 


## Available operations. 

1. [List concept_data types](#list-concept-data-types)
4. [Delete a concept_data type](#delete-a-concept_data-type)


### List concept data types

* #### List all non-retired concept data types.
    
    Get concept data types.Returns a `404 Not Found` status if concept data type not exists. 
    If user not logged in to perform this action,a `401 Unauthorized` status returned. 

    ```console
    GET /conceptdatatype"
     ```
    
* #### Get concept data type by UUID.

    Retrieve a concept data type by its UUID. Returns a `404 Not Found` status if concept data type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /conceptdatatype/:target_concept_data_type_uuid
    ```
    
### Delete a concept data type

* Delete or Retire a target concept data type by its UUID. Returns a `404 Not Found` status if concept data not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /conceptdatatype/:target_concept_data_type_uuid?purge=true
     ```
