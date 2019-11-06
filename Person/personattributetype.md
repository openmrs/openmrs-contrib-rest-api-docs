# Person Attribute Type

## Overview

* A PersonAttributeType exists to group PersonAttribute objects together.

## Available operations.

1. [List person attribute types](#list-person-attribute-types)
2. [Create a person attribute type](#create-a-person-attribute-type)
3. [Update a person attribute type](#update-a-person-attribute-type)
4. [Delete a person attribute type](#delete-a-person-attribute-type)


### List person attribute types

* #### List all non-retired person attribute types.

    Quickly filter person attribute types with a given search query. Returns a `404 Not Found` status if the person attribute type not exists.
     If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /personattributetype
     ```

* #### List person attribute type by UUID.

    Retrieve a person attribute type by its UUID. Returns a `404 Not Found` status if the person attribute type not exists. If the
    user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /personattributetype/:target_person_attribute_type_uuid
    ```

### Create a person attribute type

* To Create a person attribute type you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the person attribute type (Required)
    *description* | `String` | Description (Required)
    *format* | `java.package.Class` | the Java class the PersonAttributeType  
    *foreignKey* | `Number` | the foreign key in the database that this PersonAttributeType references
    *sortWeight* | `Number` | the order this PersonAttributeType will appear in when searched
    *searchable* | `Boolean` | a Boolean denoting whether or not this PersonAttributeType can be searched for
    *editPrivilege* | `JSON Object` | the privileges required to make changes to this type


    ```console
        POST /personattributetype
        {
            "name": "Civil Status",
            "description": "Marriage Status of this person",
            "format": "org.openmrs.Concept",
            "foreignKey": 1054,
            "searchable": false,
            "editPrivilege": {
                "name": "Super User",
                "description": "Change and update the person attribute type"
            }
        }
    ```
### Update a person attribute type

*  Update a target person attribute type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status if the person attribute not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the person attribute type (Required)
    *description* | `String` | Description (Required)
    *format* | `java.package.Class` | the Java class the PersonAttributeType  
    *foreignKey* | `Number` | the foreign key in the database that this PersonAttributeType references
    *sortWeight* | `Number` | the order this PersonAttributeType will appear in when searched
    *searchable* | `Boolean` | a Boolean denoting whether or not this PersonAttributeType can be searched for
    *editPrivilege* | `JSON Object` | the privileges required to make changes to this type


    ```console
        POST /personattributetype
        {
            "name": "Civil Status",
            "description": "Employment Status of this person",
            "format": "org.openmrs.Concept",
            "foreignKey": 1054,
            "searchable": true,
            "editPrivilege": {
                "name": "Super User",
                "description": "Change and update the person attribute type"
            }
        }
    ```

### Delete a person attribute type

* Delete or Retire a person attribute type by its UUID. Returns a `404 Not Found` status if the person attribute type not
 exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

    ```console
        DELETE /personattributetype/:target_person_attribute_type_uuid?purge=true