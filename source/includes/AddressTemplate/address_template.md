# Address Template

## Address Template Overview

Address Template is an XML Layout Template.

## Available operations for Address Template

1. [Retrieve Address Template](#retrieve-address-template)
2. [Update Address Template](#update-address-template)

## Retrieve Address Template

> Retrieve Address Template

```shell
GET /systemsetting/layout.address.format
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting/layout.address.format")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();
```


```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");
var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/systemsetting/layout.address.format", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "uuid": "98fa7af1-d183-4f70-93fb-2f488000ce4c",
    "property": "layout.address.format",
    "value": "<org.openmrs.layout.address.AddressTemplate>\n     <nameMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"Location.postalCode\"/>\n       <property name=\"address2\" value=\"Location.address2\"/>\n       <property name=\"address1\" value=\"Location.address1\"/>\n       <property name=\"country\" value=\"Location.country\"/>\n       <property name=\"stateProvince\" value=\"Location.stateProvince\"/>\n       <property name=\"cityVillage\" value=\"Location.cityVillage\"/>\n     </nameMappings>\n     <sizeMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"10\"/>\n       <property name=\"address2\" value=\"40\"/>\n       <property name=\"address1\" value=\"40\"/>\n       <property name=\"country\" value=\"10\"/>\n       <property name=\"stateProvince\" value=\"10\"/>\n       <property name=\"cityVillage\" value=\"10\"/>\n     </sizeMappings>\n     <lineByLineFormat>\n       <string>address1</string>\n       <string>address2</string>\n       <string>cityVillage stateProvince country postalCode</string>\n     </lineByLineFormat>\n   </org.openmrs.layout.address.AddressTemplate>",
    "description": null,
    "display": "Layout - Address Format = <org.openmrs.layout.address.AddressTemplate>\n     <nameMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"Location.postalCode\"/>\n       <property name=\"address2\" value=\"Location.address2\"/>\n       <property name=\"address1\" value=\"Location.address1\"/>\n       <property name=\"country\" value=\"Location.country\"/>\n       <property name=\"stateProvince\" value=\"Location.stateProvince\"/>\n       <property name=\"cityVillage\" value=\"Location.cityVillage\"/>\n     </nameMappings>\n     <sizeMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"10\"/>\n       <property name=\"address2\" value=\"40\"/>\n       <property name=\"address1\" value=\"40\"/>\n       <property name=\"country\" value=\"10\"/>\n       <property name=\"stateProvince\" value=\"10\"/>\n       <property name=\"cityVillage\" value=\"10\"/>\n     </sizeMappings>\n     <lineByLineFormat>\n       <string>address1</string>\n       <string>address2</string>\n       <string>cityVillage stateProvince country postalCode</string>\n     </lineByLineFormat>\n   </org.openmrs.layout.address.AddressTemplate>",
    "links": [
        {
            "rel": "self",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/systemsetting/98fa7af1-d183-4f70-93fb-2f488000ce4c",
            "resourceAlias": "systemsetting"
        },
        {
            "rel": "full",
            "uri": "http://localhost:8080/openmrs/ws/rest/v1/systemsetting/98fa7af1-d183-4f70-93fb-2f488000ce4c?v=full",
            "resourceAlias": "systemsetting"
        }
    ],
    "resourceVersion": "1.9"
}
```

Retrieves current Address Template.

## Update Address Template

> Update Address Template

```shell
POST /systemsetting/layout.address.format
{
    "value": "<org.openmrs.layout.address.AddressTemplate>\n     <nameMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"Location.postalCode\"/>\n       <property name=\"address2\" value=\"Location.address2\"/>\n       <property name=\"address1\" value=\"Location.address1\"/>\n       <property name=\"country\" value=\"Location.country\"/>\n       <property name=\"stateProvince\" value=\"Location.stateProvince\"/>\n       <property name=\"cityVillage\" value=\"Location.cityVillage\"/>\n     </nameMappings>\n     <sizeMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"10\"/>\n       <property name=\"address2\" value=\"40\"/>\n       <property name=\"address1\" value=\"40\"/>\n       <property name=\"country\" value=\"10\"/>\n       <property name=\"stateProvince\" value=\"10\"/>\n       <property name=\"cityVillage\" value=\"10\"/>\n     </sizeMappings>\n     <lineByLineFormat>\n       <string>address1</string>\n       <string>address2</string>\n       <string>cityVillage stateProvince country postalCode</string>\n     </lineByLineFormat>\n   </org.openmrs.layout.address.AddressTemplate>"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"value\": \"<org.openmrs.layout.address.AddressTemplate>\\n     <nameMappings class=\\\"properties\\\">\\n       <property name=\\\"postalCode\\\" value=\\\"Location.postalCode\\\"/>\\n       <property name=\\\"address2\\\" value=\\\"Location.address2\\\"/>\\n       <property name=\\\"address1\\\" value=\\\"Location.address1\\\"/>\\n       <property name=\\\"country\\\" value=\\\"Location.country\\\"/>\\n       <property name=\\\"stateProvince\\\" value=\\\"Location.stateProvince\\\"/>\\n       <property name=\\\"cityVillage\\\" value=\\\"Location.cityVillage\\\"/>\\n     </nameMappings>\\n     <sizeMappings class=\\\"properties\\\">\\n       <property name=\\\"postalCode\\\" value=\\\"11\\\"/>\\n       <property name=\\\"address2\\\" value=\\\"40\\\"/>\\n       <property name=\\\"address1\\\" value=\\\"40\\\"/>\\n       <property name=\\\"country\\\" value=\\\"10\\\"/>\\n       <property name=\\\"stateProvince\\\" value=\\\"10\\\"/>\\n       <property name=\\\"cityVillage\\\" value=\\\"10\\\"/>\\n     </sizeMappings>\\n     <lineByLineFormat>\\n       <string>address1</string>\\n       <string>address2</string>\\n       <string>cityVillage stateProvince country postalCode</string>\\n     </lineByLineFormat>\\n   </org.openmrs.layout.address.AddressTemplate>\"\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systemsetting/layout.address.format")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=1B06650EB0428F51EC119C909F58327C");
var raw = JSON.stringify({"value": "<org.openmrs.layout.address.AddressTemplate>\n     <nameMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"Location.postalCode\"/>\n       <property name=\"address2\" value=\"Location.address2\"/>\n       <property name=\"address1\" value=\"Location.address1\"/>\n       <property name=\"country\" value=\"Location.country\"/>\n       <property name=\"stateProvince\" value=\"Location.stateProvince\"/>\n       <property name=\"cityVillage\" value=\"Location.cityVillage\"/>\n     </nameMappings>\n     <sizeMappings class=\"properties\">\n       <property name=\"postalCode\" value=\"11\"/>\n       <property name=\"address2\" value=\"40\"/>\n       <property name=\"address1\" value=\"40\"/>\n       <property name=\"country\" value=\"10\"/>\n       <property name=\"stateProvince\" value=\"10\"/>\n       <property name=\"cityVillage\" value=\"10\"/>\n     </sizeMappings>\n     <lineByLineFormat>\n       <string>address1</string>\n       <string>address2</string>\n       <string>cityVillage stateProvince country postalCode</string>\n     </lineByLineFormat>\n   </org.openmrs.layout.address.AddressTemplate>"});
var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};
fetch("/openmrs/ws/rest/v1/systemsetting/layout.address.format", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Updates current Address Template with new XML sent in field `value`.
