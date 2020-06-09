# Providers 

## Provider Overview

* A Provider is a person who provides care or services to patients. A provider may be a clinician like a doctor or a nurse, 
a social worker, or a lab tech. Generally speaking, any healthcare worker that a patient can have an encounter with is a provider.

* Providers may have full records in OpenMRS as persons, or they may just be a simple name and ID number.
 
## Sub Resource types of Provider

## Provider Attribute.

* If you wish to record extra information about providers, you can create Provider Attributes.

* Provider attributes exist specifically to allow implementations to extend the data model.

## Available operations for Provider. 

1. [List providers](#list-providers)
2. [Create a provider](#create-a-provider)
3. [Update a provider](#update-a-provider)
4. [Delete a provider](#delete-a-provider)
5. [List provider attribute sub resource](#list-provider-attribute-sub-resources)
6. [Create provider attribute sub resource with properties](#create-provider-attribute-sub-resource-with-properties)
7. [Update provider attribute sub resource](#update-provider-attribute-sub-resource)
6. [Delete provider attribute sub resource](#delete-provider-attribute-sub-resource)


## List providers

* ### List all non-retired providers.
    
    Quickly filter providers with given query parameters. Returns a `404 Not Found` status if provider not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Get provider by name
    
```console
GET /provider?
q=clerk
```
    
* ### Query provider by UUID.

    Retrieve a provider by its UUID. Returns a `404 Not Found` status if provider not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
```console
GET /provider/:target_provider_uuid
```
   
## Create a provider

* To Create a provider, you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *person* | `Person UUID` | Target person who will be a provider for OpenMRS (required)
    *identifier* | `String` | Value of the identifier.Identifier is used to virtually group providers in to groups (required)
    *attributes* | `Array[]: Attribute` |  List of provider attributes 
    *retired* | `Boolean` | Retired status for the provider.
    

```console
POST /provider
{
  "person": "007037a0-0500-11e3-8ffd-0800200c9a66",
  "identifier": "doctor",
  "attributes": [
    {
      "attributeType": "target_attributeType_uuid",
      "value": "value_for_attribute"
    }
  ],
  "retired": false
}
```
## Update a provider

*  Update a target provider with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if provider not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *person* | `Person UUID` | Target person who will be a provider for OpenMRS (required)
    *identifier* | `String` | Value of the identifier.Identifier is used to virtually group providers in to groups (required)
    *attributes* | `Array[]: Attribute` |  List of provider attributes 
    *retired* | `Boolean` | Retired status for the provider.
    
```console
POST /provider/:target_provider_uuid
{
  "person": "007037a0-0500-11e3-8ffd-0800200c9a66",
  "identifier": "doctor",
  "attributes": [
    {
      "attributeType": "target_attributeType_uuid",
      "value": "value_for_attribute"
    }
  ],
  "retired": false
}
```
    
## Delete a provider

* Delete or retire a target provider by its UUID. Returns a `404 Not Found` status if provider not exists. If the user is logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

```console
DELETE /provider/:target_provider_uuid?purge=true
```

## List provider attribute subresources

* ### List all provider attribute subresources for a provider.

    Retrieve all **provider attribute** subresources of a **provider** resource by target_provider_uuid. Returns a 
    `404 Not Found` status if provider attribute not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

```console
GET /provider/:target_provider_uuid/attribute 
```

* ### List provider attribute subresources by it's UUID and parent provider UUID.
    
     Retrieve a **provider attribute** subresources of a **provider** resource. Returns a `404 Not Found` status if the provider attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
```console
GET /provider/:target_provider_uuid/attribute/:target_provider_attribute_uuid
```

## Create a provider attribute sub resource with properties

* To Create an attribute subresource for a specific provider resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type (required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (required)

```console
POST provider/:target_provider_uuid/attribute 
{
  "attributeType": "target_provider_attribute_type_uuid",
  "value": "New provider"
}
```
## Update provider attribute subresource

* Updates a provider attribute subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if the provider attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *parent_uuid* | `Provider UUID` | Target provider resource UUID
    *uuid* | `Provider_Attribute UUID` | Target provider attribute resource UUID

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute

```console
POST provider/:target_provider_uuid/attribute/:target_provider_attribute_uuid
{
    "attributeType": "target_provider_attribute_type_uuid",
    "value": "New provider"
}
```

## Delete provider attribute subresource

* Delete or Retire a target provider attribute subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
 If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’. Purging will attempt to remove the provider attribute type from the system irreversibly. Provider attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

```console
DELETE /provider/:target_provider_uuid/attribute/:target_provider_attribute_uuid
```
