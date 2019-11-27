# Overview

Welcome to OpenMRS API documentation!.OpenMRS is a software platform and a reference application which enables design of a 
customized medical records system with no programming knowledge (although medical and systems analysis knowledge is required). 
It is a common platform upon which medical informatics efforts in developing countries can be built. The system is based on a
conceptual database structure which is not dependent on the actual types of medical information required to be collected or
on particular data collection forms and so can be customized for different uses.

This document provides High level documentation of OpenMRS APIs with code samples which are in the dark area to the right. If
anything missing or incorrect please inform us by creating a [GitHub Issue](https://github.com/openmrs/openmrs-contrib-rest-api-docs).

# OpenMRS REST API

This documentation serves as a reference to the bespoke [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) 
API for [OpenMRS](https://openmrs.org/).

# Getting Started

If you are new to openMRS checkout the [Getting Started as a Developer Guide](https://wiki.openmrs.org/display/docs/Getting+Started+as+a+Developer)
from openMRS

# Current version

* By default, all requests to `/openmrs/ws/rest` receive the v1 version of the REST API.

* The OpenMRS REST Web Services module includes dynamically generated documentation. For example, see the 
  [swagger documentation](https://demo.openmrs.org/openmrs/module/webservices/rest/apiDocs.htm) on the demo 
  server (username **admin**, password **Admin123**).

# Purpose

* The purpose of this documentation is to provide a brief and good taste and experience of the APIs that are used in OpenMRS community to the new developers so that can onboard in the projects within the org easily.

* The documentation also aims to assist the existing developers to get to know the conceptual context of the APIs and how they help the consumers during the interaction in the real world.

# Schema

All API access is over HTTPS, and can be accessed from `https://demo.openmrs.org/openmrs/ws/rest/v1`. All data is sent and received as JSON.

```console
curl -X GET "https://demo.openmrs.org/openmrs/ws/rest/v1/concept"
connection: keep-alive 
content-length: 9731 
content-type: application/json;charset=UTF-8 
date: Wed, 20 Nov 2019 14:13:54 GMT 
etag: "04c83ff0cf2cc35cf05a2075ad117df83" 
server: nginx/1.10.3 (Ubuntu) 
strict-transport-security: max-age=15768000 
```

# Resources

* OpenMRS objects (persons, patients, encounters, observations, etc.) are exposed by the REST Web Services 
  modules as a REST resource as documented here.

* Resources have a default representation, which returns key properites. Most resources can be fetched using a 
  full representation (using the parameter `v=full`) that includes a more comprehensive list of properties.

# Subresources

* Some resources are not defined or do not make sense apart from their parent object. We refer 
  to these as subresources. 

* Examples of subresources are PersonNames, PersonAddresses, ConceptNames, etc. 

* You can act on subresources under the parent's url

### Examples  

#### Adding a person name.

```console
POST /openmrs/ws/rest/v1/person/:target_person_uuid/name 
{
  "givenName": "John",
  "familyName": "Smith"
}
```

#### Editing a person's name.

```console
POST /openmrs/ws/rest/v1/person/:target_person_uuid/name/:target_name_uuid 
{
  "givenName": "Johnny"
}
```

* A subresource can have only one parent. 

* If it seems like an resource has two or more parents, then it is most likely a top-level resource. 

* For example "encounters" is not be a subresource of "patient" and "location" resources (answering questions of "all encounters of a patient" and "all encounters at a location"). 

#### Instead, these should be queries on the encounter resource:

 Get encounter list for specific patient.

```console 
 GET /encounter?patient=:target_patient_uuid
```

Get encounter list for specific location.

```console 
 GET /encounter?location=:target_location_uuid
```

# Resources with subtypes

* Some resources can have subtypes. For example, the Order resource contains DrugOrder and TestOrder subtypes

* When creating a resource that has subtypes via a `POST`, you must specify which subtype of the resource you are creating, 
with a special t property of the resource.


### Examples

```console
POST /openmrs/ws/rest/v1/order
{"t": "testorder", /*... and other properties */}
```

* If you GET a resource that has subtypes, each result will be of one of those subtypes, 
which you can see by looking at the special property of each result. 

* You may query for only a certain subtype of a resource by providing a t query parameter. 

Get encounter orders of druge order sub type.

```console 
GET  /openmrs/ws/rest/v1/order?&t=drugorder&v=full'
```
