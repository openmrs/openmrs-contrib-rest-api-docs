# Concepts
  
## Concepts Overview

* The concept is the basic element of flexibility in OpenMRS. Concepts are the individual data points collected from a 
population of patients. Concepts include both questions and answers. 

* For example, blood type data is collected for a patient.  The question is, "What is the blood type for the patient?", with a
set of discrete answers of "A, B, AB or O."  We use concepts in OpenMRS to implement this. The question is a concept 
("blood type") and each response ("A," "B," "AB" and "O") is also a concept.  For this one question, a total of 5 concepts are required.

* What about a question where the answer is not a discrete answer?  If the question is "What is the name of your first pet?",
the answer would be expressed in a text box.  It would not be possible to provide a complete list of every possible name for
your pet.  In this example, there would be one concept -- "name of first pet."

* The bottom-line is that if you need a medical word within your electronic records system, it needs to be defined within the concept dictionary, more details about all the possible concepts will be given in a later section.
  
## Sub Resource types of Concepts

### Concept Attribute.

* If you wish to record extra information about concept, you can create Concept Attributes and assign them to Concept Types.

* Concept attributes exists specifically to allow implementations to extend the data model.

### Concept Name.

* ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale since there can be many names for any concept.

### Concept Mapping.

* Concept Mappings are added to facilitate managing concept dictionaries and point to other concepts that have the same meaning. 
Mappings are useful when you need to receive or send information to external systems, letting you define how your system's
 concepts relate to external concepts such as standardized medical vocabularies (e.g., ICD, LOINC, SNOMED).

* For example, add a mapping to a concept in the MCL dictionary. You can save the concept now and create some answers.

### Concept Description.

* A clear and concise description of the concept, as agreed upon by the organization's members or the most commonly 
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

### List all concepts.

```console
GET /concept?
  term=38341003
  &source=SNOMED%20CT
```

    Quickly filter concepts with given query parameters. Returns a `404 Not Found` status if concepts not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of concept object
    *code* | `String` |  Represents a name from a standard medical code
    *name* | `String` | ConceptNames are the words or phrases used to express the idea of a Concept within a particular locale
    *term* | `String` | Medical coding term or OpenMRS concept dictionary term that could be mapped to a concept
    *source* | `String` | A concept can have any number of mappings to any number of other vocabularies. Other vocabularies are called "concept sources" in OpenMRS (ie. LOINC, SNOMED, ICD-9, ICD10, RxNORM, etc), but the concept source can also be a custom (ie. org.openmrs.module.mdrtb, PIH, AMPATH, MVP, etc.). Every concept can define a string for its mapping in any "concept source" defined in the database
    *class* | `String` | The concept's class provides a useful way to narrow down the scope of the information that the concept is intended to capture.  In this way, the class is helpful for data extraction.  This classification elaborates how a concept will be represented (i.e. as a question or an answer) when the information is stored.  OpenMRS contains several default classes to use when defining concepts, but implementation sites may also create additional custom concept classes.
    
    
### Query concept by UUID.

```console
GET /concept/:target_concept_uuid
```
    Retrieve a concept by its UUID. Returns a `404 Not Found` status if concepts not exist. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create a concept

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
* To Create a concept, you need to specify below attributes in the request body. If you are not logged in to perform this action,
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
   

## Update a concept

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
*  Update a target concept with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.
    
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

    
## Delete a concept

```console
DELETE /concept/:target_concept_uuid?purge=true
```
* Delete or retire a target concept by its UUID. Returns a `404 Not Found` status if concept not exists. If the user is not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be retired unless purge = ‘true’


## List all concept mappings for a concept.

> List all concept mappings for a concept

```shell
GET /concept/:target_concept_uuid/mapping?limit=1 
```
```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping?limit=1")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ECE2890ED6EC0C39AB31295B5C17E254")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ECE2890ED6EC0C39AB31295B5C17E254");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping?limit=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "display": "ICD-10-WHO: O03.9",
            "uuid": "145917ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
            "conceptReferenceTerm": {
                "uuid": "0a0933ab-e97e-3f93-b319-8bb20ed50f64",
                "display": "ICD-10-WHO: O03.9",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptreferenceterm/0a0933ab-e97e-3f93-b319-8bb20ed50f64"
                    }
                ]
            },
            "conceptMapType": {
                "uuid": "43ac5109-7d8c-11e1-909d-c80aa9edcf4e",
                "display": "NARROWER-THAN",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptmaptype/43ac5109-7d8c-11e1-909d-c80aa9edcf4e"
                    }
                ]
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/145917ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/145917ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB?v=full"
                }
            ],
            "resourceVersion": "1.9"
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping?limit=1&startIndex=1"
        }
    ]
}

```

* Retrieve all **concept mapping** subresources of a **concept** resource by target_concept_uuid. Returns a `404 Not Found` status if concept mapping not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.


## List concept mapping by its UUID and parent concept UUID.

