# Location Attribute Type

## Location Attribute Overview

* If you wish to record extra information about locations, you can create Location Attributes and assign them to Location Types. 

## Available operations for Location Attribute 

1. [List location attribute types](#list-location-attribute-types)
2. [Create a location attribute type](#create-a-location-attribute-type)
3. [Update a location attribute type](#update-a-location-attribute-type)
4. [Delete a location attribute type](#delete-a-location-attribute-type)


### List location attribute types

### List all non-retired location attribute types.

```console
GET /locationattributetype?q="humidity"
```
    Quickly filter location attribute types with a given search query. Returns a `404 Not Found` status if the location attribute type not exists.
     If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Location attribute type.


### List location attribute type by UUID.

```console
GET /locationattributetype/:target_location_attribute_type_uuid
```
    Retrieve a location attribute type by its UUID. Returns a `404 Not Found` status if the location attribute type not exists. If the 
    user not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a location attribute type

```console
POST /locationattributetype
{
  "name": "humidity",
  "description": "This attribute type will record the humidity of the location",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 1,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": "dafault"
}
```
* To Create a location attribute type, you need to specify below attributes in the request body. If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the location attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single location. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single location (e.g., use 1 to prevent an attribute from being added to a location multiple times)
    *preferredHandlerClassname* | `Handler` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise the framework will choose the best handler for the chosen DataType,). To find which handlers to use for the Custom DataType, please refer here   
    *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
    *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting

## Update a location attribute type

```console
POST /locationattributetype/:target_location_attribute_type_uuid
{
  "name": "humidity",
  "description": "This attribute type will record the humidity of the location"",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 2,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": "dafault"
}
```
*  Update a target location attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if the location attribute not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_location_attribute_type_uuid` | Target location attribute type resource UUID

    ### Attributes

      Parameter | Type | Description
      --- | --- | ---
      *name* | `String` | Name of the location attribute type (Required)
      *description* | `String` | Description (Required)
      *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
      *minOccurs* | `Number` | Minimum number of times this value can be specified for a single location. Use `0` or `1` as the default value (Required)
      *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single location (e.g., use 1 to prevent an attribute from being added to a location multiple times)
      *preferredHandlerClassname* | `Handler` |  Handler subresource for the Custom Data Type used. Can optionally define a specific handler class want to use (otherwise the framework will choose the best handler for the chosen DataType). To find which handlers to use for the Custom DataType, please refer here   
      *datatypeConfig* | `String` | Allow the data type have any name and config it wants/needs.
      *handlerConfig* | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting



## Delete a location attribute type

```console
DELETE /locationattributetype/:target_location_attribute_type_uuid?purge=true
```
* Delete or Retire a target location attribute type by its UUID. Returns a `404 Not Found` status if the location attribute type not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’. Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

