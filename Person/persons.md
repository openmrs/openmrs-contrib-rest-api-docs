# Person

## Overview

Every individual who is referred to in a patient record in OpenMRS is stored in the system as a Person. These include Patients, any patient relative or caretaker, Providers, and Users.

All Persons have these characteristics.

## Sub resource types

### Names
A person can have one or more names, one of which must be marked as the **preferred** name. The preferred name will be displayed in search results and patient screens.

### Addresses

A person may have zero or more contact addresses. You may configure the format of these addresses for your particular locale.

### Person Attributes

To support your local needs, you can define additional pieces of information about the people in your system, on top of those that are natively supported by OpenMRS. You can define the datatype of a Person Attribute, as well as any constraints on the possible values, using metadata. This metadata is called a Person Attribute Type.

Person Attributes are suitable for storing other information. But historical values of person attributes are not retained. For example, you should use a person attribute to record a patient's contact telephone number. This information may change, but if it does so, the system need only store the most recent value, and need not retain previous values. It is not appropriate to use a person attribute to store something like the patient's height, which is recorded at a given point in time, but can be expected to change and should be tracked as it does so.

## Available Operations
1. List Persons.
2. Create Persons.
3. Update Persons.
4. Delete Persons.

### Search Persons

* #### Search Persons
     
     Fetch all non-retired persons that match the search query parameter. Returns a 200 OK status with the Person response.

    #### Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | *query_string* | *Any string in general against which the results should be filtered out*

    ```console
        GET /person/?q=query_string
    ```

* #### List person by UUID

    Retrieve a person by its UUID. Returns a `404 Not Found` status if person does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

    ```console
    GET /person/:target_person_uuid
    ```

### Create a person

* To create a person you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `Array[] : names` | List of names
    *gender* | String | A value to indicate the gender, for eg: "M" for male
    *age* | Integer | Integer value to denote the age
    *birthDate* | String | Date of birth of a person
    *birthDateEstimated* | Boolean | A true/false value to denote whether the birthdate is a correct estimate or not
    *dead* | Boolean | A true/false value to denote whether a person is dead or not
    *deathDate* | String | Date of death of the person 
    *causeOfDeath* | String | Reason for the death of the person
    *addresses* | `Array[] : addresses` | The address details aggregated in an array
    *attributes* | `Array[] : attributes` | The attribute details aggregated in an array
    *deathdateEstimated* | Boolean | A true/false value to denote whether the deathDate is a correct estimate or not
    *birthTime* | String | The time of birth of the person

    ```
    POST /person
    