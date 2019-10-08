# Patients

## Overview

* Anyone who receives care in OpenMRS must be a **Patient**.

* Every Patient must have atleast one Identifier, which is explained below. (for example,
Anyone who has an Encounter or who is enrolled in a Program is a Patient.)

* A Patient is also a Person, meaning they must have at least one name and they may have addresses.

## Sub resource types

### PatientIdentifier

* A PatientIdentifier is a medical record number assigned by your facility, used to identify and re-identify the patient on subsequent visits.

### Allergy

* OpenMRS lets you manually maintain an **Allergy List** for a patient, including the allergen, reaction, severity, etc.

## Available operations.

1.  List patients
2.  Create a patient record
3.  Update a patient record
4.  Delete a patient record
5.  List patientIdentifier sub resource
6.  Create patientIdentifier sub resource with properties
7.  Update patientIdentifier sub resource
8.  Delete patientIdentifier sub resource
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
### Update a visit

* Update a  target patient with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if  visit not exists. If user not logged in to perform this action, a `401 Unauthorized status returned`.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_visit_uuid` | Target visit resource UUID

    #### Properties

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Patient` | Patient resource with updated properties

    ```console
    POST /patient/:target_patient_uuid
    -d modified_patient_object

### Delete a patient

* Delete or Retire a target patient by its UUID. Returns a `404 Not Found` status if patient not exists. If user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    **uuid** | `String` | uuid to delete
    *purge* | `Boolean` | The resource will be voided/retired unless purge = 'true'

    ```console
    DELETE /patient/:target_patient_uuid?purge=true
    ```
