# Person

## Person Overview

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

## Available Operations for Person type

1. [Search Persons](#search-persons)
2. [Create Persons](#create-a-person)
3. [Update Persons](#update-a-person)
4. [Delete Persons](#delete-a-person)
5. [List person names](#list-person-name-subresource)
6. [Create person name](#create-person-name-subresource)
7. [Update person name](#update-person-name-subresource)
8. [Delete person name](#delete-person-name-subresource)
10. [List person addresses](#list-person-address-subresource)
11. [Create person address](#create-person-address-subresource)
12. [Update person address](#create-person-address-subresource)
13. [Delete person address](#create-person-address-subresource)
14. [List person attributes](#list-person-attribute-subresource)
15. [Create person attribute](#create-person-attribute-subresource)
16. [Update person attribute](#update-person-name-subresource)
17. [Delete person attribute](#delete-person-name-subresource)

## Search Persons

* ### Search Persons
     
     Fetch all non-voided persons that match the search query parameter. Returns a `200 OK` status with the Person response.

    ### Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | *string* | *search by name*

```console
GET /person?q=john
```

* ### List person by UUID

    Retrieve a person by their UUID. Returns a `404 Not Found` status if the person does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

```console
GET /person/:target_person_uuid
```

## Create a person

* To create a person you need to specify the below properties in the request. `401 Unauthorized` is returned if the request is not authenticated or if the authenticated user does not have appropriate permissions.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `Array[] : names` | List of names
    *gender* | String | The patient's gender ("M" for male, "F" for female, or "U" for unknown)
    *age* | Integer | The estimated age in years. Used when birthdate is unknown.
    *birthDate* | String | Date of birth of a person
    *birthDateEstimated* | Boolean | True if the birthdate is estimated; false if birthdate is accurate.
    *birthTime* | String | The time of birth of the person
    *dead* | Boolean | True if the patient is dead.
    *deathDate* | String | Date of death of the person
    *causeOfDeath* | `Concept UUID` | Reason for the death of the person
    *deathdateEstimated* | Boolean | `true` if deathDate is estimate; `false` if deathDate is accurate
    *addresses* | `Array[] : addresses` | The address details aggregated in an array
    *attributes* | `Array[] : attributes` | The attribute details aggregated in an array
    
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

## Update a person

* Update a person. This method only modifies properties specified in the request. Returns a `404 Not found`.
If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

    An example of the request is as follows : 

```console
POST /person/:target_person_uuid
{
    "gender": "M",
    "birthdate": "1997-01-13",
}
```

## Delete a person

* Delete or Void a target person. Returns a `404 Not Found` status if person not exists. If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’

```console
DELETE /person/:target_person_uuid?purge=true
 ```


## List person name

* List all the person name subresource corresponding to a `target_person_uuid`. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

```console
GET /person/:target_person_uuid/name
```

* List the person name by its `UUID` and corresponding to a `target_person_uuid`. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

```console
GET /person/:target_person_uuid/name/:target_name_uuid
```

## Create person name subresource

* To create a person name sub resource for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *givenName* | `String` | name of the person
    *middleName* | `String` | middle name of the person
    *familyName* | `String` | family name/surname of the person
    *familyName2* | `String` | second family name/surname of the person
    *preferred* | `Boolean` | true if this is the person's preferred name. When a person has only one name, it should be marked as preferred; when a person has multiple names, only one name can be preferred.
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

## Update person name 

* To update a person name with given uuid value for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *givenName* | `String` | name of the person
    *middleName* | `String` | middle name of the person
    *familyName* | `String` | family name/surname of the person
    *familyName2* | `String` | second family name/surname of the person
    *preferred* | `Boolean` | true if this is the person's preferred name. When a person has only one name, it should be marked as preferred; when a person has multiple names, only one name can be preferred.
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

## Delete a person name sub resource

* Delete or void a target name sub resource. Returns a `404 Not Found` status if attribute does not exist. 
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

 ```console
DELETE /person/:target_person_uuid/person/:target_name_uuid
 ```

## List person address subresource

* List all the person addresses corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person address does not exist. If user not logged in to perform this action, a `401 unauthorized` status is returned.

```console
GET /person/:target_person_uuid/address
```

* List all the person addresses by its `target_address_uuid` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person address does not exist. If user not logged in to perform this action, a `401 unauthorized` status is returned.

```console
GET /person/:target_person_uuid/address/:target_address_uuid
```

## Create person address subresource

* To create a person address sub resource for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    #### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *preferred* | `Boolean` | true if this is the person's preferred address. If a person has multiple addresses, only one can be preferred.
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
    *startDate* | `String` | date when the person began living at this address
    *endDate* | `String` | date when the person stopped living at this address
    *lattitude* | `String` | lattitude of the address
    *longitude* | `String` | longitude of the address


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

## Update person address subresource

* To update a person address with given uuid value for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.
    
    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *preferred* | `Boolean` | true if this is the person's preferred address. If a person has multiple addresses, only one can be preferred.
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
    *startDate* | `String` | date when the person began living at this address
    *endDate* | `String` | date when the person stopped living at this address
    *lattitude* | `String` | lattitude of the address
    *longitude* | `String` | longitude of the address


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

## Delete a person address sub resource

* Delete or void a target address sub resource. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

 ```console
DELETE /person/:target_person_uuid/person/:target_address_uuid
 ```

## List person attribute subresource

* List all person attributes for a given person. Returns a `404 Not Found` if the person doesn't exist. If not authenticated or the authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

```console
GET /person/:target_person_uuid/attribute
```

* List all the person attributes by its `UUID` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person attribute does not exist. If user not logged in to perform this action, a `401 unauthorized` status is returned.

```console
GET /person/:target_person_uuid/name/:target_attribute_uuid
```

## Create person attribute subresource

* To create a person attribute sub resource for a specific person resource you need to specify below properties in your request body.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `UUID` | UUID of the attributeType
    *value* | `String` | value associated with the attribute

```console
POST person/:target_person_uuid/attribute
{ 
    "attributeType": "8d8718c2-c2cc-11de-8d13-0010c6dffd0f",
    "value": "Birthplace",
}
```

## Update person attribute subresource

* To update a person attribute with given uuid value for a specific person resource you need to specify below properties in your request body.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `UUID` | UUID of the attributeType
    *value* | `String` | value associated with the attribute

```console
POST person/:target_person_uuid/attribute
{ 
    "attributeType": "8d8718c2-c2cc-11de-8d13-0010c6dffd0f",
    "value": "Birthplace",
}
```

## Delete a person attribute sub resource

* Delete or void a target attribute. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

 ```console
DELETE /person/:target_person_uuid/person/:target_attribute_uuid
 ```
