# Role

## Role Overview

A **Role** represents a group of privileges in the system. Roles may inherit privileges from other roles, and users may have one or more roles.

## Available operations for Role.

1. [List roles](#list-roles)
2. [Create a role](#create-a-role)
3. [Update a role](#update-a-role)
4. [Delete a role](#delete-a-role)


## List roles

* Fetch all the roles that match any specified parameters otherwise fetch all roles. Returns a `200 OK` status with the role response. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

```console
GET /role
 ```

* ## Get a role by UUID.

    Retrieve a role by its UUID. Returns a `404 Not Found` status if the role not exists. If the
    user not logged in to  perform this action, a `401 Unauthorized` status returned.

```console
GET /role/:target_role_uuid
```

## Create a role

* To create a role you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *privileges* | `Array[] : privileges` | An array of the privilege resource
    *inheritedRoles* | `Array[] : inheritedRoles` | An array of the inheritedRoles type

```console
POST /role
{
  "name": "Clinician",
  "description": "A provider assisting the Lead Surgeon.",
  "privileges": [{
      "name": "Delete Patients",
      "description": "Able to delete patients"
  }]
}
```
## Update a role

*  Update a role with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status if the role deos not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *privileges* | `Array[] : privileges` | An array of the privilege resource
    *inheritedRoles* | `Array[] : inheritedRoles` | An array of the inheritedRoles type

```console
POST /role
{
  "name": "Configures Forms",
  "description": "Manages forms and attaches them to the UI"
}
```

## Delete a role

* Delete a role by its UUID. Returns a `404 Not Found` status if the role not
 exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | must be `true` to delete the role from the system; if `false`, the request will have no effect

```console
DELETE /role/:target_role_uuid?purge=true
```
