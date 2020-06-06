# Visits 

## Visits Overview 

* A Visit in OpenMRS represents precisely what it sounds like: a time when a patient is actively interacting with the 
the healthcare system, typically at a location.

* The metadata differentiating different types of visits is a Visit Type. Visit Types displayed in the user interface, also can be searched against.

* A visit contains encounters, which store more granular data about treatments or services.

## Let's look at an example of Visits

At the Amani Clinic, a patient might typically check-in at registration, be seen by a doctor, and receives medication 
<b> dispensed </b> in the pharmacy. This would be recorded as one <b> visit </b> of <b> visit type of Outpatient </b>, and 
contain <b> three encounters (Registration, Consultation, and Dispensing) </b>.

## Visits Sub Resource types

### Visits Attribute

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types.

* Visit attributes exists specifically to allow implementations to extend the data model.

## Available operations for Visits

1. [List visits](#list-visits)
2. [Create visit](#create-visit)
3. [Update visit](#update-visit)
4. [Delete visit](#delete-visit)
5. [List attribute subresource](#list-attribute-subresources)
6. [Create attribute subresource with properties](#create-an-attribute-subresource-with-properties)
7. [Update attribute subresource](#update-attribute-subresource)
6. [Delete attribute subresource](#delete-attribute-subresource)

## List visits
```console
GET /visit?
includeInactive=true
&fromStartDate=2016-10-08T04:09:23.000Z
&patient=target_patient_uuid
&location=target_location_uuid
```
* ### List all non-retired visits.
    
    Quickly filter visits with given query parameters. Returns a `404 Not Found` status if visit not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *patient* | `Patient UUID` | Get visits for this patient
    *location* | `Location UUID` | Get visits for this location
    *includeInactive* | `Boolean` | Active/Inactive status of visit
    *fromStartDate* | `Date (ISO8601 Long)` | Start date of the visit

```console
GET /visit/:target_visit_uuid
```    
* ### List visit by UUID.

    Retrieve a visit by its UUID. Returns a `404 Not Found` status if visit not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
      
## Create visit
 
```console
POST /visit
{
    "patient": "target_patient_uuid",
    "visitType": "target_visitType_uuid",
    "startDatetime": "2016-10-08T04:09:25.000Z",
    "location": "target_location_uuid",
    "indication": null,
    "encounters": [
    "target_encounter_uuid"
    ],
    "attributes": [
    {
        "attributeType": "target_attributeType_uuid",
        "value": "value_for_attribute"
    }
    ]
}
```
* To Create a visit you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.


    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *patient* | `Patient UUID` | Patient resource UUID
    *visitType* | `Patient UUID` | Visit type resource UUID
    *startDatetime* | `Date (ISO8601 Long)` | Start date of the visit
    *location* | `Location UUID` | Location resource UUID 
    *indication* | `string` | Any indication of the visit    
    *stopDatetime* | `Date (ISO8601 Long)` | End date of the vist    
    *encounters* | `Array[]: Encounter UUID` | Encounter resources UUID    
    *attributes* | `Array[]: Attribute` | List of visit attributes  
   
## Update visit

```console
POST /visit/:target_visit_uuid
-d  modified_visit_object
```
*  Update a target visit with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if visit not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_visit_uuid` | Target visit resource UUID
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Visit` | Visit resource with updated properties.
        
## Delete visit
```console
DELETE /visit/:target_visit_uuid?purge=true
```
* Delete or Retire a target visit by its UUID. Returns a `404 Not Found` status if visit not exists. If the user is not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

## List attribute subresources
```console
GET /visit/:target_visit_uuid/attribute 
```
* ### List all attribute subresources for a visit.

    Retrieve all <b>attribute</b> sub resources of a  <b>visit</b> resource by target_visit_uuid.Returns a 
    `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.
```console
GET /visit/:target_visit_uuid/attribute/:target_attribute_uuid
```
* ### List attribute subresources by it's UUID and parent visit UUID.
    
     Retrieve an <b>attribute</b> sub resources of a <b>visit</b> resource.Returns a 
     `404 Not Found` status if attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.

## Create an attribute subresource with properties
```console
POST visit/:target_visit_uuid/attribute 
{
    "attributeType": "target_attribute_type_uuid",
    "value": "value_for_the_attriute"
}
```
* To Create an attribute subresource for a specific visit resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute

## Update attribute subresource
```console
POST visit/:target_visit_uuid/attribute/:target_attribute_uuid
{
    "attributeType": "target_attribute_type_uuid",
    "value": "modified_attriute_value"
} 
```
* Updates an attribute subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Attribute_Type resource UUID
    *updated value* | `Depends on Attribute_Type Selected` | Updated value for the attribute

## Delete attribute subresource
```console
DELETE /visit/:target_visit_uuid/attribute/:target_attribute_uuid
```
* Delete or Retire a target attribute subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
