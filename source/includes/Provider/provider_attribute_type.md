# Provider Attribute Type

## Provider Attribute Overview

* If you wish to record extra information about providers, you can create Provider Attributes and assign them to Provider Types.

## Available operations for Provider Attribute type.

1. [List provider attribute types](#list-provider-attribute-types)
2. [Create a provider attribute type](#create-a-provider-attribute-type)
3. [Update a provider attribute type](#update-a-provider-attribute-type)
4. [Delete a provider attribute type](#delete-a-provider-attribute-type)


## List provider attribute types

* ### List all non-retired provider attribute types.

    Quickly filter provider attribute types with a given search query. Returns a `404 Not Found` status if the provider attribute type not exists.
    If user not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of provider attribute type.

```console
GET /providerattributetype?q="Search Query"
 ```

* ### List provider attribute type by UUID.

    Retrieve a provider attribute type by its UUID. Returns a `404 Not Found` status if the provider attribute type not exists. 
    If user not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

```console
GET /providerattributetype/:target_provider_attribute_type_uuid
```

## Create a provider attribute type

* To Create a provider attribute type you need to specify below attributes in the request body. If user not authenticated or 
the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the provider attribute type (Required)
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single provider. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single provider (e.g., use 1 to prevent an attribute from being added to a provider multiple times)
    *preferredHandlerClassname* | `Handler` | Specifies the Java class to be used when handling this provider attribute type. The java class must implement [`CustomDataTypeHandler`(https://docs.openmrs.org/doc/org/openmrs/customdatatype/CustomDatatypeHandler.html). If not specified, the system will try to choose the best handler for the chosen datatype.
    *datatypeConfig* | `String` | Provides ability to define custom data types configuration for openMRS
    *handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list and this configuration would tell the handler the possible choices in the list for this specific attribute type

```console
POST /providerattributetype
{
  "name": "Provider Location",
  "description": "This attribute type will record the loication of the provider",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 1,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": "dafault"
}
```

## Update a provider attribute type

*  Update a target provider attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status if the provider attribute not exists. If user not authenticated or the authenticated user does not have appropriate permissions, 
a 401 Unauthorized status is returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the provider attribute type
    *description* | `String` | Description (Required)
    *datatypeClassname* | `CustomDataType Resource` | Data type for the attribute type resource. OpenMRS provides **Custom data type resource** which gives flexibility to select the data type accordingly (Required)
    *minOccurs* | `Number` | Minimum number of times this value can be specified for a single provider. Use `0` or `1` as the default value (Required)
    *maxOccurs* | `Number` | Maximum number of times this value can be specified for a single provider (e.g., use 1 to prevent an attribute from  being added to a provider multiple times)
    *preferredHandlerClassname* | `Handler` | Specifies the Java class to be used when handling this provider attribute type. The java class must implement [`CustomDataTypeHandler`(https://docs.openmrs.org/doc/org/openmrs/customdatatype/CustomDatatypeHandler.html). If not specified, the system will try to choose the best handler for the chosen datatype.
    *datatypeConfig* | `String` | Provides ability to define custom data types configuration for openMRS
    *handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list and this configuration would tell the handler the possible choices in the list for this specific attribute type

```console
POST /providerattributetype/:target_provider_attribute_type_uuid
{
  "name": "Provider Location",
  "description": "This attribute type will record the loication of the provider",
  "datatypeClassname": "org.openmrs.customdatatype.datatype.LongFreeTextDatatype",
  "minOccurs": 0,
  "maxOccurs": 2,
  "datatypeConfig": "default",
  "preferredHandlerClassname": "org.openmrs.web.attribute.handler.LongFreeTextTextareaHandler",
  "handlerConfig": "dafault"
}
```

## Delete a provider attribute type

* Delete or Retire a provider attribute type by its UUID. Returns a `404 Not Found` status if the provider attribute type not
 exists. If user not authenticated or the authenticated user does not have appropriate permissions, a 401 Unauthorized status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

```console
DELETE /providerattributetype/:target_provider_attribute_type_uuid?purge=true
```
