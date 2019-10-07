# Location 

## Overview

* A Location is a physical place where a patient may be seen, such as a hospital, a room, a clinic, or a district.

* <b>Locations may have a hierarchy</b>,such that each location may have one parent location.

* And also a Location can have one or more Children location example Children's Ward might be a location within the location 
Amani Clinic.
  
* You might also store physical areas (for example Eastern Province, or California) as Locations. 

* You should not use locations to represent logical ideas like All District Hospitals they should be modeled using LocationTags.

## Sub Resource types

### Attribute.

* If you wish to record extra information about location, you can create Location Attributes and assign them to Location Types.

* Location attributes exists specifically to allow implementations to extend the data model.


## Available operations. 

1. [List location](#list-location)
2. [Create a location](#create-a-location)
3. [Update a location](#update-a-location)
4. [Delete a location](#delete-a-location)
5. [List location attribute sub resource](#list-location-attribute-sub-resources)
6. [Create location attribute sub resource with properties](#create-a-location-attribute-sub-resource-with-properties)
7. [Update location attribute sub resource](#update-a-location-attribute-sub-resource)
6. [Delete location attribute sub resource](#delete-a-location-attribute-sub-resource)



### List location

* #### List all non-retired locations`.
    
    Quickly filter location with given query parameters.Returns a `404 Not Found` status if location not exists. If user not
    logged in to perform this action,a `401 Unauthorized` status returned.
    
    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Location object.
     
    ```console
     GET /location?
     q="Search Query"
     ```
    
* #### List location by UUID.

    Retrieve a location by its UUID. Returns a `404 Not Found` status if location not exists. If user not logged 
    in to perform this action, a `401 Unauthorized` status returned.
    
    ```console
    GET /location/:target_location_uuid
    ```
   
### Create a location

* To Create a location you need to specify below attributes in the request body.If you are not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the location (Required)
    *address1* | `String` | Address of the location (Required)
    *description* | `String` | Description
    *cityVillage* | `String` | City/village
    *stateProvince* | `String` | State and province
    *country* | `String` | Country    
    *postalCode* | `String` | Postal code of the location 
    *latitude* | `String` | Latitude    
    *longitude* | `String` | Longitude
    *countyDistrict* | `String` | Disitrict
    *tags* | `Array[]: LocationTag UUID` | UUID's of the location tags
    *parentLocation* | `Parent Location UUID` | UUID of the target parent location
    *childLocations* | `Array[]: Child Location UUID` | UUID's of the target child locations
    *attributes* | `Array[]: Attribute UUID` | UUID's of location attributes  

   
    ```console
        POST /location
        {
          "name": "name ",
          "description": "string",
          "address1": "string",
          "address2": "string",
          "cityVillage": "string",
          "stateProvince": "string",
          "country": "string",
          "postalCode": "string",
          "latitude": "string",
          "longitude": "string",
          "countyDistrict": "string",
          "address3": "string",
          "address4": "string",
          "address5": "string",
          "address6": "string",
          "tags": [
            "target_location_tag_uuid"
          ],
          "parentLocation": "target_parent_location_uuid",
          "childLocations": [
            "target_child_location_uuid"
          ],
          "attributes": [
              {
                 "attributeType": "target_attributeType_uuid",
                  "value": "value_for_attribute"
              }
          ]
        }
    ```
### Update a location

*  Update a target location with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if location not exists. If user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_location_uuid` | Target location resource UUID
    
    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *resource* | `Location` | Location resource with updated properties.
    
    ```console
        POST /location/:target_location_uuid
        -d  modified_location_object
    ```
    
### Delete a location

* Delete or Retire a target location by its UUID. Returns a `404 Not Found` status if location not exists.If user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

    ```console
        DELETE /location/:target_location_uuid?purge=true
     ```
