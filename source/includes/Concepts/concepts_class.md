# Concept Class

## Overview

* The concept's class provides a useful way to narrow down the scope of the information that the concept is intended to capture.  
In this way, the class is helpful for data extraction.  This classification details how a concept will be represented 
(i.e. as a question or an answer) when the information is stored.  OpenMRS contains several default classes to use when 
defining concepts, but implementation sites may also create additional custom concept classes for use. 

## Available operations. 

1. [List concept classes](#list-concept-classes)
2. [Create a concept class](#create-a-concept-class)
3. [Update a concept class](#update-a-concept-class)
4. [Delete a concept class](#delete-a-concept-class)


### List concept classes

* #### List all non-retired concept classes.

    List all concept classes with a given search query.Returns a `404 Not Found` status if concept classes not exists. 
    If user not logged in to perform this action,a `401 Unauthorized` status returned.

    ```console
    GET /conceptclass"
     ```

* #### List concept class type by UUID.

    Retrieve a concept class by its UUID. Returns a `404 Not Found` status if concept class type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /conceptclass/:target_concept_class_uuid
    ```

### Create a concept class

* To Create a concept class you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept class (Required)
    *description* | `String` | Description

    ```console
        POST /conceptclass
        {
          "name": "Procedure",
          "description": "Describes a clinical procedure"
        }
    ```
### Update a concept class

*  Update a target concept class with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept class not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept class (Required)
    *description* | `String` | Description

    ```console
        POST /conceptclass
        {
          "name": "Procedure",
          "description": "Describes a clinical procedure"
        }
    ```

### Delete a concept class

* Delete or Retire a target concept class  by its UUID. Returns a `404 Not Found` status if concept class not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /conceptclass/:target_concept_class_uuid?purge=true
     ```
