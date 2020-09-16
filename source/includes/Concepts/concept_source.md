# Concept Source

## Concept Source Overview

* Concepts are often managed within a dictionary (as a collection of concepts). While OpenMRS has, it's own dictionary of concepts, other dictionaries may exist in other systems or as standardized reference terminologies (like LOINC or ICD). The authorities who manage these other concept dictionaries represent "Concept Sources."
* For eg `PIH Malawi`:`Partners in Health Malawi concept dictionary`, `SNOMED CT`:`SNOMED Preferred mapping` etc.


## Available operations for Concept Source. 

1. [List concept_source types](#list-concept-source)
2. [Create a concept_source](#create-a-concept-source)
3. [Update a concept_source type](#update-a-concept-source)
4. [Delete a concept_source type](#delete-a-concept-source)


## List concept source

### List all non-retired concept source.

```shell
GET /conceptsource/conceptsource?q=pih&limit=1
```
```response
{
    "results": [
        {
            "uuid": "fb9aaaf1-65e2-4c18-b53c-16b575f2f385",
            "display": "PIH",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource/fb9aaaf1-65e2-4c18-b53c-16b575f2f385"
                }
            ]
        }
    ],
    "links": [
        {
            "rel": "next",
            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/conceptsource?q=pih&limit=1&startIndex=1"
        }
    ]
}
```
    Quickly filter concept source types with a given search query. Returns a `404 Not Found` status if concept source type not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.
    
    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `String` | Full or partial match to concept source name. Search is case-insensitive for eg. PIH

    
### Query concept source by UUID.

```shell
GET /conceptsource/:target_concept_source_type_uuid
```
    Retrieve a concept source type by its UUID. Returns a `404 Not Found` status if concept source type not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create a concept source

```console
POST /conceptsource
{
  "name": "SNOMED CT",
  "description": "SNOMED Preferred mapping",
  "hl7Code": "SCT"
}
```
* To Create a concept source type you need to specify below attributes in the request body. If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept source type (Required)
    *description* | `String` | Description for the concept source type resource (Required)
    *hl7Code* | `String` | A short code defined by governing bodies like HL7 (as in Vocabulary Table 0396). Alternatively, this could be the "Implementation Id" code used by another OpenMRS installation to define its concepts and forms
    *uniqueId* | `String` | A globally unique id to for the concept source
   
## Update a concept source

```console
POST /conceptsource
{
 "name": "SNOMED CTS",
 "description": "SNOMED Preferred mapping",
 "hl7Code": "SCT"
}
```
*  Update a target concept source type with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if concept source not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the concept source type
    *description* | `String` | Description for the concept source type resource
    *hl7Code* | `String` | The 5-20 character code defined for this source by governing bodies. Alternatively, this could be the "Implementation Id" code used by another OpenMRS installation to define its concepts and forms
    *uniqueId* | `String` | A globally unique id to for the concept source
    
    
## Delete a concept source

```console
DELETE /conceptsource/:target_concept_source_type_uuid?purge=true
```
* Delete or Retire a target concept source type by its UUID. Returns a `404 Not Found` status if concept source not exists. If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

