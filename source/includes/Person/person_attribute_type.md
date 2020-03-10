# Person Attribute Type

## Person Attribute Type Overview

* Person attributes provide a mechanism for implementations to add custom attributes to their person records. A Person Attribute Type defines one of these custom attributes, including its data type and search behavior.

* For example, creating a Person Attribute Type for civil status (whether or not someone is single or married) would allow an implementation to record this information for each person in their system.

## Available operations.

1. [List person attribute types](#list-person-attribute-types)
2. [Create a person attribute type](#create-a-person-attribute-type)
3. [Update a person attribute type](#update-a-person-attribute-type)
4. [Delete a person attribute type](#delete-a-person-attribute-type)


## List person attribute types

* ### List all non-retired person attribute types.

    Quickly filter person attribute types with a given search query. If the request is not authenticated or the authenticated user does not have appropriate permissions, a `401 Unauthorized` status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter person attributes by its name(partial search is not supported)

```console
GET /personattributetype?q=race
 ```

* ### Get person attribute type by UUID.

    Retrieve a person attribute type by its UUID. Returns a `404 Not Found` status if the person attribute type does not exist. If the
    user not logged in to  perform this action, a `401 Unauthorized` status is returned.

```console
GET /personattributetype/:target_person_attribute_type_uuid
```

## Create a person attribute type

* To Create a person attribute type you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the person attribute type (Required)
    *description* | `String` | Description (Required)
    *format* | `Java Class` | the Java class the PersonAttributeType  
    *foreignKey* | `Number` | the internal identifier (foreign key) to a Concept that defines the possible values for this attribute
    *sortWeight* | `Number` | the order this PersonAttributeType will appear in when searched
    *searchable* | `Boolean` | true if this person attributes should be used to find patients. The default is false
    *editPrivilege* | `JSON Object` | the privilege required to make changes to this type

```console
POST /personattributetype
{
    "name": "Edit Civil Status",
    "description": "Able to manage the civil status of persons",
    "format": "org.openmrs.Concept",
    "foreignKey": 1054,
    "searchable": false,
    "editPrivilege": {
        "name": "Super User",
        "description": "Change and update the person attribute type"
    }
}
```
## Update a person attribute type

*  Update a target person attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status if the person attribute does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the person attribute type (Required)
    *description* | `String` | Description (Required)
    *format* | `Java Class` | the Java class the PersonAttributeType  
    *foreignKey* | `Number` | the internal identifier (foreign key) to a Concept that defines the possible values for this attribute
    *sortWeight* | `Number` | the order this PersonAttributeType will appear in when searched
    *searchable* | `Boolean` | true if this person attributes should be used to find patients. The default is false
    *editPrivilege* | `JSON Object` | the privilege required to make changes to this type

```console
POST /personattributetype
{
    "name": "Edit Civil Status",
    "description": "Able to manage the civil status of persons",
    "format": "org.openmrs.Concept",
    "foreignKey": 1054,
    "searchable": true,
    "editPrivilege": {
        "name": "Super User",
        "description": "Change and update the person attribute type"
    }
}
```

## Delete a person attribute type

* Delete or Retire a person attribute type by its UUID. Returns a `404 Not Found` status if the person attribute type does not
 exist. If the user is not logged in to  perform this action, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

```console
DELETE /personattributetype/:target_person_attribute_type_uuid?purge=true
```
