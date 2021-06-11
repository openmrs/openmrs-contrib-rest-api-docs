# Administration Links

## Administration Links Overview

Every installed module can register its administration pages. They are accessible through Legacy UI at [openmrs/admin/index.htm](openmrs/admin/index.htm)

The following endpoints allow users to return list of installed modules with their administration links.

## Available Operations for Administration Links type

1. [List Administration Links](#list-administration-links)

## List Administration Links

> List Administration Links

```shell
GET /administrationlinks?v=default
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/administrationlinks?v=default")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/administrationlinks?v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "webservices.rest",
            "display": "REST Web Services",
            "title": "REST Web Services",
            "administrationLinks": {
                "module/webservices/rest/settings.form": "Settings",
                "module/webservices/rest/test.htm": "Test",
                "module/webservices/rest/apiDocs.htm": "API Documentation"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/administrationlinks/webservices.rest",
                    "resourceAlias": "administrationlinks"
                }
            ]
        },
        {
            "uuid": "owa",
            "display": "Open Web Apps Module",
            "title": "Open Web Apps Module",
            "administrationLinks": {
                "/module/owa/manager.form": "Manage Apps",
                "/module/owa/settings.form": "Settings"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/administrationlinks/owa",
                    "resourceAlias": "administrationlinks"
                }
            ]
        },
        {
            "uuid": "openconceptlab",
            "display": "Open Concept Lab",
            "title": "Open Concept Lab",
            "administrationLinks": {
                "/owa/openconceptlab/index.html#/subscription": "Configuration Page",
                "/owa/openconceptlab/index.html#/": "Status Page"
            },
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/administrationlinks/openconceptlab",
                    "resourceAlias": "administrationlinks"
                }
            ]
        }
    ]
}
```

* Fetches all installed modules with their administration links. Returns a `200 OK` status with the List of AdministrationLinks response.

## List Administration Links by module ID

> List Administration Links by module ID

```shell
GET /administrationlinks/:moduleId
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/administrationlinks/:moduleId")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/administrationlinks/:moduleId", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "uuid": "webservices.rest",
    "display": "REST Web Services",
    "title": "REST Web Services",
    "administrationLinks": {
        "module/webservices/rest/settings.form": "Settings",
        "module/webservices/rest/test.htm": "Test",
        "module/webservices/rest/apiDocs.htm": "API Documentation"
    },
    "links": [
        {
            "rel": "self",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/administrationlinks/webservices.rest",
            "resourceAlias": "administrationlinks"
        }
    ],
    "resourceVersion": "1.8"
}
```

* Fetches administration links of given module by its id. Returns a `404 Not Found` status if the module does not have any links registered. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.
