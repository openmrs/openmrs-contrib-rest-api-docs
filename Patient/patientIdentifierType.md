# PatientIdentifierType

## Overview
Administrators define what types of identifiers they will collect. These range from National ID numbers, to driver's license numbers, to per-hospital medical record numbers.

### Properties on PatientIdentifierType:

* format: a regular expression defining what the identifier text should contain

* formatDescription: An optional description of the regular expression (used to explain the requirements of the regular expression in terms a user would understand). For example, a regular expression like `\d{4,8}` could have a description like "Must be a number between 4 and 8 digits in length."

* required: a true/false whether every patient MUST have this type

* checkDigit: a true/false whether this identifier has a checkdigit at the end

* validator: full class name of an [IdentifierValidator](https://docs.openmrs.org/doc/org/openmrs/patient/IdentifierValidator.html) (e.g., [`org.openmrs.patient.impl.LuhnIdentifierValidator`](https://docs.openmrs.org/doc/org/openmrs/patient/impl/LuhnIdentifierValidator.html))

* locationBehavior: "REQUIRED" if a location must be associated with the identifier; "NOT_USED" if the identifier does require a location

## Available operations

1. [List PatientIdentifierType resources](#List-patientidentifierType-resource)
2. [Create a patientIdentifierType record](#create-a-patientidentifierType)
3. [Update a patientIdentifierType record](#update-a-patientIdentifierType)
4. [Delete a patientIdentifierType record](#delete-a-patientIdentifierType)

### List PatientIdentifierType resource

* #### List patientIdentifierType

    Fetch all non-retired patientIdentifierTypes resources that match any specified parameters otherwise fetch all non-retired patients. Returns a `200 OK` status with the patientIdentifierType response. If the user is not logged in it returns `401 Unauthorized` status is returned.

    ```console
    GET /patientidentifiertype
    ```

* #### Get patientIdentifierType by UUID.

    Retrieve a patientIdentifierType by its UUID. Returns a `404 Not Found` status if patientIdentifierType does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ```console
    GET /patientidentifiertype/:target_patientIdentifierType_uuid
    ```
### Create a patientIdentifierType

* To create a patientIdentifierType you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

    #### Properties

    Parameter | Type | Description
    --- | --- | ---
    *name* | string | label for the identifier
    *description* | string | a small description about the patientIdentifier
    *format* | string | a regular expression defining what the identifier text should contain
    *formatDescription* | string | an optional description of the regular expression
    *required* | boolean | a true/false whether every patient MUST have this type
    *checkDigit* | boolean | a true/false whether this identifier has a checkdigit at the end
    *validator* | string | `org.openmrs.patient.IdentifierValidator`
    *locationBehavior* | "REQUIRED" or "NOT USED" | behavior of the location with respect to the identifier 
    *uniquenessBehavior* | string | specify the uniqueness of the behaviour, it can be either Unique, Non Unique or Location.

    ```console
    POST /patientidentifiertype
    {
        "name": "Wilson Hosp MRN",
        "description": "Wilson Hospital Medical Record Number",
        "format": "\d{1,10}-\d",
        "formatDescription": "Up to ten digts followed by a hyphen and another digit",
        "required": true,
        "validator": "org.openmrs.patient.impl.LuhnIdentifierValidator",
        "checkDigit": true,
        "locationBehavior": "REQUIRED",
        "uniquenessBehavior": "Unique"
    }
    ```
### Update a patientIdentifierType

* Update a target patientIdentifierType with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if patientIdentifierType not exists. If user not logged in to perform this action, a `401 Unauthorized status returned`.

    ```console
    POST /patientidentifertype/:target_patientidentifiertype_uuid
    {
        "name": "Amani Identifier",
        "description": "Medical record number for Amani Health System",
        "format": "\\d{1,10}-\\d",
        "formatDescription": "Up to ten digts followed by a hyphen and another digit",
        "required": false,
        "validator": "org.openmrs.patient.impl.LuhnIdentifierValidator",
        "locationBehavior": "NOT_USED",
        "uniquenessBehavior": "UNIQUE"
    }
    ```

### Delete a patientIdentifierType

* Delete or retire a target patientIdentifierType by its UUID. Returns a `404 Not Found` status if patientIdentifierType not exists. If user is not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = 'true'

    ```console
    DELETE /patientidentifiertype/:target_patientidentifiertype_uuid?purge=true
    ```