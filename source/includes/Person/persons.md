# Person

## Person Overview

Every individual who is referred to in a patient record in OpenMRS is stored in the system as a Person. These include Patients, any patient relative or caretaker, Providers, and Users.

All Persons have these characteristics.

## Subresource types

### Names
A person can have one or more names, one of which must be marked as the **preferred** name. The preferred name will be displayed in search results and patient screens.

### Addresses

A person may have zero or more contact addresses. You may configure the format of these addresses for your particular locale.

### Person Attributes

To support your local needs, you can define additional information about the people in your system, on top of those that are natively supported by OpenMRS. You can define the datatype of a Person Attribute, as well as any constraints on the possible values, using metadata. This metadata is called a Person Attribute Type.

Person Attributes are suitable for storing other information. But historical values of person attributes are not retained. For example, you should use a person attribute to record a patient's contact telephone number. This information may change, but if it does so, the system need only store the most recent value, and need not retain previous values. It is not appropriate to use a person attribute to store something like the patient's height, which is recorded at a given point in time, but can be expected to change and should be tracked as it does so.

## Available Operations for Person type

1. [Search Persons](#search-persons)
2. [Create Persons](#create-a-person)
3. [Update Persons](#update-a-person)
4. [Delete Persons](#delete-a-person)
5. [List person name](#list-person-name-subresource)
6. [Create person name](#create-person-name-subresource)
7. [Update person name](#update-person-name-subresource)
8. [Delete person name](#delete-person-name-subresource)
10. [List person addresses](#list-person-address-subresource)
11. [Create person address](#create-person-address-subresource)
12. [Update person address](#create-person-address-subresource)
13. [Delete person address](#create-person-address-subresource)
14. [List person attributes](#list-person-attribute-subresource)
15. [Create person attribute](#create-person-attribute-subresource)
16. [Update person attribute](#update-person-attribute-subresource)
17. [Delete person attribute](#delete-person-attribute-subresource)

## Search Persons

### Search Persons

```console
GET /person?q=john
```
     
     Fetch all non-voided persons that match the search query parameter. Returns a `200 OK` status with the Person response.

### Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | *string* | *search by name*


### List person by UUID

```console
GET /person/:target_person_uuid
```

    Retrieve a person by their UUID. Returns a `404 Not Found` status if the person does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.


## Create a person

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
    

## Update a person

```console
POST /person/:target_person_uuid
{
    "gender": "M",
    "birthdate": "1997-01-13",
}
```

* Update a person. This method only modifies properties specified in the request. Returns a `404 Not found`.
If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

    An example of the request is as follows : 

## Delete a person

```console
DELETE /person/:target_person_uuid?purge=true
```

* Delete or Void a target person. Returns a `404 Not Found` status if person not exists. If not authenticated or authenticated user does not have sufficient privileges, `401 Unauthorized` status is returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’



## List person name subresource

```console
GET /person/:target_person_uuid/name
```
* List all the person name subresource corresponding to a `target_person_uuid`. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

```console
GET /person/:target_person_uuid/name/:target_name_uuid
```
* List the person name by its `UUID` and corresponding to a `target_person_uuid`. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.


## Create person name subresource

```console
POST person/:target_person_uuid/name
{ 
    "givenName": "Mohit",
    "familyName": "Kumar",
    "preferred": true,
    "prefix": "Mr."
}
```

* To create a person name subresource for a specific person resource you need to specify below properties in your request body.
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

## Update person name subresource

```console
POST person/:target_person_uuid/name
{ 
    "givenName": "Mohit",
    "familyName": "Verma",
    "preferred": true,
    "prefix": "Dr."
}
```

* To update a person name with given UUID value for a specific person resource, you need to specify below properties in your request body.
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


## Delete person name subresource

```console
DELETE /person/:target_person_uuid/person/:target_name_uuid
```

* Delete or void a target name subresource. Returns a `404 Not Found` status if an attribute does not exist. 
If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

 
## List person address subresource

> List person address subresource

```shell
GET /person/:target_person_uuid/address
```

> Success Response

```response

{
    "results": [
        {
            "display": "Address15501",
            "uuid": "e350d53f-0252-4259-8d87-d97a2d58166e",
            "preferred": true,
            "address1": "Address15501",
            "address2": null,
            "cityVillage": "City5501",
            "stateProvince": "State5501",
            "country": "Country5501",
            "postalCode": "55501",
            "countyDistrict": null,
            "startDate": null,
            "endDate": null,
            "latitude": null,
            "longitude": null,
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/e350d53f-0252-4259-8d87-d97a2d58166e",
                    "resourceAlias": "address"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/e350d53f-0252-4259-8d87-d97a2d58166e?v=full",
                    "resourceAlias": "address"
                }
            ],
            "resourceVersion": "2.0"
        }
    ]
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* List all the person addresses corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person address does not exist. If the user is not logged in to perform this action, a `401 unauthorized` status is returned.

## List person address subresource by UUID

> List person address subresource by UUID

```shell
GET /person/:target_person_uuid/address/:target_address_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/e350d53f-0252-4259-8d87-d97a2d58166e")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/e350d53f-0252-4259-8d87-d97a2d58166e", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* List all the person addresses by its `target_address_uuid` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person address does not exist. If user not logged in to perform this action, a `401 unauthorized` status is returned.


## Create person address subresource

> Create person address subresource

```shell
POST person/:target_person_uuid/address
{ 
    "address1": "30, Vivekananda Layout, Munnekolal,Marathahalli",
    "cityVillage": "Bengaluru",
    "stateProvince": "Karnataka",
    "postalCode": "560037",
    "latitude": "28.65033",
    "longitude": "77.304255"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{ \r\n    \"address1\": \"30, Vivekananda Layout, Munnekolal,Marathahalli\",\r\n    \"cityVillage\": \"Bengaluru\",\r\n    \"stateProvince\": \"Karnataka\",\r\n    \"postalCode\": \"560037\",\r\n    \"latitude\": \"28.65033\",\r\n    \"longitude\": \"77.304255\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var raw = JSON.stringify({"address1":"30, Vivekananda Layout, Munnekolal,Marathahalli","cityVillage":"Bengaluru","stateProvince":"Karnataka","postalCode":"560037","latitude":"28.65033","longitude":"77.304255"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address", requestOptions)


```

* To create a person address subresource for a specific person resource you need to specify below properties in your request body.
If user not logged in to perform this action, a `401 Unauthorized` status is returned.

    #### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *preferred* | `Boolean` | true if this is the person's preferred address. If a person has multiple addresses, only one can be preferred
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
    *latitude* | `String` | latitude of the address
    *longitude* | `String` | longitude of the address



## Update person address subresource

> Update person address subresource

```shell
POST person/:target_person_uuid/address/:target_address_uuid
{ 
    "address1": "30, Vivekananda Layout, Munnekolal,Marathahalli",
    "cityVillage": "Bengaluru",
    "stateProvince": "Karnataka",
    "postalCode": "560037",
    "latitude": "28.65033",
    "longitude": "77.304255"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{ \r\n    \"address1\": \"30, Vivekananda Layout, Munnekolal,Marathahalli\",\r\n    \"cityVillage\": \"Bengaluru\",\r\n    \"stateProvince\": \"Karnataka\",\r\n    \"postalCode\": \"560037\",\r\n    \"latitude\": \"28.65033\",\r\n    \"longitude\": \"77.304255\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/62fc41dd-e120-40c5-8a66-b651b0a5fecc")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var raw = JSON.stringify({"address1":"30, Vivekananda Layout, Munnekolal,Marathahalli","cityVillage":"Bengaluru","stateProvince":"Karnataka","postalCode":"560037","latitude":"28.65033","longitude":"77.304255"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/62fc41dd-e120-40c5-8a66-b651b0a5fecc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* To update a person address with given UUID value for a specific person resource you need to specify below properties in your request body.
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
    *latitude* | `String` | latitude of the address
    *longitude* | `String` | longitude of the address


## Delete a person address subresource

> Delete a person address subresource

```shell
DELETE /person/:target_person_uuid/person/:target_address_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/62fc41dd-e120-40c5-8a66-b651b0a5fecc")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ED9DBD5CFD355A973EFFECD642D8331D");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/person/90f7f0b4-06a8-4a97-9678-e7a977f4b518/address/62fc41dd-e120-40c5-8a66-b651b0a5fecc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or void a target address subresource. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

 
## List person attribute subresource


```console
GET /person/:target_person_uuid/attribute
```
* List all person attributes for a given person. Returns a `404 Not Found` if the person doesn't exist. If not authenticated or the authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

```console
GET /person/:target_person_uuid/name/:target_attribute_uuid
```
* List all the person attributes by its `UUID` and corresponding to a `target_person_uuid`. Returns a `404 Not Found` status if person attribute does not exist. If user not logged in to perform this action, a `401 unauthorized` status is returned.


## Create person attribute subresource

```console
POST person/:target_person_uuid/attribute
{ 
    "attributeType": "8d8718c2-c2cc-11de-8d13-0010c6dffd0f",
    "value": "Birthplace",
}
```
* To create a person attribute subresource for a specific person resource you need to specify below properties in your request body.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

    #### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `UUID` | UUID of the attributeType
    *value* | `String` | value associated with the attribute


## Update person attribute subresource

```console
POST person/:target_person_uuid/attribute
{ 
    "attributeType": "8d8718c2-c2cc-11de-8d13-0010c6dffd0f",
    "value": "Birthplace",
}
```
* To update a person attribute with given UUID value for a specific person resource you need to specify below properties in your request body.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ### Attributes
    
    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `UUID` | UUID of the attributeType
    *value* | `String` | value associated with the attribute


## Delete person attribute subresource

```console
DELETE /person/:target_person_uuid/person/:target_attribute_uuid
```
* Delete or void a target attribute. Returns `404 Not Found` status if the person does not exist. 
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` 
status is returned.

 
