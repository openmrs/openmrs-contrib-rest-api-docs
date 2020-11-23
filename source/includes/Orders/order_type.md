# Order type

## Order type Overview

* Orders represent requests from providers for some action to care for a patient. 
Common types of orders are prescriptions (drug orders), lab tests, radiology tests, 
procedures and referrals.

* In nearly all cases, handling different types of orders requires specific behavior of the application. The OpenMRS platform is designed to handle certain types of orders. 
Adding new order types will usually only happen when new features to handle the 
new order type are also being added to the system (using a module or app).

## Available operations for Order type.

1. [List orders](#list-orders)
2. [Create an order](#create-an-order)
3. [Update an order](#update-an-order)
4. [Delete an order](#delete-an-order)

## List orders

> List orders

```shell
GET /ordertype?v=full
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/ordertype?v=full")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/ordertype?v=full", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response

{
    "results": [
        {
            "uuid": "131168f4-15f5-102d-96e4-000c29c2a5d7",
            "display": "Drug Order",
            "name": "Drug Order",
            "javaClassName": "org.openmrs.DrugOrder",
            "retired": false,
            "description": "An order for a medication to be given to the patient",
            "conceptClasses": [],
            "parent": null,
            "auditInfo": {
                "creator": {
                    "uuid": "45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
                    "display": "admin",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002"
                        }
                    ]
                },
                "dateCreated": "2010-05-12T00:00:00.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7"
                }
            ],
            "resourceVersion": "1.10"
        },
        {
            "uuid": "52a447d3-a64a-11e3-9aeb-50e549534c5e",
            "display": "Test Order",
            "name": "Test Order",
            "javaClassName": "org.openmrs.TestOrder",
            "retired": false,
            "description": "Order type for test orders",
            "conceptClasses": [],
            "parent": null,
            "auditInfo": {
                "creator": {
                    "uuid": "45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
                    "display": "admin",
                    "links": [
                        {
                            "rel": "self",
                            "uri": "/openmrs/ws/rest/v1/user/45ce6c2e-dd5a-11e6-9d9c-0242ac150002"
                        }
                    ]
                },
                "dateCreated": "2014-03-09T00:00:00.000+0000",
                "changedBy": null,
                "dateChanged": null
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "/openmrs/ws/rest/v1/ordertype/52a447d3-a64a-11e3-9aeb-50e549534c5e"
                }
            ],
            "resourceVersion": "1.10"
        }
    ]
}

```

* Fetch all non-retired order types that match any specified parameters otherwise fetch all non-retired order types. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.


### Get a particular order type

> Get a particular order type

```shell
GET /ordertype/:target_ordertype_uuid
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```
		

* Retrieve a particular order.If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.


## Create an order type

> Create an order type

```shell
POST /ordertype
{
    "name": "drug order3",
    "description": "One 500mg tablet of Ciprofloxacin, twice a day",
    "parent": "070f0120-0283-4858-885d-a20d967729cf",
    "javaClassName": "org.openmrs.DrugOrder"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"name\": \"drug order\",\r\n    \"description\": \"One 500mg tablet of Ciprofloxacin, twice a day\",\r\n    \"parent\": \"070f0120-0283-4858-885d-a20d967729cf\",\r\n    \"javaClassName\": \"org.openmrs.DrugOrder\"\r\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/ordertype")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var raw = JSON.stringify({"name":"drug order","description":"One 500mg tablet of Ciprofloxacin, twice a day","parent":"070f0120-0283-4858-885d-a20d967729cf","javaClassName":"org.openmrs.DrugOrder"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/ordertype", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

* Order types depend on code within the application to properly handle them, so it would be unusual to create a new order type unless some new code (e.g., a module) has been added to the system to handle the new order type.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | the name of the order type (Required)
    *description* | `String` | the description of the order type
    *javaClassName* | `Java Class` | the java class (Required)
    *[parent](order)* | `Order UUID` | the order uuid
    *[conceptClasses](#concept-class)* | `Array[] : Concept UUID` | classes of concepts that can be used to generate an order of this type.

    
## Update an order type

> Update an order type

```shell
POST /ordertype/:target_ordertype_uuid
{
  "description": "One 400mg tablet of Ciprofloxacin, twice a day"
}
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n  \"description\": \"One 400mg tablet of Ciprofloxacin, twice a day\"\r\n}\r\n");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```


```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var raw = JSON.stringify({"description":"One 400mg tablet of Ciprofloxacin, twice a day"});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));


```

* Update an order type with given UUID, this method only modifies properties in the request. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | the name of the order type
    *description* | `String` | the description of the order type
    *javaClassName* | `Java Class` | the java class
    *[parent](order)* | `Order UUID` | the order uuid
    *[conceptClasses](#concept-class)* | `Array[] : Concept UUID` | classes of concepts that can be used to generate an order of this type.


## Delete an order type

> Delete an order type

```shell
DELETE /ordertype/:target_ordertype_uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1FB1E7BA1F2EF800D4BDF81D1D1FB1F0");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/ordertype/131168f4-15f5-102d-96e4-000c29c2a5d7?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Delete or retire an order type by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

