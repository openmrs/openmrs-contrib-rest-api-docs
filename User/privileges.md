# Privilege

## Overview

A **Privilege** is an authorization to perform a particular action in the system. The list of available privileges are defined by the core system and by add-on modules (for example, **Delete Patients** and **Manage Encounter Types**), but you need to configure which roles have which privileges while you are configuring your system.

## Available operations.

1. [List privilege](#list-privileges)
2. [Create a privilege](#create-a-privilege)
3. [Update a privilege](#update-a-privilege)
4. [Delete a privilege](#delete-a-privilege)


### List privilege

* Fetch all non-retired privileges that match any specified parameters otherwise fetch all non-retired privileges. Returns a `200 OK` status with the privilege response. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /privilege
     ```

* #### List privileges by UUID.

    Retrieve a privilege by its UUID. Returns a `404 Not Found` status if the privilege not exists. If the
    user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /privilege/:target_privilege_uuid
    ```

### Create a privilege

* To create a privilege you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the privilege(Required)
    *description* | `String` | Description of the privilege(Required)

    ```console
        POST /privilege
        {
            "name": "Delete Patients",
            "description": "A privilege or permission to delete patients"
        }
    ```
### Update a privilege

*  Update a privilege with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status if the privilege deos not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *description* | `String` | Description of the privilege (Required)

    ```console
        POST /privilege/:target_privilege_uuid
        {
          "description": "A user who can delete all the encounter types"
        }
    ```

### Delete a privilege

* Delete or Retire a privilege by its UUID. Returns a `404 Not Found` status if the privilege not
 exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

    ```console
        DELETE /privilege/:target_privilege_uuid?purge=true
     ```