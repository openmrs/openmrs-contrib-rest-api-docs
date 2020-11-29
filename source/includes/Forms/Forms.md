# Forms

## Forms Overview

* Forms in OpenMRS can be thought of as data collecting tools, which help in collecting patient data during an encounter with the patient (sometimes even after the encounter is over).
* The concept dictionary is a central part of OpenMRS. Concepts can commonly be thought of as questions and possible answers which are present on forms.
* Forms in OpenMRS can be of many types, e.g.,In almost all the instances observation forms which help in capturing observations during an encounter (like admission,Vitals e.t.c)


## Subresource types of Forms

### formFields

* The FormField relates to the fields present on a form. A form can have many 0 or more fields associated with it in a hierarchical manner.
* formFields can be used for persisting concepts like the date of collection, patient demographics, medications, allergies, and clinical observations


## Available operations for Forms

1.  [List Forms](#search-forms)
3.  [Create a form](#create-a-form) 
4.  [Update a form](#update-a-form)
5.  [Delete a form](#delete-a-form)
6.  [List formfields](#list-formfields)
7.  [Create formFields subresource with properties](#create-formfield-subresource-with-properties)
8.  [Update formFields subresource with properties](#update-formfields-subresource-with-properties)
9.  [Delete formFields subresource with properties](#delete-formfields-subresource-with-properties)


## List Forms

> List Forms

```shell
GET /form?v=full&limit=1
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/form?v=full&limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/form?v=full&limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "d2c7532c-fb01-11e2-8ff2-fd54ab5fdb2a",
            "display": "Admission (Simple)",
            "name": "Admission (Simple)",
            "description": null,
            "encounterType": {
                "uuid": "e22e39fd-7db2-45e7-80f1-60fa0d5a4378",
                "display": "Admission",
                "name": "Admission",
                "description": "Indicates that the patient has been admitted for inpatient care, and is not expected to leave the hospital unless discharged.",
                "retired": false,
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encountertype/e22e39fd-7db2-45e7-80f1-60fa0d5a4378"
                    },
                    {
                        "rel": "full",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/encountertype/e22e39fd-7db2-45e7-80f1-60fa0d5a4378?v=full"
                    }
                ],
                "resourceVersion": "1.8"
            },
            "version": "1.0",
            "build": null,
            "published": false,
            "formFields": [],
            "retired": false,
            "auditInfo": {
                "creator": {
                    "uuid": "A4F30A1B-5EB9-11DF-A648-37A07F9C90FB",
                    "display": "daemon",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/user/A4F30A1B-5EB9-11DF-A648-37A07F9C90FB"
                        }
                    ]
                },
                "dateCreated": "2017-01-18T08:54:11.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "resources": [],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/form/d2c7532c-fb01-11e2-8ff2-fd54ab5fdb2a"
                }
            ],
            "resourceVersion": "1.9"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/form?v=full&limit=1&startIndex=1"
        }
    ]
}

```

* Fetch all non-retired Forms that match any specified parameters otherwise fetch all non-retired forms. Returns a `200 OK` status with the form response, and returns a `401` response when the user is not logged in. 

### Query Parameters

    Parameter | Description
    --- | ---
    *limit* | use this parameter to limit the number of results to be returned 
    *startIndex* | the offset where to start the query
    *v* | the required representation to return (i.e., ref, default, full or custom )
    *q* | the search query
    
    

## List forms by UUID

> List forms by UUID

```shell
GET /form/:target_form_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/form/d2c7532c-fb01-11e2-8ff2-fd54ab5fdb2a")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/form/d2c7532c-fb01-11e2-8ff2-fd54ab5fdb2a", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Retrieve a form by its UUID. Returns a `404 Not Found` status if the form does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.
    

## Create-a-form

```shell

POST /form
{
  "name": "Admission",
  "description": "dummy description",
  "version": "1.0",
  "encounterType": "Vitals",
  "published": true,
  "formFields": [
    "medication","allergies"
  ]
}
```

* To create a Form, you need to specify the below properties in the request. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

    ### Properties

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | name of the form resource to be created
    *description* | `String` | description of the form resource to be created
    *version* | `String` | current version of the form resource to be created
    *[encouterType](#encounter-type)* | `Encounter type UUID` | the specific encounter type where this form is designed to collect data for e.g. vitals,admission.
    *published* | `boolean` | whether the form has been published or not
    *formFields* | `Array[]: formFields` | list of formFields associated with this form

## Update a form

```console
POST /form/:target_form_uuid
{
  "name": "Admission",
  "description": "dummy description",
  "version": "1.0",
  "encounterType": "Vitals",
  "published": true,
  "formFields": [
    "medication","allergies"
  ]
}
```


* Update a target Form with given UUID, this method only modifies properties in the request. 
Returns a `404 Not Found` status if form not exists. If the user is not logged in to perform this action, a `401 Unauthorized status returned`.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_form_uuid` | Target form resource UUID

    ### Properties

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | name of the form resource to be created
    *description* | `String` | description of the form resource to be created
    *version* | `String` | current version of the form resource to be created
    *encouterType* | `String` | the specific encounter type where this form is designed to collect data
    *published* | `boolean` | whether the form has been published or not
    *formFields* | `Array[]: formFields` | list of formFields associated with this form
    *xslt* | `String` | specifying XSLT description for the form if it supports XSLT transformations
    *template* | `String` | template of the form to be created 


## Delete a form

```console
DELETE /form/:target_form_uuid?purge=true
```

* Delete or retire a target form by its UUID. Returns a `404 Not Found` status if the form does not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    **uuid** | `String` | uuid to delete
    *purge* | `Boolean` | The form will be voided/retired unless purge = 'true'


## List formfields

### List all formFields subresources for a form.

```console
GET /form/:target_form_uuid/formFields
```  

    Retrieve all formFields subresources of a form resource by `target_form_uuid`. Returns a `404 Not Found` status if formFields not exist. If the user is not logged in to perform this action, a `401 unauthorized` status returned.

### List formFields subresource by its UUID and parent form UUID.

```console
GET /form/:target_form_uuid/formFields/:target_formFields_uuid
```

    Retrieve a formFields subresources of a form resource. Returns a `404 Not Found` status if formFields does not exist. If you are not logged in to perform this action, a `401 Unauthorized` status returned. 

## create formfield subresource with properties 

```console
POST form/:target_form_uuid/formFields
{
  form: "UUID",
  field: "UUID",
  required: false,
  parent: "UUID",
  fieldNumber: 2,
  fieldPart: "4",
  pageNumber: 1,
  minOccurs: 0,
  maxOccurs: 1,
  sortWeight: false
}
```

* To create a formFields subresource for a specific form resource, you need to specify below properties in your request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query parameter 
    Parameter | Description
    --- | ---
    `target_form_uuid` | form resource uuid

    ### Properties for resource

    Parameter | Type | Description
    --- | --- | ---
    *form* | `String` | UUID of the parent form resource
    *field* | `String` | UUID of the formField to be created for the parent form
    *required* | `String` | if this field is required for the form to be submitted or not
    *parent* | `String` | parent form of this formField
    *fieldNumber* | `integer` | the number specified to this field in form
    *fieldPart* | `String` | the part specified to this field (like 1.4) here 4 is the field part and 1 is the field number.
    *PageNumber* | `String` | the page number where this field appears on the form
    *minOccurs* | `integer` | the minimum number of times this field appears on the form
    *maxOccurs* | `integer` | the maximum number of times this field appears on the form
    *sortWeight* | `boolean` | do we order this field or not, when this field will be searched for 

## Update formFields subresource with properties

```console
POST form/:target_form_uuid/formFields/:target_formFields_uuid
{
  form: "UUID",
  field: "UUID",
  required: false,
  parent: "UUID",
  fieldNumber: 2,
  fieldPart: "4",
  pageNumber: 1,
  minOccurs: 0,
  maxOccurs: 1,
  sortWeight: false
}
```

* Updates a formFields subresource value with given UUID. This method will only modify the value of the subresource. Returns a `404 Not Found` status if attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Query parameter 
    Parameter | Description
    --- | ---
    `target_form_uuid` | form resource uuid
    `target_formFields_uuid` | formFields subresource uuid


    ### Properties

    Parameter | Type | Description
    --- | --- | ---
   *form* | `String` | UUID of the parent form resource
    *field* | `String` | UUID of the formField to be created for the parent form
    *required* | `String` | if this field is required for the form to be submitted or not
    *parent* | `String` | parent form of this formField
    *fieldNumber* | `integer` | the number specified to this field in form
    *fieldPart* | `String` | the part specified to this field (like 1.4) here 4 is the field part and 1 is the field number.
    *PageNumber* | `String` | the page number where this field appears on the form
    *minOccurs* | `integer` | the minimum number of times this field appears on the form
    *maxOccurs* | `integer` | the maximum number of times this field appears on the form
    *sortWeight* | `boolean` | do we order this field or not, when this field will be searched for 



## Delete formFields subresource with properties

```console
DELETE /form/:target_form_uuid/formFields/:target_formFields_uuid
```

* Delete or retire a target formFields subresource by its UUID. Returns a `404 Not Found` status if attribute not exists. 
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    **uuid** | `String` | uuid of parent form to delete
    **uuid** | `String` | uuid of formFields to delete
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    

