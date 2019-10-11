# Location Tag Type

## Overview

* Tags are strings attached to an entity (like tagging of blog entries) to form a folksonomy and/or to categorize data. 

* Location Tags are being used to tag locations, which enables the system to act based on the presence of tags on specific locations. 

* You should not use locations to represent logical ideas like `All-District Hospitals`. They should be modeled using LocationTags.

* For example, location tags may be used to control which locations are included in a choice list or to define which locations included in a report.

## Available operations. 

1. [List location tags](#list-location-tags)
2. [Create a location tag](#create-a-location-tag)
3. [Update a location tag](#update-a-location-tag)
4. [Delete a location tag](#delete-a-location-tag)


### List location tags

* #### List all non-retired location tags.

    Quickly filter location tags with a given search query. Returns a `404 Not Found` status if the location tag not exists.
    If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ##### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Location location tag type.

    ```console
    GET /locationtag?q="visit"
     ```

* #### List location tag by UUID.

    Retrieve a location tag by its UUID. Returns a `404 Not Found` status if the location tag type not exists. If the 
    user not logged in to  perform this action, a `401 Unauthorized` status returned.

    ```console
    GET /locationtag/:target_location_tag_uuid
    ```

### Create a location tag

* To Create a location tag  you need to specify below attributes in the request body.If the user not logged in to perform this action,
 a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | Name of the location tag  (Required)
    *description* | `String` | Description (Required)
    *retired* | `Boolean` | Retired status of the location tag
    *retiredReason* | `String` | For location tags that are retired, this may contain an explanation of why the location tag was retired.

    ```console
        POST /locationtag
        {
          "name": "Visit Location",
          "description": "Visits are only allowed to happen at locations tagged with this location tag.",
          "retired": false
        }
    ```
### Update a location tag

*  Update a target location tag with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if the location tag not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *uuid* | `target_location_tag_uuid` | Target location tag resource UUID

    #### Attributes

      Parameter | Type | Description
      --- | --- | ---
      *name* | `String` | Name of the location tag type (Required)
      *description* | `String` | Description (Required)
      *retired* | `Boolean` | Retired status of the location tag
      *retiredReason* | `String` | For location tags that are retired, this may contain an explanation of why the location tag was retired.

    ```console
        POST /locationtag/:target_location_tag_uuid
        {
          "name": "Visit Location",
          "description": "Visits are only allowed to happen at locations tagged with this location tag.",
          "retired": true,
          "retiredReason": "Not valid anymore"
        }
    ```

### Delete a location tag

* Delete or Retire a target location tag type by its UUID. Returns a `404 Not Found` status if the location tag not
 exists. If the user not logged in to  perform this action, a `401 Unauthorized` status returned.

    #### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’. Purging will attempt to irreversibly remove the tag from the system. Location tags types that have been used (i.e., are referenced from existing data) cannot be purged.

    ```console
        DELETE /locationtag/:target_location_tag_uuid?purge=true
     ```
