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
5. List person name subresources.
6. Create person name subresources.
7. Update person name subresources.
8. Delete person name subresources.
10. List person address subresources.
11. Create person address subresources.
12. Update person address subresources.
13. Delete person address subresources.
14. List person attribute subresource.
15. Create person attribute subresources.
16. Update person attribute subresources.
17. Delete person attribute subresources

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
    }
    ```

### Update a person

* Update a target person with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if person not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned. 

    An example of the request is as follows : 

    ```console
    POST /person/:target_person_uuid
    {
        "age": 22,
        "gender": "M",
        "birthdate": "1997-01-13",
    }
    ```

### Delete a person

* Delete or Void a target person by its UUID. Returns a `404 Not Found` status if person not exists.If user 
 not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

    ```console
    DELETE /person/:target_person_uuid?purge=true
     ```


### List person name subresource

* List all the person name subresource corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person name not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

```console
GET /person/:target_person_uuid/name
```

* List all the person name subresource by it's `UUID` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person name not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

```console
GET /person/:target_person_uuid/name/:target_name_uuid
```

### Create person name subresource

* To create a person name sub resource for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

#### Attributes

Parameter | Type | Description
--- | --- | ---
*givenname* | `String` | name of the person
*middlename* | `String` | middle name of the person
*familyName* | `String` | family name/surname of the person
*familyName2* | `String` | second family name/surname of the person
*preferred* | `Boolean` | preferred/not preferred name
*prefix* | `String` | prefix for the name
*familyNamePrefix* | `String` | prefix if any for the family name 
*familyNameSuffix* | `String` | Suffix if any for the family name
*degree* | `String` | degree attained by the person

```console
POST person/:target_person_uuid/name
{ 
    "givenName": "Mohit",
    "familyName": "Kumar",
    "preferred": true,
    "prefix": "Mr."
}
```

### Update person name subresource

* To update a person name with given uuid value for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

#### Attributes

Parameter | Type | Description
--- | --- | ---
*givenname* | `String` | name of the person
*middlename* | `String` | middle name of the person
*familyName* | `String` | family name/surname of the person
*familyName2* | `String` | second family name/surname of the person
*preferred* | `Boolean` | preferred/not preferred name
*prefix* | `String` | prefix for the name
*familyNamePrefix* | `String` | prefix if any for the family name 
*familyNameSuffix* | `String` | Suffix if any for the family name
*degree* | `String` | degree attained by the person

```console
POST person/:target_person_uuid/name
{ 
    "givenName": "Mohit",
    "familyName": "Verma",
    "preferred": true,
    "prefix": "Dr."
}
```

### Delete a person name sub resource

* Delete or retire a target name sub resource by its UUID.Returns a `404 Not Found` status if attribute not exists. 
If user not logged in to perform this action, a `401 Unauthorized` status returned.

 ```console
DELETE /person/:target_person_uuid/person/:target_name_uuid
 ```

### List person address subresource

* List all the person address subresource corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person address not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

```console
GET /person/:target_person_uuid/address
```

* List all the person address subresource by it's `target_address_uuid` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person address not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

```console
GET /person/:target_person_uuid/address/:target_address_uuid
```

### Create person address subresource

* To create a person address sub resource for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

#### Attributes

Parameter | Type | Description
--- | --- | ---
*preferred* | `Boolean` | preferred/not preferred address
*address1* | `String` | address of the person
*address2* | `String` | second address of the person
*cityVillage* | `String` | city/village of the person
*stateProvince* | `String` | name of the state of the person
*country* | `String` | country of the person
*postalCode* | `String` | pin code of the person
*countyDistrict* | `String` | county district of the person
*address3* | `String` | third address of the person
*address4* | `String` | fourth address of the person
*address5* | `String` | fifth address of the person
*address6* | `String` | sixth address of the person
*startDate* | `String` | start date of living by the person
*endDate* | `String` | end date of living by the person
*lattitude* | `String` | lattitude of the location of the person
*longitude* | `String` | longitude of the location of the person


```console
POST person/:target_person_uuid/address
{ 
    "address1": "30, Vivekananda Layout, Munnekolal,Marathahalli",
    "cityVillage": "Bengaluru"
    "stateProvince": "Karnataka",
    "postalCode": "560037",
    "lattitude": "28.65033",
    "longitude": "77.304255"
}
```

### Update person address subresource

* To update a person address with given uuid value for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

#### Attributes

Parameter | Type | Description
--- | --- | ---
*preferred* | `Boolean` | preferred/not preferred address
*address1* | `String` | address of the person
*address2* | `String` | second address of the person
*cityVillage* | `String` | city/village of the person
*stateProvince* | `String` | name of the state of the person
*country* | `String` | country of the person
*postalCode* | `String` | pin code of the person
*countyDistrict* | `String` | county district of the person
*address3* | `String` | third address of the person
*address4* | `String` | fourth address of the person
*address5* | `String` | fifth address of the person
*address6* | `String` | sixth address of the person
*startDate* | `String` | start date of living by the person
*endDate* | `String` | end date of living by the person
*lattitude* | `String` | lattitude of the location of the person
*longitude* | `String` | longitude of the location of the person


```console
POST person/:target_person_uuid/address
{ 
    "address1": "30, Vivekananda Layout, Munnekolal,Marathahalli",
    "cityVillage": "Bengaluru"
    "stateProvince": "Karnataka",
    "postalCode": "560037",
    "lattitude": "28.65033",
    "longitude": "77.304255"
}
```

### Delete a person address sub resource

* Delete or retire a target address sub resource by its UUID.Returns a `404 Not Found` status if attribute not exists. 
If user not logged in to perform this action, a `401 Unauthorized` status returned.

 ```console
DELETE /person/:target_person_uuid/person/:target_address_uuid
 ```

### List person attribute subresource

* List all the person attribute subresource corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person attribute not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

```console
GET /person/:target_person_uuid/attribute
```

* List all the person attribute subresource by it's `UUID` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person attribute not exists. If user not logged in to perform this action, a `401 unauthorized` status returned.

```console
GET /person/:target_person_uuid/name/:target_attribute_uuid
```

### Create person attribute subresource

* To create a person attribute sub resource for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

#### Attributes

Parameter | Type | Description
--- | --- | ---
*attributeType* | `UUID` | UUID of the attributeType
*value* | `String` | value associated with the attribute
*hydratedObject* | `UUID` | UUID of the hydrated person attribute object

```console
POST person/:target_person_uuid/attribute
{ 
    "attributeType": "Mohit",
    "value": "Kumar",
}
```

### Update person attribute subresource

* To update a person attribute with given uuid value for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

#### Attributes

Parameter | Type | Description
--- | --- | ---
*attributeType* | `UUID` | UUID of the attributeType
*value* | `String` | value associated with the attribute
*hydratedObject* | `UUID` | UUID of the hydrated person attribute object

```console
POST person/:target_person_uuid/attribute
{ 
    "attributeType": "Mohit",
    "value": "Kumar",
}
```

### Delete a person attribute sub resource

* Delete or retire a target attribute sub resource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If user not logged in to perform this action, a `401 Unauthorized` status returned.

 ```console
DELETE /person/:target_person_uuid/person/:target_attribute_uuid
 ```