# Patients

## Overview

* Anyone who receives care in OpenMRS must be a **Patient**.

* Every Patient must have atleast one Identifier, which is explained below. (for example,
Anyone who has an Encounter or who is enrolled in a Program is a Patient.)

* A Patient is also a Person, meaning they must have at least one name and they may have addresses.

## Sub resource types

### PatientIdentifier (Identifier)

* A PatientIdentifier is a medical record number assigned by your facility, used to identify and re-identify the patient on subsequent visits.

### Allergy

* OpenMRS lets you manually maintain an **Allergy List** for a patient, including the allergen, reaction, severity, etc.

## Available operations.

1. [List Patients](#search-patients)
2. [Create a patient record](#create-a-patient)
3. [Update a patient record](#update-a-patient)
4. [Delete a patient record](#delete-a-patient)
5. [List patientIdentifier sub resource](#list-patientIdentifier-sub-resources)
6. [Create patientIdentifier sub resource with properties](#create-a-patientIdentifier-sub-resource-with-properties)
7. [Update patientIdentifier sub resource](#update-patientidentifier-sub-resource-with-properties)
8. [Delete patientIdentifier sub resource](#delete-patientidentifier-sub-resource-with-properties)
9.  List allergy sub resource
10. Create allergy sub resource with properties
11. Update allergy sub resource
12. Delete allergy sub resource

### Search patients

* #### Search patients

    Fetch all non-retired patients that match any specified parameters otherwise fetch all non-retired patients. Returns a `200 OK` status with the patient response. 

    ##### Query Parameters

    Parameter | Description
    --- | ---
    matchSimilar | use this parameter to enter anything to match 
    country | Country where the patient is registered
    birthDate | must be used with matchSimilar
    Gender | Gender of the patient
    city | City where the patient is registered
    address  | Address of the patients
    familyName | must be used with matchSimilar
    middleName | must be used with matchSimilar
    postalCode | must be used with matchSimilar
    givenname  | must be used with matchSimilar
    state | must be used with matchSimilar

    ```console
    GET /patient?
        country=india
        &gender=M
    ```

* #### List patient by UUID.

    Retrieve a patient by its UUID. Returns a `404 Not Found` status if patient does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ```console
    GET /patient/:target_patient_uuid
    ```

### Create a patient

* To create a patient you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

    #### Properties

    Parameter | Type | Description
    --- | --- | ---
    *person* | `PERSON_UUID` | Person resource UUID
    *identifiers* | `Array[]: Identifiers` | List of patientIdentifiers

    ```console
        POST /patient
        {
          "person": "uuid",
          "identifiers": [
            {
              "identifier": "string",
              "identifierType": "uuid",
              "location": "uuid",
              "preferred": true
            }
          ]
        }
    ```
### Update a patient

* Update a target patient with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if patient not exists. If user not logged in to perform this action, a `401 Unauthorized status returned`.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_patient_uuid` | Target patient resource UUID

    #### Properties

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Patient` | Patient resource with updated properties

    ```console
    POST /patient/:target_patient_uuid
    -d modified_patient_object

### Delete a patient

* Delete or retire a target patient by its UUID. Returns a `404 Not Found` status if patient not exists. If user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    **uuid** | `String` | uuid to delete
    *purge* | `Boolean` | The resource will be voided/retired unless purge = 'true'

    ```console
    DELETE /patient/:target_patient_uuid?purge=true
    ```
### List patientIdentifier sub resources

* #### List all patientIdentifier sub resources for a patient.

    Retrieve all <b>identifier</b> sub resources of a <b>patient</b> resource by `target_patient_uuid`.Returns a `404 Not Found` status if patientIdentifier not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

    ```console
     GET /patient/:target_patient_uuid/identifier
    ```  
* #### List patientIdentifier sub resource by it's UUID and parent patient UUID.

    Retrieve a <b>patientIdentifier</b> sub resources of a <b>patient</b> resource. Returns a `404 Not Found` status if patientIdentifier not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

    ```console
    GET /patient/:target_patient_uuid/identifier/:target_identifier_uuid
    ```
### Create a patientIdentifier sub resource with properties 

* To create a patientIdentifier sub resource for a specific patient resource you need to specifyn below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query parameter 
    Parameter | Description
    --- | ---
    `target_patient_uuid` : patient resource uuid

    #### Properties for resource

    Parameter | type | Description
    --- | --- | ---
    *identifier* | `String` | value of the identifier
    *identifierType* | `Identifier_Type_UUID` | Create identifier from this Identifier_type
    *location* | `Location UUID` | Get patients for this location
    *preferred* | `boolean` | preferred/not preferred identifier

    ```console
        POST patient/:target_patient_uuid/identifier
        { 
            "identifier" : "string",
            "identifierType" : "target_identifer_uuid",
            "location" : "target_location_uuid",
            "preferred" : true/false
        }
    ```
### Update patientIdentifier sub resource with properties

* Updates an patientIdentifier sub resource value with given uuid, this method will only modify value of the sub resource. Returns a `404 Not Found` status if attribute not exists.If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    #### Properties

    Parameter | Type | Description
    --- | --- | ---
    *identifier* | `String` | updated value of the identifier
    *identifierType* | `Identifier_Type_UUID` | Create identifier from this Identifier_type
    *location* | `Location UUID` | updated location
    *preferred* | `boolean` | updated status of preferred/not preferred identifier

    ```console
        POST patient/:target_patient_uuid/identifier/:target_identifier_uuid
        { 
            "identifier" : "string",
            "identifierType" : "target_identifer_uuid",
            "location" : "target_location_uuid",
            "preferred" : true/false
        }
    ```

### Delete patientIdentifier sub resource with properties

* Delete or retire a target identifier sub resource by its UUID.Returns a `404 Not Found` status if attribute not exists. 
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
     ```console
        DELETE /patient/:target_patient_uuid/identifier/:target_identifier_uuid
     ```