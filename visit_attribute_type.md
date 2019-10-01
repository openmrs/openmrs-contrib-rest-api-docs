# Visits Attribute Type

## Overview

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types. 

* For example, you might create attributes for "Followup Visit," or "Distance Patient Traveled."
 

## Available operations. 

1. [List visits attribute types](#list-visits-attribute-types)
2. [Create a visit attribute type](#create-a-visit-attribute-type)
3. [Update a visit attribute type](#update-a-visit-attribute-type)
4. [Delete a visit attribute type](#delete-a-visit-attribute-type)


### List visits attribute types

* #### List all non-retired visits attribute types.
    
    Quickly filter visit attribute types with a given search query. Returns a `404 Not Found` status if the visit attribute type not exists. 
    If the user not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Visit attribute type.

    ```console
    GET /visitattributetype?q="Search Query"
     ```
    
* #### List visit attribute type by UUID.

    Retrieve a visit attribute type by its UUID. Returns a `404 Not Found` status if visit attribute type not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /visitattributetype/:target_visit_attribute_type_uuid
    ```
   
### Create a visit attribute type

* To Create a visit attribute type you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type Classname of custom data type resource (Required)
    *minOccurs* | `Number` | No of minimum occurrence (Required)
    *maxOccurs* | `Number` | No of maximum occurrence
    *preferredHandlerClassname* | `Handler` | Handler sub resource of CustomDataType   
    *datatypeConfig* | `String` | Data type configuration   
    *handlerConfig* | `String` | Handler config for intiate
   
    ```console
        POST /visitattributetype
       {
         "name": "string",
         "description": "string",
         "datatypeClassname": "string",
         "minOccurs": 0,
         "maxOccurs": 0,
         "datatypeConfig": "string",
         "preferredHandlerClassname": "string",
         "handlerConfig": "string"
       }
    ```
### Update a visit attribute type

*  Update a target visit attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if visit attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_visit_attribute_type_uuid` | Target visit attribute type resource UUID
    
    #### Attributes

      Parameter | Type | Description
      --- | --- | ---
      *name* | `String` | Name of the visit attribute type (Required)
      *description* | `String` | Description (Required)
      *datatypeClassname* | `CustomDataType Resource` | Data type Classname of custom data type resource (Required)
      *minOccurs* | `Number` | No of minimum occurrence (Required)
      *maxOccurs* | `Number` | No of maximum occurrence
      *preferredHandlerClassname* | `Handler` | Handler sub resource of CustomDataType   
      *datatypeConfig* | `String` | Data type configuration   
      *handlerConfig* | `String` | Handler config for intiate
    
    ```console
        POST /visitattributetype/:target_visit_attribute_type_uuid
        {
          "name": "string",
          "description": "string",
          "datatypeClassname": "string",
          "minOccurs": 0,
          "maxOccurs": 0,
          "datatypeConfig": "string",
          "preferredHandlerClassname": "string",
          "handlerConfig": "string"
        }
    ```
    
### Delete a visit attribute type

* Delete or Retire a target visit attribute type by its UUID. Returns a `404 Not Found` status if visit attribute not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /visitattributetype/:target_visit_attribute_type_uuid?purge=true
     ```
