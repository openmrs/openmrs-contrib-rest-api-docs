# Concepts
  
## Concepts Overview

* The concept is the basic element of flexibility in OpenMRS. Concepts are the individual data points collected from a 
population of patients. Concepts include both questions and answers. 

* For example, blood type data is collected for a patient.  The question is "What is the blood type for the patient?", with a
set of discrete answers of "A, B, AB or O".  To implement this in OpenMRS with concepts, the question is a concept 
("blood type") and each response ("A", "B", "AB" and "O") is also a concept.  For this one question, a total of 5 concepts 
are required.

* What about a question where the answer is not a discrete answer?  If the question is "What is the name of your first pet?",
the answer would be expressed in a text box.  It would not be possible to provide a complete list of every possible name for
your pet.  In this example, there would be one concept -- "name of first pet".

* The bottom line is, if you need a medical word within your electronic records system, it needs to be defined within the 
concept dictionary.  More detail about all the possible concepts in a later section.
  
## Sub Resource types of Concepts

### Concept Attribute.

* If you wish to record extra information about concept, you can create Concept Attributes and assign them to Concept Types.

* Concept attributes exists specifically to allow implementations to extend the data model.

### Concept Name.

* ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale. 
Because there may be many names for any concept.

### Concept Mapping.

* Concept Mappings are added to facilitate managing concept dictionaries and point to other concepts which have the same meaning. 
Mappings are useful when you need to receive or send information to external systems, letting you define how your system's
 concepts relate to external concepts such as standardized medical vocabularies (e.g., ICD, LOINC, SNOMED).

* For example, add a mapping to a concept in the MCL dictionary. You can save the concept now and create some answers.

### Concept Description.

* A clear and concise description of the concept, as agreed upon by the members of the organization or the most commonly 
referenced source.  

## Available operations for Concepts 
 
