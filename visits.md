# Visits 

## Overview

* A Visit in OpenMRS represents precisely what it sounds like: a time when a patient is actively interacting with the 
the healthcare system, typically at a location.

* The metadata differentiating different types of visits is a Visit Type. Visit Types displayed in the user interface, 
also, can be searched against.

* A visit contains encounters, which store more granular data about treatments or services.

### Let’s look at an example.

At the Amani Clinic, a patient might typically check-in at registration, be seen by a doctor, and receives medication 
<b> dispensed </b> in the pharmacy. This would be recorded as one <b> visit </b> of <b> visit type of Outpatient </b>, and 
contain <b> three encounters (Registration, Consultation, and Dispensing) </b>.

## Sub Resource types

### Attribute.

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types.

* Visit attributes exists specifically to allow implementations to extend the data model.


## Available operations. 

1. [List visits](#list-visits)
2. [Create a visit](#create-a-visit)
3. [Update a visit](#update-a-visit)
4. [Delete a visit](#delete-a-visit)
5. [List attribute sub resource](list-attribute-sub-resources)
6. [Create attribute sub resource with properties](#create-an-attribute-sub-resource-with-properties)
7. [Update attribute sub resource](#update-attribute-sub-resource)
6. [Delete attribute sub resource](#delete-attribute-sub-resource)



### List visits

* #### List all non-retired visits.
    
    Quickly filter visits with given query parameters.Returns a `404 Not Found` status if visit not exists. If user not logged 
    in to perform this action,a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *patient* | `Patient UUID` | Get visits for this patient
    *location* | `Location UUID` | Get visits for this location
    *includeInactive* | `Boolean` | Active/Inactive status of visit
    *fromStartDate* | `Date (ISO8601 Long)` | Start date of the visit

    ```console
    GET /visit?
      includeInactive=true
      &fromStartDate=2016-10-08T04:09:23.000Z
      &patient=target_patient_uuid
      &location=target_location_uuid
     ```
    
* #### List visit by UUID.

    Retrieve a visit by its UUID. Returns a `404 Not Found` status if visit not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /visit/:target_visit_uuid
    ```
   
### Create a visit

* To Create a visit you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

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
### Update a visit

*  Update a target visit with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if visit not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_visit_uuid` | Target visit resource UUID
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Visit` | Visit resource with updated properties.
    
    ```console
        POST /visit/:target_visit_uuid
        -d  modified_visit_object
    ```
    
### Delete a visit

* Delete or Retire a target visit by its UUID. Returns a `404 Not Found` status if visit not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /visit/:target_visit_uuid?purge=true
     ```
### List attribute sub resources

* #### List all attribute sub resources for a visit.

    Retrieve all <b>attribute</b> sub resources of a  <b>visit</b> resource by target_visit_uuid.Returns a 
    `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

    ```console
        GET /visit/:target_visit_uuid/attribute 
    ```

* #### List attribute sub resources by it's UUID and parent visit UUID.
    
     Retrieve an <b>attribute</b> sub resources of a <b>visit</b> resource.Returns a 
     `404 Not Found` status if attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
    ```console
        GET /visit/:target_visit_uuid/attribute/:target_attribute_uuid
    ```
### Create an attribute sub resource with properties

* To Create an attribute sub resource for a specific visit resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Attribute_Type
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute
    
    ```console
        POST visit/:target_visit_uuid/attribute 
        {
          "attributeType": "target_attribute_type_uuid",
          "value": "value_for_the_attriute"
        }
    ```
 
 
### Update attribute sub resource

* Updates an attribute sub resource value with given uuid, this method will only modify value of the sub resource.Returns 
a `404 Not Found` status if attribute not exists.If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Attribute_Type resource UUID
    *updated value* | `Depends on Attribute_Type Selected` | Updated value for the attribute

    ```console
        POST visit/:target_visit_uuid/attribute/:target_attribute_uuid
        {
          "attributeType": "target_attribute_type_uuid",
          "value": "modified_attriute_value"
        } 
    ```
### Delete attribute sub resource

* Delete or Retire a target attribute sub resource by its UUID.Returns a `404 Not Found` status if attribute not exists. 
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
     ```console
        DELETE /visit/:target_visit_uuid/attribute/:target_attribute_uuid
     ```
