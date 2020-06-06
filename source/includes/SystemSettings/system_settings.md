# System Setting

## System Setting Overview

* System Settings are used to store module and system-wide settings. They primarily consist of a property name and a value and a description explaining how this property is being used

* System Settings are configuration variables that can be modified without restarting or recompiling the application. They're useful when module code needs to refer to a value that's unique to a particular installation, such as a concept ID number or a file path

* some examples : 
     * system-wide setting: `Default Location` which specifies the name of the location to use as a system default 
     * module-specific system setting: `Require Email as Username` is a system setting under the user module which accepts boolean type as a valid value 


## Available operations for systemsetting type.

1. [List System Settings](#list-system-settings)
2. [Create a System Setting](#create-a-system-setting)
3. [Update a System Setting](#update-a-system-setting)
4. [Delete a System Setting](#delete-a-system-setting)

## List System Settings

```console
GET /systemsetting?limit=5
```
* Fetch all non-retired System Settings that match any specified parameters otherwise fetch all non-retired System Settings. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *limit* | `integer`| use this parameter to limit the number of results to be returned 
    *startIndex*| `integer` | the offset where to start the query
    *v* | `String` | the required representation to return (i.e., ref, default, full or custom )
    *q* | `String` | the search query


### Get a particular System Setting

```console
GET /systemsetting/:target_systemsetting_uuid
```
    Retrieve a particular System Setting. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.


## Create a System Setting


```console
POST /systemsetting
{
  "property": "property name",
  "description": "dummy description",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "datatypeConfig": "default",
  "preferredHandlerClassname":"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler"
  "handlerConfig": "default",
  "value": "dummy value"
}
```
* To create a System Setting, you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *property* | `String` | the property name for this System Setting, names can be up to 255 chars, must be unique, and follow a convention of module ID followed by category & name lower camelCase separated by periods for e.g., addresshierarchy.allowFreetext
    *description* | `String` | a description for the usage of this property
    *datatypeClassname* | `String` | Data type for this System Setting.OpenMRS provides Custom data type resource, which gives the flexibility to select the data type accordingly             *datatypeConfig* | `String` | An optional identifier from the fulfiller (e.g., lab            *preferredHandlerClassname*  | `String` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise, the framework will choose the best handler for the chosen DataType)
    *handlerConfig*  | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting
    *value* | `String` | the value assigned to this system setting 
    
## Update a System Setting


```console
POST /systemsetting/:target_systemsetting_uuid
{
  "property": "property name",
  "description": "dummy description",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "datatypeConfig": "default",
  "preferredHandlerClassname":"org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler"
  "handlerConfig": "default",
  "value": "dummy value"
}
```
* Update a System Setting with given UUID, this method only modifies properties in the request. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *property* | `String` | the property name for this System Setting, names can be up to 255 chars, must be unique, and follow a convention of module ID followed by category & name lower camelCase separated by periods for e.g., addresshierarchy.allowFreetext
    *description* | `String` | a description for the usage of this property
    *datatypeClassname* | `String` | Data type for this System Setting.OpenMRS provides Custom data type resource, which gives flexibility to select the data type accordingly             *datatypeConfig* | `String` | An optional identifier from the fulfiller (e.g., lab            *preferredHandlerClassname*  | `String` | Handler subresource for the Custom Data Type used. Can optionally define a specific handler class wants to use (otherwise, the framework will choose the best handler for the chosen DataType)
    *handlerConfig*  | `String` | Allow the handler have any name and config it wants/needs. This will help to identify the data type unambiguously which has been contained and will allow introspecting
    *value* | `String` | the value assigned to this system setting  
    
## Delete a System Setting

```console
DELETE /systemsetting/:target_systemsetting_uuid?purge=true
```

* Delete or void a System Setting by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

