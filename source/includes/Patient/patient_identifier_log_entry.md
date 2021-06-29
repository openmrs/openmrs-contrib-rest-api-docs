# Patient Identifier LogEntry

## LogEntry Overview

LogEntry is a resource that encapsulates Log entry for Patient Identifier generation event.

## Available operations for LogEntry

1. [List LogEntries](#list-logentries)

## List LogEntries

> List LogEntries

```shell
GET idgen/logentry?v=default
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/logentry?v=default)
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/logentry?v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
  "results": [
    {
      "uuid": "10503A",
      "links": [
        {
          "rel": "self",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/logentry/10503A",
          "resourceAlias": "logentry"
        },
        {
          "rel": "full",
          "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/logentry/10503A?v=full",
          "resourceAlias": "logentry"
        }
      ],
      "resourceVersion": "1.8",
      "source": {
        "uuid": "47ea53ab-e57a-4671-b2c8-63a4b31bb140",
        "name": "pool",
        "identifierType": {
          "uuid": "05a29f94-c0ed-11e2-94be-8c13b969e334",
          "display": "OpenMRS ID",
          "name": "OpenMRS ID",
          "description": "OpenMRS patient identifier, with check-digit",
          "format": null,
          "formatDescription": null,
          "required": true,
          "validator": "org.openmrs.module.idgen.validator.LuhnMod30IdentifierValidator",
          "locationBehavior": null,
          "uniquenessBehavior": null,
          "retired": false,
          "links": [
            {
              "rel": "self",
              "uri": "http://localhost:8080/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334",
              "resourceAlias": "patientidentifiertype"
            },
            {
              "rel": "full",
              "uri": "http://localhost:8080/openmrs/ws/rest/v1/patientidentifiertype/05a29f94-c0ed-11e2-94be-8c13b969e334?v=full",
              "resourceAlias": "patientidentifiertype"
            }
          ],
          "resourceVersion": "2.0"
        },
        "display": "OpenMRS ID - pool - org.openmrs.module.idgen.IdentifierPool",
        "links": [
          {
            "rel": "self",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/identifiersource/47ea53ab-e57a-4671-b2c8-63a4b31bb140",
            "resourceAlias": "identifiersource"
          }
        ],
        "type": "identifierpool",
        "resourceVersion": "1.8"
      },
      "identifier": "10503A",
      "comment": "Batch Export of 5 to file",
      "generatedBy": {
        "uuid": "1c3db49d-440a-11e6-a65c-00e04c680037",
        "display": "admin",
        "username": "admin",
        "systemId": "admin",
        "userProperties": {
          "loginAttempts": "0",
          "lockoutTimestamp": "",
          "emrapi.lastViewedPatientIds": "7,8"
        },
        "person": {
          "uuid": "1296b0dc-440a-11e6-a65c-00e04c680037",
          "display": "Super User",
          "links": [
            {
              "rel": "self",
              "uri": "http://localhost:8080/openmrs/ws/rest/v1/person/1296b0dc-440a-11e6-a65c-00e04c680037",
              "resourceAlias": "person"
            }
          ]
        },
        "privileges": [],
        "roles": [
          {
            "uuid": "8d94f852-c2cc-11de-8d13-0010c6dffd0f",
            "display": "System Developer",
            "links": [
              {
                "rel": "self",
                "uri": "http://localhost:8080/openmrs/ws/rest/v1/role/8d94f852-c2cc-11de-8d13-0010c6dffd0f",
                "resourceAlias": "role"
              }
            ]
          },
          {
            "uuid": "8d94f280-c2cc-11de-8d13-0010c6dffd0f",
            "display": "Provider",
            "links": [
              {
                "rel": "self",
                "uri": "http://localhost:8080/openmrs/ws/rest/v1/role/8d94f280-c2cc-11de-8d13-0010c6dffd0f",
                "resourceAlias": "role"
              }
            ]
          }
        ],
        "retired": false,
        "links": [
          {
            "rel": "self",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/user/1c3db49d-440a-11e6-a65c-00e04c680037",
            "resourceAlias": "user"
          },
          {
            "rel": "full",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/user/1c3db49d-440a-11e6-a65c-00e04c680037?v=full",
            "resourceAlias": "user"
          }
        ],
        "resourceVersion": "1.8"
      },
      "dateGenerated": "2021-06-25T21:37:33.000+0200"
    }
  ],
  "links": [
    {
      "rel": "next",
      "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/logentry?v=default&startIndex=50",
      "resourceAlias": null
    }
  ]
}
```

You can also filter Log Entries with given query parameters.
If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

| Parameter    | Type           | Description                           |
| ------------ | ---------------| ------------------------------------- |
| [_source_](#patientidentifiersource) | `PatientIdentifierSource_UUID` | Filter entries by source |
| _fromDate_ | `Date` | Filter entries older than date  |
| _toDate_ | `Date` | Filter entries younger than date  |
| _identifier_ | `String` | Filter entries by generated identifier  |
| _comment_ | `String` | Filter entries by generation event's comment  |
| [_generatedBy_](#user) | `User_UUID` | Filter entries by user who executed generation  |


## Get LogEntry by Identifier

> Get LogEntry by Identifier

```shell
GET idgen/logentry/:identifier
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/logentry/:identifier)
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=A2AF09658C73E1ECEC5D3C8C7C249A2D");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/logentry/:identifier", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can also fetch log entry for a unique generated identifier.
