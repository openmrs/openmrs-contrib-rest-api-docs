# PatientIdentifierType

## Overview
Administrators define what types of identifiers they will collect. These range from National ID numbers, to driver's license numbers, to per-hospital medical record numbers.

### Properties on PatientIdentifierType:

* format: a regular expression defining what the identifier text should contain.

* formatDescription: An optional description of the regular expression (used to explain the requirements of the regular expression in terms a user would understand). For example, a regular expression like \d{4,8}could have a description like "Must be a number between 4 and 8 digits in length."

* required: a true/false whether every patient MUST have this type

* checkDigit: a true/false whether this identifier has a checkdigit at the end.

* validator: full class name of the IdentifierValidators (for example : `org.openmrs.patient.IdentifierValidator`).

* locationBehavior: "REQUIRED" if a location must be associated with the identifier; "NOT_USED" if the identifier does require a location.

## Available operations

1. [List PatientIdentifierType resources](#List-patientidentifierType)
2. [Create a patientIdentifierType record](#create-a-patient)
3. [Update a patientIdentifierType record](#update-a-patient)
4. [Delete a patientIdentifierType record](#delete-a-patient)

### List PatientIdentifierType resour

* #### List patientIdentifierType

    Fetch all non-retired patientIdentifierTypes resources that match any specified parameters otherwise fetch all non-retired patients. Returns a `200 OK` status with the patient response. If the user is not logged in it returns `401 Unauthorized` status is returned.

    ```console
    GET /patientidentifiertype?
        &q=**searchqQuery**
    ```

* #### List patientIdentifierType by UUID.

    Retrieve a patientIdentifierType by its UUID. Returns a `404 Not Found` status if patient does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ```console
    GET /patientIdentifierType/:target_patientIdentifierType_uuid
    ```