1.  [List concepts](#list-concepts)
2.  [Create a concept](#create-a-concept)
3.  [Update a concept](#update-a-concept)
4.  [Delete a concept](#delete-a-concept)
5.  [List concept mapping](#list-concept-mapping)
6.  [Create concept mapping with properties](#create-a-concept-mapping-with-properties)
7.  [Update concept mapping](#update-a-concept-mapping)
8.  [Delete concept mapping](#delete-a-concept-mapping)
9.  [List concept name](#list-concept-name)
10. [Create concept name with properties](#create-a-concept-name-with-properties)
11. [Update concept name](#update-concept-name)
12. [Delete concept name](#delete-concept-name)
13. [List concept attribute](#list-concept-attribute)
14. [Create concept attribute with properties](#create-a-concept-attribute-with-properties)
15. [Update concept attribute](#update-concept-attribute)
16. [Delete concept attribute](#delete-concept-attribute)
13. [List concept description](#list-concept-descriptions)
14. [Create concept description with properties](#create-a-concept-description-with-properties)
15. [Update concept description](#update-concept-description)
16. [Delete concept description](#delete-concept-description


## List concepts

* ### List all concepts.
    
    Quickly filter concepts with given query parameters.Returns a `404 Not Found` status if concepts not exists. If user not logged 
    in to perform this action,a `401 Unauthorized` status returned.
    
    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of concept object
    *code* | `String` |  Represents a name from a standard medical code
    *name* | `String` | ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale
    *term* | `String` | Medical coding term or OpenMRS concept dictionary term that could be mapped to a concept
    *source* | `String` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (ie. LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc), but the concept source can also be a custom (ie. org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database
    *class* | `String` | The concept's class provides a useful way to narrow down the scope of the information that the concept is intended to capture.  In this way, the class is helpful for data extraction.  This classification details how a concept will be represented (i.e. as a question or an answer) when the information is stored.  OpenMRS contains several default classes to use when defining concepts, but implementation sites may also create additional custom concept classes for use.
    
```console
GET /concept?
  term=38341003
  &source=SNOMED%20CT
 ```
    
* ### Query concept by UUID.

    Retrieve an concepts by its UUID. Returns a `404 Not Found` status if concepts not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
```console
GET /concept/:target_concept_uuid
```
   
## Create a concept

* To Create an concept you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale (required)
    *datatype* | `target_concept_datatype_uuid` | A concept datatype prescribes the structured format by which you desire the data to be represented. In simple terms, the datatype defines the type of data that the concept is intended to collect (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept (required)
    *answers* | `Array of Child Concepts` | An array of concepts which are answers for the current concept 
    *setMembers* | `Array of Child Concepts` | Describes the questions contained by a concept set. Each set member is a question concept in and of itself    
    *units* | `String` | Standard unit used to measure the concept
    *allowDecimal* | `String` | Allow to use decimals
    *conceptClass* | `target_concept_class_uuid` | The classification of a concept. This classification details how a concept will be represented (i.e. as a question or an answer) (required)
    *descriptions* | `Array[] String` | A concept map connects a concept term to a concept
    *mappings* | `Array[] String` | Connects a concept term to a concept.  
   
```console
POST /concept
{
  "names": [
    {
      "name": "What is the blood type for the patient?",
      "locale": "en",
      "localePreferred": true,
      "conceptNameType": "FULLY_SPECIFIED"
    }
  ],
  "datatype": "8d4a4c94-c2cc-11de-8d13-0010c6dffd0f",
  "version": "1.2.2",
  "conceptClass": "8d492774-c2cc-11de-8d13-0010c6dffd0f"
}
```
## Update a concept

*  Update a target concept with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *names* | `String` | ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale (required)
    *datatype* | `target_concept_datatype_uuid` | A concept datatype prescribes the structured format by which you desire the data to be represented. In simple terms, the datatype defines the type of data that the concept is intended to collect (required)
    *version* | `String` | A method to keep track of the number of updates applied to a specific concept (required)
    *answers* | `Array of Child Concepts` | An array of concepts which are answers for the current concept 
    *setMembers* | `Array of Child Concepts` | Describes the questions contained by a concept set. Each set member is a question concept in and of itself    
    *units* | `String` | Standard unit used to measure the concept
    *allowDecimal* | `String` | Allow to use decimals
    *conceptClass* | `target_concept_class_uuid` | The classification of a concept. This classification details how a concept will be represented (i.e. as a question or an answer) (required)
    *descriptions* | `Array[] String` | A concept map connects a concept term to a concept
    *mappings* | `Array[] String` | Connects a concept term to a concept.  

```console
POST /concept/:target_concept_uuid
{
  "names": [
    {
      "name": "What is the blood type for the sick patient?",
      "locale": "en",
      "localePreferred": true,
      "conceptNameType": "FULLY_SPECIFIED"
    }
  ],
  "datatype": "8d4a4c94-c2cc-11de-8d13-0010c6dffd0f",
  "version": "1.2.2",
  "conceptClass": "8d492774-c2cc-11de-8d13-0010c6dffd0f"
}
```
    
## Delete a concept

* Delete or retire a target concept by its UUID. Returns a `404 Not Found` status if concept not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’

```console
DELETE /concept/:target_concept_uuid?purge=true
```
## List concept mapping

* ### List all concept mappings for a concept.

    Retrieve all **concept mapping** sub resources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if concept mapping not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

```console
GET /concept/:target_concept_uuid/mapping 
```

* ### List concept mapping by it's UUID and parent concept UUID.
    
     Retrieve an **concept mapping** sub resources of a **concept** resource. Returns a 
     `404 Not Found` status if concept mapping not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
```console
GET /concept/:target_concept_uuid/mapping/:target_concept_mapping_uuid
```
## Create a concept mapping with properties

* To Create a concept mapping sub resource for a specific concept resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *conceptReferenceTerm* | `target_concept_reference_term_type_uuid` | A concept term defines a medical coding term or OpenMRS concept dictionary term that could be mapped to a concept (required)
    *conceptMapType* | `target_concept_map_type_uuid` | A concept map connects a concept term to a concept (required)
    
```console
POST concept/:target_concept_uuid/mapping
{
  "conceptReferenceTerm": "21fb14d7-5cd9-3621-ac30-c9e57320e233",
  "conceptMapType": "35543629-7d8c-11e1-909d-c80aa9edcf4e"
}
```
 
 
## Update a concept mapping

* Updates an concept mapping sub resource value with given uuid, this method will only modify value of the sub resource. Returns 
a `404 Not Found` status if concept mapping not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *conceptReferenceTerm* | `target_concept_reference_term_type_uuid` | A concept term defines a medical coding term or OpenMRS concept dictionary term that could be mapped to a concept (required)
    *conceptMapType* | `target_concept_map_type_uuid` | A concept map connects a concept term to a concept (required)

```console
POST concept/:target_concept_uuid/mapping
{
  "conceptReferenceTerm": "21fb14d7-5cd9-3621-ac30-c9e57320e233",
  "conceptMapType": "35543629-7d8c-11e1-909d-c80aa9edcf4e"
}
```
## Delete a concept mapping

* Delete or Voided a target concept mapping sub resource by its UUID. Returns a `404 Not Found` status if concept mapping not exists. 
 If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to irreversibly remove the concept mapping type from the system. Concept mapping types that have been used (i.e., are referenced from existing data) cannot be purged.
    
```console
DELETE concept/:target_concept_uuid/mapping/:target_concept_mapping_uuid
```
## List concept name

* ### List all concept names for a concept.

    Retrieve all **concept name** sub resources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if concept name not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

```console
GET /concept/:target_concept_uuid/name 
```

* ### List concept name it's UUID and parent concept UUID.
    
     Retrieve an **concept name** sub resources of a **concept** resource. Returns a 
     `404 Not Found` status if concept name not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
```console
GET /concept/:target_concept_uuid/name/:target_concept_name_uuid
```
## Create a concept name with properties

* To Create a concept name sub resource for a specific concept resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the concept (required)
    *locale* | `String` | Language to record concept name (required)
    *localePreferred* | `String` | This is the preferred name to use within a locale.  By default, this is the fully-specified name; however, full-specified names are sometimes long and more detailed than necessary for day-to-day use.  In those cases, a synonym can be defined to be the locale-preferred name.  There can only be one preferred name within a locale.  The primary term should be the word(s) used most often by those who will have access to the records to prevent duplicate concept creation.
    *conceptNameType* | `String` | Type of the name to be specified.
    
```console
POST concept/:target_concept_uuid/name
{
  "name": "Bronchospasm",
  "locale": "en",
  "localePreferred": true,
  "conceptNameType": "FULLY_SPECIFIED"
}
```
 
 
## Update concept name

* Updates an concept name sub resource value with given uuid, this method will only modify value of the sub resource. Returns 
a `404 Not Found` status if concept name not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the concept (required)
    *locale* | `String` | Language to record concept name (required)
    *localePreferred* | `String` | This is the preferred name to use within a locale.  By default, this is the fully-specified name; however, full-specified names are sometimes long and more detailed than necessary for day-to-day use.  In those cases, a synonym can be defined to be the locale-preferred name.  There can only be one preferred name within a locale.  The primary term should be the word(s) used most often by those who will have access to the records to prevent duplicate concept creation.
    *conceptNameType* | `String` | Type of the name to be specified.

```console
POST concept/:target_concept_uuid/name
{
  "name": "Bronchospasm",
  "locale": "en",
  "localePreferred": true,
  "conceptNameType": "FULLY_SPECIFIED"
}
```
## Delete concept name

* Delete or retire a target concept name sub resource by its UUID. Returns a `404 Not Found` status if concept name not exists. 
 If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to irreversibly remove the concept name type from the system. Concept name types that have been used (i.e., are referenced from existing data) cannot be purged.
    
```console
DELETE concept/:target_concept_uuid/name/:target_concept_name_uuid
```

## List concept attribute

* ### List all concept attributes for a concept.

    Retrieve all **concept attribute** sub resources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if concept attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

```console
GET /concept/:target_concept_uuid/attribute 
```

* ### List concept attribute by it's UUID and parent concept UUID.
    
     Retrieve an **concept attribute** sub resources of a **concept** resource. Returns a 
     `404 Not Found` status if concept attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
```console
GET /concept/:target_concept_uuid/attribute/:target_concept_attribute_uuid
```
## Create a concept attribute with properties

* To Create a concept attribute sub resource for a specific concept resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Concept Attribute_Type (required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (required)
    
```console
POST concept/:target_concept_uuid/attribute
{
  "attributeType": "target_concept_attribute_type_uuid",
  "value": "value_for_the_attriute"
}
```
 
 
## Update concept attribute

* Updates an concept attribute sub resource value with given uuid, this method will only modify value of the sub resource. Returns 
a `404 Not Found` status if concept attribute not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Concept Attribute_Type (required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (required)

```console
POST concept/:target_concept_uuid/attribute
{
  "attributeType": "target_concept_attribute_type_uuid",
  "value": "value_for_the_attriute"
}
```
## Delete concept attribute

* Delete or retire a target concept attribute sub resource by its UUID. Returns a `404 Not Found` status if concept attribute not exists. 
 If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to irreversibly remove the concept name type from the system. Concept name types that have been used (i.e., are referenced from existing data) cannot be purged.
    
```console
DELETE concept/:target_concept_uuid/attribute/:target_concept_attribute_uuid
```
    
## List concept descriptions

* ### List all concept descriptions for a concept.

    Retrieve all **concept description** sub resources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if concept description not exists. If user not logged in to perform this action, a `401 Unauthorized` status
    returned.

```console
    GET /concept/:target_concept_uuid/description 
```

* ### List concept description by it's UUID and parent concept UUID.
    
     Retrieve an **concept description** sub resources of a **concept** resource. Returns a 
     `404 Not Found` status if concept description not exists. If you are not logged in to perform this action, a `401 Unauthorized` status
     returned.
     
```console
GET /concept/:target_concept_uuid/description/:target_concept_description_uuid
```
## Create a concept description with properties

* To Create a concept description sub resource for a specific concept resource you need to specify below attributes in the request body.
If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *description* | `String` | Description text to e provided for the concept (required)
    *locale* | `String` | Language description provided by (required)
    
```console
POST concept/:target_concept_uuid/description
{
  "description": "Pregnancy terminated by a spontaneous abortion.",
  "locale": "en"
}
```
 
 
## Update concept description

* Updates an concept description sub resource value with given uuid, this method will only modify value of the sub resource. Returns 
a `404 Not Found` status if concept description not exists. If user not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *description* | `String` | Description text to e provided for the concept (required)
    *locale* | `String` | Language description provided by (required)

```console
POST concept/:target_concept_uuid/description
{
  "description": "Pregnancy terminated by a spontaneous abortion.",
  "locale": "en"
}
```
## Delete concept description

* Delete or retire a target concept description sub resource by its UUID. Returns a `404 Not Found` status if concept description not exists. 
 If user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to irreversibly remove the concept description  from the system. Concept description that have been used (i.e., are referenced from existing data) cannot be purged.
    
```console
DELETE concept/:target_concept_uuid/description/:target_concept_description_uuid
```

