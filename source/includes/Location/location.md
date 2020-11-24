# Location 

## Location Overview

* A Location is a physical place where a patient may be seen, such as a hospital, a room, a clinic, or a district.

* **Locations may have a hierarchy**, such that each location may have one parent location.

* A Location can have one or more Children location example Children's Ward might be a location within the location Amani Clinic.
  
* You might also store physical areas (for example, Eastern Province, or California) as Locations. 

* You should not use locations to represent logical ideas like All-District Hospitals. They should be modeled using LocationTags.

## Location Sub Resource types

### Location Attribute.

* If you wish to record extra information about location, you can create Location Attributes and assign them to Location Types.

* Location attributes exists specifically to allow implementations to extend the data model.


## Available operations for location

1. [List location](#list-location)
2. [Create a location](#create-a-location)
3. [Update a location](#update-a-location)
4. [Delete a location](#delete-a-location)
5. [List location attribute subresource](#list-location-attribute-subresources)
6. [Create location attribute subresource with properties](#create-a-location-attribute-subresource-with-properties)
7. [Update location attribute subresource](#update-a-location-attribute-subresource)
8. [Delete location attribute subresource](#delete-a-location-attribute-subresource)



## List location

> List location

```shell
GET /location?q=amani&v=default
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location?q=amani&v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location?q=amani&v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "aff27d58-a15c-49a6-9beb-d30dcfc0c66e",
            "display": "Amani Hospital",
            "name": "Amani Hospital",
            "description": null,
            "address1": null,
            "address2": null,
            "cityVillage": null,
            "stateProvince": null,
            "country": null,
            "postalCode": null,
            "latitude": null,
            "longitude": null,
            "countyDistrict": null,
            "tags": [
                {
                    "uuid": "37dd4458-dc9e-4ae6-a1f1-789c1162d37b",
                    "display": "Visit Location",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/locationtag/37dd4458-dc9e-4ae6-a1f1-789c1162d37b"
                        }
                    ]
                }
            ],
            "parentLocation": null,
            "childLocations": [
                {
                    "uuid": "b1a8b05e-3542-4037-bbd3-998ee9c40574",
                    "display": "Inpatient Ward",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/b1a8b05e-3542-4037-bbd3-998ee9c40574"
                        }
                    ]
                },
                {
                    "uuid": "2131aff8-2e2a-480a-b7ab-4ac53250262b",
                    "display": "Isolation Ward",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/2131aff8-2e2a-480a-b7ab-4ac53250262b"
                        }
                    ]
                },
                {
                    "uuid": "7fdfa2cb-bc95-405a-88c6-32b7673c0453",
                    "display": "Laboratory",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/7fdfa2cb-bc95-405a-88c6-32b7673c0453"
                        }
                    ]
                },
                {
                    "uuid": "58c57d25-8d39-41ab-8422-108a0c277d98",
                    "display": "Outpatient Clinic",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/58c57d25-8d39-41ab-8422-108a0c277d98"
                        }
                    ]
                },
                {
                    "uuid": "7f65d926-57d6-4402-ae10-a5b3bcbf7986",
                    "display": "Pharmacy",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/7f65d926-57d6-4402-ae10-a5b3bcbf7986"
                        }
                    ]
                },
                {
                    "uuid": "6351fcf4-e311-4a19-90f9-35667d99a8af",
                    "display": "Registration Desk",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/6351fcf4-e311-4a19-90f9-35667d99a8af"
                        }
                    ]
                }
            ],
            "retired": false,
            "attributes": [],
            "links": [
                {
                    "rel": "self",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e"
                },
                {
                    "rel": "full",
                    "uri": "http://demo.openmrs.org/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e?v=full"
                }
            ],
            "resourceVersion": "2.0"
        }
    ]
}

```
    
* Quickly filter location with given query parameters. Returns a `404 Not Found` status if the location not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.
    
### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *q* | `Search Query` | Display Name of Location object.
     
    
## List location by UUID.

> List location by UUID

```shell
GET /location/:target_location_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve a location by its UUID. Returns a `404 Not Found` status if the location not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.
    
   
## Create a location

> Create a location

```shell
POST /location
{
    "name": "Salzburg Hospital",
    "description": "Salzburg hospital location",
    "address1": "Mullner House 48",
    "cityVillage": "salzburg",
    "stateProvince": "salzburg",
    "country": "Austria",
    "postalCode": "5020",
    "countyDistrict": "salzburg",
    "tags": [
        "37dd4458-dc9e-4ae6-a1f1-789c1162d37b"
    ],
    "childLocations": [
        "7fdfa2cb-bc95-405a-88c6-32b7673c0453",
        "6351fcf4-e311-4a19-90f9-35667d99a8af"
    ],
    "attributes": [
        {
            "attributeType": "fa0527cb-8b37-4a0a-8e7a-cff04acc8554",
            "value": "low humidity"
        }
    ]
}

```
* To Create a location you need to specify below attributes in the request body. If the user not logged in to perform this action,a `401 Unauthorized` status returned.

### Attributes

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
    *countyDistrict* | `String` | District or Country
    *[tags](#location-tag-type)* | `Array[]: LocationTag UUID` | UUID's of the location tags
    *[parentLocation](#location)* | `Parent Location UUID` | UUID of the target parent location
    *[childLocations](#location)* | `Array[]: Child Location UUID` | UUID's of the target child locations e.g.(Inpatient ward, outpatient clinic)
    *[attributes](#list-location-attribute-subresources)* | `Array[]: Attribute UUID` | UUID's of location attributes  


## Update a location

> Update a location

```shell
POST /location/:target_location_uuid
{
    "description": "Modified location of Salzburg hospital location"
}       
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"description\": \"Modified location of Salzburg hospital location\"\r\n}       \r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var raw = JSON.stringify({"description":"Modified location of Salzburg hospital location"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

*  Update a target location with given UUID, this method only modifies properties in the request. Returns a `404 Not Found` 
status if the location not exists. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    
### Attributes

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
    *countyDistrict* | `String` | District or Country
    *[tags](#location-tag-type)* | `Array[]: LocationTag UUID` | UUID's of the location tags
    *[parentLocation](#location)* | `Parent Location UUID` | UUID of the target parent location
    *[childLocations](#location)* | `Array[]: Child Location UUID` | UUID's of the target child locations e.g.(Inpatient ward, outpatient clinic)
    *[attributes](#list-location-attribute-subresources)* | `Array[]: Attribute UUID` | UUID's of location attributes  

    
## Delete a location

```shell
DELETE /location/:target_location_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target location by its UUID. Returns a `404 Not Found` status if the location not exists. If the user not logged 
  in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’

## List location attribute subresources

> List location attribute subresources

```shell
GET /location/:target_location_uuid/attribute 
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


> Success Response

```response

{
    "results": [
        {
            "display": "humidity: low humidity",
            "uuid": "83f76320-0fa9-4bd7-b13f-7304ef723e8d",
            "attributeType": {
                "uuid": "fa0527cb-8b37-4a0a-8e7a-cff04acc8554",
                "display": "humidity",
                "links": [
                    {
                        "rel": "self",
                        "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/locationattributetype/fa0527cb-8b37-4a0a-8e7a-cff04acc8554"
                    }
                ]
            },
            "value": "low humidity",
            "voided": false,
            "links": [
                {
                    "rel": "self",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d"
                },
                {
                    "rel": "full",
                    "uri": "http://qa-refapp.openmrs.org/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d?v=full"
                }
            ],
            "resourceVersion": "1.9"
        }
    ]
}

```
* Retrieve all attribute sub resources of a location resource by target_location_uuid. Returns a `404 Not Found` status if the attribute not exists. 
* If the user not logged in to perform this action, a `401 Unauthorized` status returned.


## List location attribute subresources by own UUID and parent location UUID.

> List location attribute subresources by own UUID

```shell
GET /location/:target_location_uuid/attribute/:target_attribute_uuid
```    

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Retrieve an attribute sub resources of a location resource.Returns a `404 Not Found` status if the attribute not exists. 
* If the user are not logged in to perform this action, a `401 Unauthorized` status returned.
     
## Create a location attribute subresource with properties

```shell
POST location/:target_location_uuid/attribute 
{
    "attributeType": "fa0527cb-8b37-4a0a-8e7a-cff04acc8554",
    "value": "high humidity"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"attributeType\": \"fa0527cb-8b37-4a0a-8e7a-cff04acc8554\",\r\n    \"value\": \"high humidity\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var raw = JSON.stringify({"attributeType":"fa0527cb-8b37-4a0a-8e7a-cff04acc8554","value":"high humidity"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute", requestOptions)
  .then(response => response.text())


```

* To Create an attribute subresource for a specific location resource, you need to specify below attributes in the request body.
If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[attributeType](#location-attribute-type)* | `Attribute_Type UUID` | Create Attribute from this Location Attribute_Type (Required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (Required)

 
 
## Update a location attribute subresource

> Update a location attribute subresource

```shell
POST location/:target_location_uuid/attribute/:target_location_attribute_uuid
{
    "value": "low humidity"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"value\": \"low humidity\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var raw = JSON.stringify({"value":"low humidity"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Updates a location attribute sub resource value with given UUID, this method will only modify the value of the subresource. Returns a `404 Not Found` status if the attribute not exists. 
* If the user not logged in to perform this action, a `401 Unauthorized` status
returned.

  ### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *[attributeType](#location-attribute-type)* | `Attribute_Type UUID` | Create Attribute from this Location Attribute_Type (Required)
    *value* | `Depends on Attribute_Type Selected` | Value for the attribute (Required)


## Delete a location attribute subresource

> Delete a location attribute subresource

```shell
DELETE /location/:target_location_uuid/attribute/:target_location_attribute_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=644F0C130F7EA78D917F896CE811FBAF");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/location/aff27d58-a15c-49a6-9beb-d30dcfc0c66e/attribute/83f76320-0fa9-4bd7-b13f-7304ef723e8d?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Delete or Retire a target location attribute subresource by its UUID. Returns a `404 Not Found` status if the attribute not exists. 
* If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    ### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *purge* | `Boolean` | The resource will be voided/retired unless purge = ‘true’
    
