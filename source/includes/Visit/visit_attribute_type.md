# Visits Attribute Type

## Visits Attribute Type Overview

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types. 

* For example, you might create attributes for "Followup Visit," or "Distance Patient Traveled."
 

## Available operations for Visits Attribute Type 

1. [List visits attribute types](#list-visits-attribute-types)
2. [Create a visit attribute type](#create-a-visit-attribute-type)
3. [Update a visit attribute type](#update-a-visit-attribute-type)
4. [Delete a visit attribute type](#delete-a-visit-attribute-type)


## List visits attribute types

* ### List all non-retired visits attribute types.
    
    Quickly filter visit attribute types with a given search query. Returns a `404 Not Found` status if the visit attribute type not exists.
     If the user not logged in to  perform this action, a `401 Unauthorized` status returned.
    
    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Visit attribute type.

```console
GET /visitattributetype?q="Search Query"
  ```
    
* ### List visit attribute type by UUID.

    Retrieve a visit attribute type by its UUID. Returns a `404 Not Found` status if the visit attribute type not exists. If the 
    user not logged in to  perform this action, a `401 Unauthorized` status returned.
    
```console
GET /visitattributetype/:target_visit_attribute_type_uuid
```
   
## Create a visit attribute type

* To Create a visit attribute type you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource.OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single visit.Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single visit (e.g., use 1 to prevent an attribute from being added to a visit multiple times)
    *preferredHandlerClassname* | `Handler` | Handler sub resource for the Custom Data Type used.Can optionally define a specific handler class want to use (otherwise the framework will choose the best handler for the chosen datatype).To find which handlers to use for the Custom DataType please refer here   
    *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
    *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs.This will help to identify the data type unambiguously which has been contained and will allow introspecting
   
```console
POST /visitattributetype
{
  "name": "Patient condition",
  "description": "This attribute type will record the health conditon of the patient",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 1,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": "dafault"
}
```
## Update a visit attribute type

*  Update a target visit attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if the visit attribute not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_visit_attribute_type_uuid` | Target visit attribute type resource UUID
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the visit attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource.OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single visit.Use `0` or `1` as the default value (Required) (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single visit (e.g., use 1 to prevent an attribute from being added to a visit multiple times)
    *preferredHandlerClassname* | `Handler` |  Handler sub resource for the Custom Data Type used.Can optionally define a specific handler class want to use (otherwise the framework will choose the best handler for the chosen datatype).To find which handlers to use for the Custom DataType please refer here   
    *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
    *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs.This will help to identify the data type unambiguously which has been contained and will allow introspecting
    
```console
POST /visitattributetype/:target_visit_attribute_type_uuid
{
  "name": "Patient condition modified",
  "description": "This attribute type will record the health conditon of the patient",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 2,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": "dafault"
}
```
    
## Delete a visit attribute type

* Delete or Retire a target visit attribute type by its UUID. Returns a `404 Not Found` status if the visit attribute type not
 exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

```console
DELETE /visitattributetype/:target_visit_attribute_type_uuid?purge=true
```