> List concept mapping by its UUID and parent concept UUID

```shell
GET /concept/:target_concept_uuid/mapping/:target_concept_mapping_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/133911ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ECE2890ED6EC0C39AB31295B5C17E254")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ECE2890ED6EC0C39AB31295B5C17E254");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/133911ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a **concept mapping** subresources of a **concept** resource. Returns a `404 Not Found` status if concept mapping not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
## Create a concept mapping with properties

> Create a concept mapping with properties

```shell
POST concept/:target_concept_uuid/mapping
{
  "conceptReferenceTerm": "21fb14d7-5cd9-3621-ac30-c9e57320e233",
  "conceptMapType": "35543629-7d8c-11e1-909d-c80aa9edcf4e"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"conceptReferenceTerm\": \"21fb14d7-5cd9-3621-ac30-c9e57320e233\",\r\n  \"conceptMapType\": \"35543629-7d8c-11e1-909d-c80aa9edcf4e\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/140AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=E84B91CD41B12C89101E366386887CF4")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=E84B91CD41B12C89101E366386887CF4");

var raw = JSON.stringify({"conceptReferenceTerm":"21fb14d7-5cd9-3621-ac30-c9e57320e233","conceptMapType":"35543629-7d8c-11e1-909d-c80aa9edcf4e"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/140AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* To Create a concept mapping subresource for a specific concept resource, you need to specify below attributes in the request body.If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*conceptReferenceTerm* | `target_concept_reference_term_type_uuid` | A [concept reference term](#concept-reference-term) defines a medical coding term or OpenMRS concept dictionary term that could be mapped to a concept (required)
*conceptMapType* | `target_concept_map_type_uuid` | A [concept map](#concept-map-type) connects a concept term to a concept (required)
    
 
 
## Update a concept mapping

> Update a concept mapping

```shell
POST concept/:target_concept_uuid/mapping
{
  "conceptReferenceTerm": "21fb14d7-5cd9-3621-ac30-c9e57320e233",
  "conceptMapType": "35543629-7d8c-11e1-909d-c80aa9edcf4e"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"conceptReferenceTerm\": \"21fb14d7-5cd9-3621-ac30-c9e57320e233\",\r\n  \"conceptMapType\": \"35543629-7d8c-11e1-909d-c80aa9edcf4e\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/140AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/101fea18-161e-4f86-9bd6-35300046c2b4")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=E84B91CD41B12C89101E366386887CF4")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=E84B91CD41B12C89101E366386887CF4");

var raw = JSON.stringify({"conceptReferenceTerm":"21fb14d7-5cd9-3621-ac30-c9e57320e233","conceptMapType":"35543629-7d8c-11e1-909d-c80aa9edcf4e"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/140AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/101fea18-161e-4f86-9bd6-35300046c2b4", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Updates a concept mapping subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if concept mapping not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status
returned.

### Attributes

Parameter | Type | Description
--- | --- | ---
*conceptReferenceTerm* | `target_concept_reference_term_type_uuid` | A [concept reference term](#concept-reference-term) defines a medical coding term or OpenMRS concept dictionary term that could be mapped to a concept (required)
*conceptMapType* | `target_concept_map_type_uuid` | A [concept map](#concept-map-type) connects a concept term to a concept (required)

## Delete a concept mapping

> Delete a concept mapping

```shell
DELETE concept/:target_concept_uuid/mapping/:target_concept_mapping_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/133911ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ECE2890ED6EC0C39AB31295B5C17E254")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ECE2890ED6EC0C39AB31295B5C17E254");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/concept/48AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/mapping/133911ABBBBBBBBBBBBBBBBBBBBBBBBBBBBB", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Voided a target concept mapping subresource by its UUID. Returns a `404 Not Found` status if concept mapping not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
* A `400 Bad Request` status is returned if the resource dosent support purging.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to remove the concept mapping type from the system irreversibly. Concept mapping types that have been used (i.e., are referenced from existing data) cannot be purged.
    
## List concept name

### List all concept names for a concept.

```console
GET /concept/:target_concept_uuid/name 
```
    Retrieve all **concept name** subresources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if concept name not exists. If the user isnot logged in to perform this action, a `401 Unauthorized` status returned.


### List concept name it's UUID and parent concept UUID.

```console
GET /concept/:target_concept_uuid/name/:target_concept_name_uuid
```    
     Retrieve a **concept name** subresources of a **concept** resource. Returns a 
     `404 Not Found` status if concept name not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
## Create a concept name with properties

```console
POST concept/:target_concept_uuid/name
{
  "name": "Bronchospasm",
  "locale": "en",
  "localePreferred": true,
  "conceptNameType": "FULLY_SPECIFIED"
}
```
* To Create a concept name subresource for a specific concept resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the concept (required)
    *locale* | `String` | Language to record concept name (required)
    *localePreferred* | `String` | This is the preferred name to use within a locale.  By default, this is the fully-specified name; however, full-specified names are sometimes long and more detailed than necessary for day-to-day use.  In those cases, a synonym can be defined to be the locale-preferred name.  There can only be one preferred name within a locale.  The primary term should be the word(s) used by those who will have access to the records to prevent duplication of concept creation.
    *conceptNameType* | `String` | Type of the name to be specified.
     
 
## Update concept name

```console
POST concept/:target_concept_uuid/name
{
  "name": "Bronchospasm",
  "locale": "en",
  "localePreferred": true,
  "conceptNameType": "FULLY_SPECIFIED"
}
```
* Updates a concept name subresource value with given UUID, this method will only modify value of the subresource. Returns a `404 Not Found` status if concept name not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name for the concept (required)
    *locale* | `String` | Language to record concept name (required)
    *localePreferred* | `String` | This is the preferred name to use within a locale.  By default, this is the fully-specified name; however, full-specified names are sometimes long and more detailed than necessary for day-to-day use.  In those cases, a synonym can be defined to be the locale-preferred name.  There can only be one preferred name within a locale.  The primary term should be the word(s) used most often by those who will have access to the records to prevent duplicate concept creation.
    *conceptNameType* | `String` | Type of the name to be specified.


## Delete concept name

```console
DELETE concept/:target_concept_uuid/name/:target_concept_name_uuid
```
* Delete or retire a target concept name subresource by its UUID. Returns a `404 Not Found` status if concept name not exists. 
 If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to remove the concept name type from the system irreversibly. Concept name types that have been used (i.e., are referenced from existing data) cannot be purged.
    

## List concept attribute


### List all concept attributes for a concept.

```console
GET /concept/:target_concept_uuid/attribute 
```
    Retrieve all **concept attribute** subresources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if a concept attribute not exists. If the user isnot logged in to perform this action, a `401 Unauthorized` status returned.


### List concept attribute by its UUID and parent concept UUID.

```console
GET /concept/:target_concept_uuid/attribute/:target_concept_attribute_uuid
```    
     Retrieve a **concept attribute** subresources of a **concept** resource. Returns a 
     `404 Not Found` status if a concept attribute not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
## Create a concept attribute with properties

```console
POST concept/:target_concept_uuid/attribute
{
  "attributeType": "target_concept_attribute_type_uuid",
  "value": "value_for_the_attriute"
}
```
* To Create a concept attribute subresource for a specific concept resource, you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Concept Attribute_Type (required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (required)
    
 
 
## Update concept attribute

```console
POST concept/:target_concept_uuid/attribute
{
  "attributeType": "target_concept_attribute_type_uuid",
  "value": "value_for_the_attriute"
}
```
* Updates a concept attribute subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if the concept attribute not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *attributeType* | `Attribute_Type UUID` | Create Attribute from this Concept Attribute_Type (required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (required)

## Delete concept attribute

```console
DELETE concept/:target_concept_uuid/attribute/:target_concept_attribute_uuid
```
* Delete or retire a target concept attribute subresource by its UUID. Returns a `404 Not Found` status if concept attribute not exists. 
 If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters 

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to remove the concept name type from the system irreversibly. Concept name types that have been used (i.e., are referenced from existing data) cannot be purged.
    
    
## List concept descriptions

### List all concept descriptions for a concept.

```console
    GET /concept/:target_concept_uuid/description 
```
    Retrieve all **concept description** subresources of a **concept** resource by target_concept_uuid. Returns a 
    `404 Not Found` status if concept description not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.


### List concept description by its UUID and parent concept UUID.

```console
GET /concept/:target_concept_uuid/description/:target_concept_description_uuid
```
     Retrieve a **concept description** subresources of a **concept** resource. Returns a 
     `404 Not Found` status if concept description not exists. If you are not logged in to perform this action, a `401 Unauthorized` status returned.
     
## Create a concept description with properties

```console
POST concept/:target_concept_uuid/description
{
  "description": "Pregnancy terminated by spontaneous abortion.",
  "locale": "en"
}
```
* To Create a concept description subresource for a specific concept resource you need to specify below attributes in the request body.
If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *description* | `String` | Description text to e provided for the concept (required)
    *locale* | `String` | Language description provided by (required)
    
 
 
## Update concept description

```console
POST concept/:target_concept_uuid/description
{
  "description": "Pregnancy terminated by spontaneous abortion.",
  "locale": "en"
}
```
* Updates a concept description subresource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if concept description not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status
returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *description* | `String` | Description text to e provided for the concept (required)
    *locale* | `String` | Language description provided by (required)

## Delete concept description

```console
DELETE concept/:target_concept_uuid/description/:target_concept_description_uuid
```
* Delete or retire a target concept description subresource by its UUID. Returns a `404 Not Found` status if concept description not exists. 
 If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided unless purge = ‘true’. Purging will attempt to remove the concept description from the system irreversibly. Concept descriptions that have been used (i.e., are referenced from existing data) cannot be purged.
    

