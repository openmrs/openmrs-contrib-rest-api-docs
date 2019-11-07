# User

## Overview

 A User in OpenMRS is an account that a person may use to log into the system.

The real-life person is represented by a Person record in OpenMRS, and a person may have more than one user account. If you want a patient to be able to view her own record in OpenMRS, then you need to create a user account and link it to the patient.

## Available operations

1. [List users](#list-user)
2. [Create a user](#create-a-user)
3. [Update a user](#update-a-user)
4. [Delete a user](#delete-a-user)


### List user

* #### List all non-voided users.
    
    Quickly filter users with given query parameters.Returns a `404 Not Found` status if user not exists. 
     If not logged in to perform this action,a `401 Unauthorized` status returned.
    
    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Query to filter users by its name

    ```console
    GET /user?
      q=Clinician
     ```
    
* #### Get user by UUID.

    Retrieve a user by its UUID. Returns a `404 Not Found` status if user not exists. If not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /user/:target_user_uuid
    ```
   
### Create a user

* To create a user you need to specify below attributes in the request body. If you are not logged in to perform 
this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the user
    *description* | `String | Description of the user
    *username* | `String | username of the user
    *password* | `String | password of the user
    *person* | `String` | person resource associated with the user
    *systemId* | `String` | a unique identifier assigned to each user
    *roles* | `Array[] : role` | a list of roles attributed to the user
    *userProperties* | `JSON Object`| A set of key value pairs. Used to store user specific data 
    *secretQuestion* | `String` | A secret question chosen by the user
   
    ```console
        POST /user
        {
          "name": "Mohit Kumar",
          "description": "A GSoD participant."
          "username": "batbrain7"
          "password": "******"
          "person" :
                {
                "names": [
                    {
                        "givenName": "Mohit",
                        "familyName": "Kumar"
                    }
                ],
                "gender": "M",
                "birthdate": "1997-09-02",
                "addresses": [
                {
                 "address1": "30, Vivekananda Layout, Munnekolal,Marathahalli",
                "cityVillage": "Bengaluru",
                "country": "India",
                "postalCode": "560037"
                }
            ]
        },
        "systemId": "string",
        "userProperty": {},
        "secretQuestion" : "What is the name of your high school?"
    }
    ```
### Update a user role

*  Update a target user with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if user not exists. If not logged in to perform this action, a `401 Unauthorized` status returned.
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the user
    *description* | `String | Description of the user
    *username* | `String | username of the user
    *password* | `String | password of the user
    *person* | `String` | person resource associated with the user
    *systemId* | `String` | a unique identifier assigned to each user
    *roles* | `Array[] : role` | a list of roles attributed to the user
    *userProperties* | `JSON Object`| A set of key value pairs. Used to store user specific data 
    *secretQuestion* | `String` | A secret question chosen by the user
   
    ```console
        POST /user/:target_user_uuid
        {
          "name": "Mohit Sharma",
          "description": "An OpenMRS Developer."
          "username": "batbrain7"
          "password": "******"
          "person" :
                {
                "names": [
                    {
                        "givenName": "Mohit",
                        "familyName": "Sharma"
                    }
                ],
                "gender": "M",
                "birthdate": "1997-09-02",
                "addresses": [
                {
                 "address1": "30, Vivekananda Layout, Munnekolal,Marathahalli",
                "cityVillage": "Bengaluru",
                "country": "India",
                "postalCode": "560037"
                }
            ]
        },
        "systemId": "string",
        "userProperty": {},
        "secretQuestion" : "In which year did you graduate"
    }
    ```
    
### Delete a user

* Delete or Void a target user by its UUID. Returns a `404 Not Found` status if user not exists.If not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

    ```console
        DELETE /user/:target_user_uuid?purge=true
     ```
