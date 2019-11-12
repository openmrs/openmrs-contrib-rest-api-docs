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

* Fetch all non-retired roles that match any specified parameters otherwise fetch all non-retired roles. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of order

    ```console
    GET /order?q=penicillin
     ```

* #### List a particular order

    Retrieve a particular order.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ```console
    GET /order/:target_order_uuid
    ```

### Create an order

* To create a role you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounter* | `Encounter UUID` | the encounter for this order
    *orderType* | `String` | the type of the order
    *action* | `String` | the action for the order
    *accessionNumber* | `String` | 
    *patient* | `Patient UUID` | the patient for the order
    *concept* | `Concept UUID` | the concept of the order
    *previousNumber* | `String` | the link to the previous order
    *instructions* | `String` | the instructions for the order
    *urgency* | `Urgency` | the level of urgency of the order
    *dateActivated* | `Date` | the start date of the order
    *dateStopped* | `Date` | the date of discontinuation

    ```console
        POST /order
        {
          "encounter": "69f83020-caf2-4c9e-bca7-89b8e62b52e1",
          "action": "new",
          "urgency": "ROUTINE",
          "patient": "070f0120-0283-4858-885d-a20d967729cf",
          "dateActivated": "2018-10-16 12:08:43"
        }
    ```
    
### Update an order

* Update an order with given UUID, this method only modifies properties in the request. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounter* | `Encounter UUID` | the encounter for this order
    *orderType* | `String` | the type of the order
    *action* | `String` | the action for the order
    *accessionNumber* | `String` | 
    *patient* | `Patient UUID` | the patient for the order
    *concept* | `Concept UUID` | the concept of the order
    *previousNumber* | `String` | the link to the previous order
    *instructions* | `String` | the instructions for the order
    *urgency* | `Urgency` | the level of urgency of the order
    *dateActivated* | `Date` | the start date of the order
    *dateStopped* | `Date` | the date of discontinuation

    ```console
        POST /order/:target_order_uuid
        {
          "encounter": "69f83020-caf2-4c9e-bca7-89b8e62b52e1",
          "action": "new",
          "urgency": "ROUTINE",
          "patient": "070f0120-0283-4858-885d-a20d967729cf",
          "dateStopped": "2019-03-12 11:48:23"
        }
    ```

### Delete an order

* Delete or Retire an order by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’.Purging will attempt to irreversibly remove the attribute type from the system. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

    ```console
        DELETE /order/:target_order_uuid?purge=true
     ```