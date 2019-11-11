# Order

## Overview

An **Order** is an action that a provider requests be taken regarding a patient.

For example a provider could order a Complete Blood Count laboratory panel for a patient.

An Order only records an intention, not whether or not the action is carried out. The results of an Order are typically recorded later as Observations.

## Available operations.

1. [List orders](#list-orders)
2. [Create an order](#create-an-order)
3. [Update an order](#update-an-order)
4. [Delete an order](#delete-an-order)


### List orders

* Fetch all non-retired roles that match any specified parameters otherwise fetch all non-retired roles. Returns `404 Not Found` status if the order does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of order

    ```console
    GET /order
     ```

* #### List a particular order.

    Retrieve a particular order. Returns `404 Not Found` status if the order does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    ```console
    GET /role/:target_role_uuid
    ```

### Create a role

* To create a role you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role(Required)
    *description* | `String` | Description of the role(Required)
    *privileges* | `Array[] : privileges` | An array of the privilege resource
    *inheritedRoles* | `Array[] : inheritedRoles` | An array of the inheritedRoles type

    ```console
        POST /role
        {
          "name": "Clinician",
          "description": "A provider assisting the Lead Surgeon.",
          "privileges": [{
              "name": "Delete Patients",
              "description": "The one having this privilege can to delete the patients."
          }]
        }
    ```
### Update a role

*  Update a role with given UUID, this method only modifies properties in the request. Returns a `404 Not Found`
status if the role deos not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the role (Required)
    *description* | `String` | Description of the role (Required)
    *privileges* | `Array[] : privileges` | An array of the privilege resource
    *inheritedRoles* | `Array[] : inheritedRoles` | An array of the inheritedRoles type

    ```console
        POST /role
        {
          "name": "Assisting Surgeon",
          "description": "A surgeon who assisted the Lead Surgeon"
        }
    ```

### Delete a role

* Delete or Retire a role by its UUID. Returns a `404 Not Found` status if the role not
 exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

    ```console
        DELETE /role/:target_role_uuid?purge=true
     ```