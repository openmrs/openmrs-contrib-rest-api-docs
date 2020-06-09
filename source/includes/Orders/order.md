# Order

## Order Overview

An **Order** represents a request from a provider such as a lab test, procedure, referral, etc.

For example, a provider could order a Complete Blood Count laboratory panel for a patient.

An Order only records an intention, not whether or not the action is carried out. The results of an Order are typically recorded later as Observations.

## Available operations for Order type.

1. [List orders](#list-orders)
2. [Create an order](#create-an-order)
3. [Update an order](#update-an-order)
4. [Delete an order](#delete-an-order)

## List orders

```console
GET /order?q=penicillin
```
* Fetch all non-retired orders that match any specified parameters otherwise fetch all non-retired orders. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `String` | Full or partial display name of order


### Get a particular order

```console
GET /order/:target_order_uuid
```
    Retrieve a particular order. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.


## Create an order


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
* To create a role, you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounter* | `Encounter UUID` | the encounter for this order
    *orderType* | `OrderType UUID` | the type of the order
    *action* | `String` | Possible actions are `NEW` (placing a new order), `REVISE` (revising an existing order), `DISCONTINUE` (request an active order to be stopped),`RENEW` (resume a prior order).
    *accessionNumber* | `String` | An optional identifier from the fulfiller (e.g., lab system) for the specimen or record associated with the order.
    *patient* | `Patient UUID` | the patient for the order
    *concept* | `Concept UUID` | UUID for the concept of the order; the item being requested (e.g., "serum creatinine")
    *previousNumber* | `String` | when orders are revised, this links to the previous revision of the order
    *instructions* | `String` | the instructions for the order
    *urgency* | `Urgency` | `ROUTINE` (carry out order according to standard procedures), 
`STAT` (carry out order immediately), `ON_SCHEDULED_DATE` 
(carry out order at a specific time)
    *dateActivated* | `Date` | the start date of the order
    *dateStopped* | `Date` | the date of discontinuation

    
## Update an order


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
* Update an order with given UUID, this method only modifies properties in the request. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *encounter* | `Encounter UUID` | the encounter for this order
    *orderType* | `OrderType UUID` | the type of the order
    *action* | `String` | Possible actions are `NEW` (placing a new order), `REVISE` (revising an existing order), `DISCONTINUE` (request an active order to be stopped),`RENEW` (resume a prior order).
    *accessionNumber* | `String` | An optional identifier from the fulfiller (e.g., lab system) for the specimen or record associated with the order.
    *patient* | `Patient UUID` | the patient for the order
    *concept* | `Concept UUID` | UUID for the concept of the order; the item being requested (e.g., "serum creatinine")
    *previousNumber* | `String` | when orders are revised, this links to the previous revision of the order
    *instructions* | `String` | the instructions for the order
    *urgency* | `Urgency` | `ROUTINE` (carry out order according to standard procedures), 
`STAT` (carry out order immediately), `ON_SCHEDULED_DATE` 
(carry out order at a specific time)
    *dateActivated* | `Date` | the start date of the order
    *dateStopped* | `Date` | the date of discontinuation

## Delete an order

```console
DELETE /order/:target_order_uuid?purge=true
```

* Delete or void an order by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’.Purging will attempt to remove the attribute type from the system irreversibly. Attribute types that have been used (i.e., are referenced from existing data) cannot be purged.

