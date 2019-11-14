# Forms

## Overview

* A Form represents an electronic form that may be used for entering or viewing data. The basic OpenMRS system does not define 
a specific technology for entering forms. You will need to use one of the community-developed form entry modules. See the 
chapter "Data Entry" for more details.

* The Form Entry (Infopath) and XForms modules rely on a Form Schema, where you define which Concepts are used on the Form. 
The HTML Form Entry module does not require you to manage the schema.
  
## Sub Resource types

### Forms Formfield.

* If you wish to record extra information about concept, you can create Concept Attributes and assign them to Concept Types.

* Concept attributes exists specifically to allow implementations to extend the data model.

### Forms Resource.

* ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale. 
Because there may be many names for any concept.


## Available operations. 
1.  [List forms](#list-forms)
2.  [Create a form](#create-a-form)
3.  [Update a form](#update-a-form)
4.  [Delete a form](#delete-a-form)
5.  [List form field sub resource](#list-form-field-sub-resources)
6.  [Create form field sub resource with properties](#create-a-form-field-sub-resource-with-properties)
7.  [Update form field sub resource](#update-a-form-field-sub-resource)
8.  [Delete form field sub resource](#delete-a-form-field-sub-resource)
9.  [List form resource sub resource](#list-form-resource-sub-resources)
10. [Create form resource sub resource with properties](#create-a-form-resource-sub-resource-with-properties)
11. [Update form resource sub resource](#update-form-resource-sub-resource)
12. [Delete form resource sub resource](#delete-form-resource-sub-resource)


### List forms

* #### List all forms.

    Quickly filter forms with given query parameters.Returns a `404 Not Found` status if forms not exists. If user not logged 
    in to perform this action,a `401 Unauthorized` status returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of forms object
 
    ```console
    GET /form?
      q=Admission
     
     ```

* #### Query forms by UUID.

    Retrieve an forms by its UUID. Returns a `404 Not Found` status if forms not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /form/:target_form_uuid
    ```

### Create a form

* To Create an forms you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the form (required)
    *description* | `String` | Description for the form
    *version* | `String` | A method to keep track of the number of updates applied to a specific form (required)
    *encounterType* | `target_encounter_UUID` | Encounter type to be used for the form (required)
    *published* | `String` | Status of the form published or not
    *formFields* | `Array[] target_form_field_UUID` | Form fields to be included in the form
    *xslt* | `String` |  Define XSLT for the form if needs to translates the submitted form data (within FormEntry) into HL7

    ```console
        POST /form
        {
          "name": "Admission (Simple)",
          "version": "1.0",
          "encounterType": "e22e39fd-7db2-45e7-80f1-60fa0d5a4378",
          "published": false,
          "formFields": []
        }
    ```
### Update a form

*  Update a target forms with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if forms not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | Name for the form (required)
    *description* | `String` | Description for the form
    *version* | `String` | A method to keep track of the number of updates applied to a specific form (required)
    *encounterType* | `target_encounter_UUID` | Encounter type to be used for the form (required)
    *published* | `String` | Status of the form published or not
    *formFields* | `Array[] target_form_field_UUID` | Form fields to be included in the form
    *xslt* | `String` |  Define XSLT for the form if needs to translates the submitted form data (within FormEntry) into HL7

    ```console
        POST /form/:target_form_uuid
        {
          "name": "Admission (Simple)",
          "version": "1.0",
          "encounterType": "e22e39fd-7db2-45e7-80f1-60fa0d5a4378",
          "published": false,
          "formFields": []
        }
    ```

### Delete a form

* Delete or retire a target forms by its UUID. Returns a `404 Not Found` status if forms not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

    ```console
        DELETE /form/:target_form_uuid?purge=true
     ```
### List form field sub resources

* #### List all form field sub resources for a concept.

    Retrieve all **form field** sub resources of a **form** resource by target_form_uuid. Returns a 
    `404 Not Found` status if form field not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

    ```console
        GET /form/:target_form_uuid/formfield 
    ```

* #### List form field sub resources by it's UUID and parent concept UUID.

     Retrieve an **form field** sub resources of a **form** resource. Returns a 
     `404 Not Found` status if form field not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.

    ```console
        GET /form/:target_form_uuid/formfield/:target_form_field_uuid
    ```
### Create a form field sub resource with properties

* To Create a form field sub resource for a specific form resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *form* | `target_form_uuid` | UUID of the parent form (required)
    *field* | `target_field_uuid` | UUID of the target field to be included (required)
    *required* | `Boolean` | Indicates whether the form element should be required 
    *fieldNumber* | `target_concept_map_type_uuid` |  The field number corresponding to the actual form element in your form. This value may be left blank
    *fieldPart* | `target_concept_map_type_uuid` | The sub field number/letter corresponding to the actual form element in your form (i.e. 'a' in 1a). This value may be left blank
    *pageNumber* | `target_concept_map_type_uuid` | : The page number where this form element appears. This value may be left blank
    *minOccurs* | `target_concept_map_type_uuid` | The minimum number of times that this form element should appear on the form. This value may be left blank. Default = 0
    *maxOccurs* | `target_concept_map_type_uuid` | The maximum number of times that this form element should appear on the form. This value may be left blank. Default = 1. Use -1 to allow for an arbitrary number of values, for example, if you intend to use a 
    *sortWeight* | `target_concept_map_type_uuid` | Based on the value the order this form field will appear in when searched

    ```console
        POST form/:target_form_uuid/formfield
        {
          "form": "a000cb34-9ec1-4344-a1c8-f692232f6edd",
          "field": "92d94c32-d13f-461d-9738-bfd3f8bb111c",
          "required": true,
          "fieldPart": "1",
          "pageNumber": 0,
          "minOccurs": 0,
          "maxOccurs": 0,
          "sortWeight": true
        }
    ```


### Update a form field sub resource

* Updates form field sub resource value with given uuid, this method will only modify value of the sub resource. Returns 
a `404 Not Found` status if concept mapping not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *form* | `target_form_uuid` | UUID of the parent form
    *field* | `target_field_uuid` | UUID of the target field to be included
    *required* | `Boolean` | Indicates whether the form element should be required
    *fieldNumber* | `target_concept_map_type_uuid` |  The field number corresponding to the actual form element in your form. This value may be left blank
    *fieldPart* | `target_concept_map_type_uuid` | The sub field number/letter corresponding to the actual form element in your form (i.e. 'a' in 1a). This value may be left blank
    *pageNumber* | `target_concept_map_type_uuid` | : The page number where this form element appears. This value may be left blank
    *minOccurs* | `target_concept_map_type_uuid` | The minimum number of times that this form element should appear on the form. This value may be left blank. Default = 0
    *maxOccurs* | `target_concept_map_type_uuid` | The maximum number of times that this form element should appear on the form. This value may be left blank. Default = 1. Use -1 to allow for an arbitrary number of values, for example, if you intend to use a 
    *sortWeight* | `target_concept_map_type_uuid` | Based on the value the order this form field will appear in when searched.
  
   ```console
        POST form/:target_form_uuid/formfield
        {
          "form": "a000cb34-9ec1-4344-a1c8-f692232f6edd",
          "field": "92d94c32-d13f-461d-9738-bfd3f8bb111c",
          "required": true,
          "fieldPart": "1",
          "pageNumber": 0,
          "minOccurs": 0,
          "maxOccurs": 0,
          "sortWeight": true
        }
    ```
    
### Delete a form field sub resource

* Delete or Retire a target form field sub resource by its UUID. Returns a `404 Not Found` status if form field not exists. 
 If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to irreversibly remove the concept mapping type from the system. Concept mapping types that have been used (i.e., are referenced from existing data) cannot be purged.

     ```console
        DELETE form/:target_form_uuid/formfield/:target_form_field_uuid
     ```
     
### List form resource sub resources

* #### List all form resource sub resources for a concept.

    Retrieve all **form resource** sub resources of a **form** resource by target_form_uuid. Returns a 
    `404 Not Found` status if form resource not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

    ```console
        GET /form/:target_form_uuid/resource 
    ```

* #### Query form resource sub resources by it's UUID and parent concept UUID.

     Retrieve an **form resourc** sub resources of a **form** resource. Returns a 
     `404 Not Found` status if form resource not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.

    ```console
        GET /form/:target_form_uuid/resource/:target_form_resource_uuid
    ```
### Create a form resource sub resource with properties

* To Create a form resource sub resource for a specific form resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *form* | `String` | UUID of the form (required)
    *name* | `String` | Name of the form resource (required)
    *dataType* | `String` | Data type for the attribute type resource.OpenMRS provides Custom data type resource which gives flexibility to select the data type accordingly (Required).
    *handler* | `String` | Name of the handler to be used 
    *handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list and this configuration would tell the handler the possible choices in the list for this specific attribute type
    *value* | `String` | Value for the form resource

    ```console
        POST form/:target_form_uuid/resource
        {
          "form": "a000cb34-9ec1-4344-a1c8-f692232f6edd",
          "name": "form resource",
          "dataType": "default",
          "handler": "default",
        }
    ```


### Update form resource sub resource

* Updates an orm resource sub resource value with given uuid, this method will only modify value of the sub resource. Returns 
a `404 Not Found` status if concept name not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *form* | `String` | UUID of the form (required)
    *name* | `String` | Name of the form resource (required)
    *dataType* | `String` | Data type for the attribute type resource.OpenMRS provides Custom data type resource which gives flexibility to select the data type accordingly (Required).
    *handler* | `String` | Name of the handler to be used 
    *handlerConfig* | `String` | Allow handler to be used for more than one attribute type. The actual configuration depends on the needs of the specified handler. For example, a "Pre-defined List" handler could be made to implement a simple selection list and this configuration would tell the handler the possible choices in the list for this specific attribute type
    *value* | `String` | Value for the form resource

    ```console
        POST form/:target_form_uuid/resource
        {
          "form": "a000cb34-9ec1-4344-a1c8-f692232f6edd",
          "name": "form resource",
          "dataType": "default",
          "handler": "default",
        }
    ```
### Delete form resource sub resource

* Delete or retire a target form resource sub resource by its UUID. Returns a `404 Not Found` status if form resource not exists. 
 If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to irreversibly remove the concept name type from the system. Form resource types that have been used (i.e., are referenced from existing data) cannot be purged.

     ```console
        DELETE form/:target_form_uuid/resource/:target_form_resource_uuid
     ```
