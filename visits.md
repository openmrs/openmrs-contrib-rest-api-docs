# Visits 

### Overview

* A Visit in OpenMRS represents exactly what it sounds like: a time period when a patient is actively interacting with the 
healthcare system, typically at a location.

* The metadata differentiating different types of visits is a Visit Type.Visit Types are displayed in the user interface, 
and can be searched against.

* A visit contains encounters, which store more granular data about treatments or services.

##### Let’s look at an example.

At the Amani Clinic, a patient might typically check-in at registration, be seen by a doctor, and receives medication 
<b> dispensed </b> in the pharmacy. This would be recorded as one <b> visit </b> of <b> visit type of Outpatient </b>, and 
contain <b> three encounters (Registration, Consultation, and Dispensing) </b>.

### Sub Resourse types.

#### Attribute.

* If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types.

* Visit attributes exists specifically to allow implementations to extend the data model.


### Available operations. 
<ol>
    <li>List visits.</li>
    <li>Create a visit.</li>
    <li>Update a visit.</li>
    <li>Delete a visit.</li>
    <li>List attribute subresources.</li>
    <li>Create attribute subresource with properties.</li>
    <li>Update attribute subresource.</li>
    <li>Delete attribute subresource.</li>
</ol>


#### List visits.

* **List all non-retired visits.**
    
    Quickly filter visits with given query parameters.Returns a `404 Not Found` status if visit not exists. If you are not logged 
    in to this action,a `401 Unauthorized` status is returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *patient* | `String` | **Patient resource uuid**
    *location* | `String` | **Location resource uuid**
    *includeInactive* | `Boolean` | **Active/Inactive status of visit**
    *fromStartDate* | `Date (ISO8601 Long)` | **Start date of the visit**

    ```console
    curl -X GET 'https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/visit?
      includeInactive=true
      &fromStartDate=2016-10-08T04:09:23.000Z
      &patient=target_patient_uuid
      &location=target_location_uuid'
    -H 'Authorization: Basic Auth'
     ```
    
* **List visit by uuid.**

    Gets a visit by its uuid. Returns a `404 Not Found status` if visit not exists. If you are not logged in to
    this action, a `401 Unauthorized` status is returned.
    
    ```console
    curl -X GET "/openmrs/ws/rest/v1/visit/target_visit_uuid" 
    -H  "accept: application/json" 
    -H  "authorization: Basic Auth"
    ```
#### Create a visit.

* To Create a a visit need you to specify below attributes in the request body.If you are not logged in to this action,
 a `401 Unauthorized` status is returned.

    ##### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *patient* | `String` | **Patient resource uuid**
    *visitType* | `String` | **Visit type resource uuid**
    *startDatetime* | `Date (ISO8601 Long)` | **Start date of the visit**
    *location* | `String` | **Location resource uuid**    
    *indication* | `string` | **Any indication of the visit**    
    *stopDatetime* | `Date (ISO8601 Long)` | **End date of the vist**    
    *encounters* | `Array[]: String` | **Encounter resources uuids**    
    *attributes* | `Array[]: Attribute` | **List of visit attributes**    
   
    ```console
        curl -X POST "/openmrs/ws/rest/v1/visit" 
        -H  "accept: application/json" 
        -H  "content-type: application/json" 
        -d "{  
            "patient":"target_patient_uuid",
            "visitType":"target_visitType_uuid",
            "startDatetime":"2016-10-08T04:09:25.000Z",
            "location":"target_location_uuid",  
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
        }"

    ```

#### Update a visit.

* Update a target visit with given uuid, this method will only modify properties in request.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `String` | **Target visit resource uuid**
    
    ##### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Visit` | **Visit resource with updated properties.**
    
    ```console
        curl -X POST "/openmrs/ws/rest/v1/visit/target_visit_uuid"
        -H  "accept: application/json" 
        -H  "authorization: Basic Auth" 
        -H  "content-type: application/json" 
        -d  modified_visit_object
    ```

#### Delete a visit.

* Delete or Retire  a  target visit by its uuid.The resource will be voided/retired unless `purge = true`. Returns a 
`404 Not Found` status if visit not exists. If you are not logged in to this action, a `401 Unauthorized` status is returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | **The resource will be voided/retired unless purge = ‘true’**

    ```console
        curl -X DELETE "/openmrs/ws/rest/v1/visit/target_visit_uuid?purge=true" 
        -H  "accept: application/json" 
        -H  "authorization: Basic Auth"
     ```
