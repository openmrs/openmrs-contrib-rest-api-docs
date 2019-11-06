# Current version

* By default, all requests to `/openmrs/ws/rest` receive the v1 version of the REST API.

* We have hosted online [swagger documentation](https://demo.openmrs.org/openmrs/module/webservices/rest/apiDocs.htm) that is 
generated on the fly.

# Resources

* Every available object in the web services (ws) module is written up as a resource. 

* The resource class defines the properties that are exposed and the setters that are available. 

* The class also defines the representations and what goes in them (ref vs default vs full).

<b>See documentation about resources and their URIs here: [REST Web Service Resources in OpenMRS 1.9](https://wiki.openmrs.org/display/docs/REST+Web+Service+Resources+in+OpenMRS+1.9)</b>


# Subresources

* There are some objects that are not defined or do not make sense apart from their parent object which we refer as subresources. 

* Examples are PersonNames, PersonAddresses, ConceptNames, etc. 

* You can act on subresources under the parent url.

### Examples :  

<b> Adding a person name. </b>

```console
POST /openmrs/ws/rest/v1/person/target_person_uuid/name 
{
  "givenName": "John",
  "familyName": "Smith"
}
```

<b> Editing a person's name. </b>

```console
POST /openmrs/ws/rest/v1/person/target_person_uuid/name/target_name_uuid 
{
  "givenName": "Johnny"
}
```

* A subresource can have only one parent. 

* If it seems like an object has two or more parents, then it is most likely a top-level resource. 

* Example "encounters" should not be a subresource of "patient" and "location" resource type (answering questions of "all encounters of a patient" and "all encounters at a location"). 

<b> Instead, these should be queries on the encounter resource: </b> 
 
 ```console
 
 Get encounter list for specific patient.
 
 GET '/openmrs/ws/rest/v1/encounter?patient=target_patient_uuid'
 
```
 ```console
 
 Get encounter list for specific location.
 
 GET '/openmrs/ws/rest/v1/encounter?location=target_location_uuid'
 
```

# Resources with Subtypes

* Some resources can have multiple subtypes,<b> for example the order resource contains drugorder and testorder subtypes</b>

* When creating a resource that has subtypes via a POST, you must specify which subtype of the resource you are creating, 
with a special t property of the object.


### Examples :  

 ```console

POST /openmrs/ws/rest/v1/order
{"t": "testorder", /*... and other properties */}
```

* If you GET a resource that has subtypes, each result will be of one of those subtypes, 
which you can see by looking at the special t property of each result. 

* You may query for only a certain subtype of a resource by providing a t query parameter. 

 ```console
 
 Get encounter orders of druge order sub type.
 
 GET  /openmrs/ws/rest/v1/order?&t=drugorder&v=full'
```
