# PatientIdentifierSource

## PatientIdentifierSource Overview

## Available operations for PatientIdentifierSource

1. [List PatientIdentifierSources](#list-patientidentifiersources)
2. [Create a PatientIdentifierSource](#create-a-patientidentifiersource)
3. [Update a PatientIdentifierSource](#update-a-patientidentifiersource)
4. [Delete a PatientIdentifierSource](#delete-a-patientidentifiersource)
5. [Export PatientIdentifiers from Source](#export-patientidentifiers-from-source)
6. [Reserve PatientIdentifiers in Source](#reserve-patientidentifiers-in-source)
7. [Upload PatientIdentifiers from Source](#upload-patientidentifiers-from-source)
8. [Upload PatientIdentifiers from Request Body](#upload-patientidentifiers-from-request-body)

## List PatientIdentifierSources

> List PatientIdentifierSource

```shell
GET /idgen/identifiersource?v=default
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/identifiersource?v=default")
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

fetch("/openmrs/ws/rest/v1/idgen/identifiersource?v=default", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response
{
    "results": [
        {
            "uuid": "691eed12-c0f1-11e2-94be-8c13b969e334",
            "name": "Generator for OpenMRS ID",
            "description": null,
            "baseCharacterSet": "0123456789ACDEFGHJKLMNPRTUVWXY",
            "prefix": null,
            "suffix": null,
            "firstIdentifierBase": "10000",
            "minLength": 6,
            "maxLength": null,
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
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/idgen/identifiersource/691eed12-c0f1-11e2-94be-8c13b969e334",
                    "resourceAlias": "identifiersource"
                }
            ],
            "type": "sequentialidentifiergenerator",
            "resourceVersion": "1.8"
        }
    ]
}
```

Returns list of all available PatientIdentifierSources.

### Query Parameters

Parameter                                   | Type                         | Description
---                                         | ---                          | ---
*[identifierType](#patientidentifiertype)*  | `PatientIdentifierType_UUID` | Source Identifier Type


## List PatientIdentifierSource by UUID

> List PatientIdentifierSource by UUID

```shell
GET /idgen/identifiersource/:uuid
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")
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

fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Retrieve PatientIdentifierSource by its UUID. Returns a `404 Not Found` status if patient does not exist in the system. If the user is not logged in to perform this action, a `401 Unauthorized` status is returned.

## Create a PatientIdentifierSource

> Create a PatientIdentifierSource

There are 3 types of PatientIdentifierSource you can create via REST API:

- SequentialIdentifierGenerator
  
- RemoteIdentifierSource
  
- IdentifierPool

## Create SequentialIdentifierGenerator

> Create SequentialIdentifierGenerator

```shell
POST /idgen/identifiersource
{
    "sourceType": "SequentialIdentifierGenerator",
    "identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334",
    "name": "New identifier",
    "description": "Description",
    "firstIdentifierBase": 10000,
    "baseCharacterSet": "0123456789ACDEFGHJKLMNPRTUVWXY",
    "prefix": "",
    "suffix": "",
    "minLength": 3,
    "maxLength": 10
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"sourceType\": \"SequentialIdentifierGenerator\",\n    \"identifierType\": \"05a29f94-c0ed-11e2-94be-8c13b969e334\",\n    \"name\": \"New identifier\",\n    \"description\": \"Description\",\n    \"firstIdentifierBase\": 10000,\n    \"baseCharacterSet\": \"0123456789ACDEFGHJKLMNPRTUVWXY\",\n    \"prefix\": \"\",\n    \"suffix\": \"\",\n    \"minLength\": 3,\n    \"maxLength\": 10\n}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/identifiersource")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var raw = JSON.stringify({"sourceType": "SequentialIdentifierGenerator","identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334","name": "New identifier","description": "Description","firstIdentifierBase": 10000,"baseCharacterSet": "0123456789ACDEFGHJKLMNPRTUVWXY","prefix": "","suffix": "","minLength": 3,"maxLength": 10});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/identifiersource", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

To create a SequentialIdentifierGenerator you need to specify the below properties. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

Parameter                                   | Type                         | Description                
---                                         | ---                          | ---              
*sourceType*                                | `String`                     | Always set to "SequentialIdentifierGenerator" (Required)
*[identifierType](#patientidentifiertype)*  | `PatientIdentifierType_UUID` | Source Identifier Type (Required)
*name*                                      | `String`                     | Name (Required)      
*baseCharacterSet*                          | `String`                     | Character set for generating identifiers (Required)      
*firstIdentifierBase*                       | `integer`                    | Base of first generated identifier (Required)      
*description*                               | `String`                     | Description     
*prefix*                                    | `String`                     | Identifier Prefix     
*suffix*                                    | `String`                     | Identifier Suffix     
*minLength*                                 | `integer`                    | Minimum Identifier length     
*maxLength*                                 | `integer`                    | Maximum Identifier length          

## Create RemoteIdentifierSource                                                                                                                                                                                                                                                                                                                                                                                                                                                     
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
> Create RemoteIdentifierSource                                                                                                                                                                                                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
```shell
POST /idgen/identifiersource                                                                                                                                                                                                                                                                                                                                                                                                                                                                
{
    "sourceType": "RemoteIdentifierSource",
    "identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334",
    "name": "RemoteIdentifierSource",
    "description": "RemoteIdentifierSource",
    "url": "http://example.com",
    "username": "",
    "password": ""
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\n    \"sourceType\": \"RemoteIdentifierSource\",\n    \"identifierType\": \"05a29f94-c0ed-11e2-94be-8c13b969e334\",\n    \"name\": \"RemoteIdentifierSource\",\n    \"description\": \"RemoteIdentifierSource\",\n    \"url\": \"http://example.com\",\n    \"username\": \"\",\n    \"password\": \"\"\n}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"sourceType": "RemoteIdentifierSource", "identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334","name": "RemoteIdentifierSource","description": "RemoteIdentifierSource","url": "http://example.com","username": "","password": ""});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
To create a RemoteIdentifierSource you need to specify the below properties. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.                                                                                                                                                                                                                                                                                                               
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
### Properties                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
Parameter                                   | Type                         | Description                                                                                                                                                                                                                                                                                                                                                                                                    
---                                         | ---                          | ---           
*sourceType*                                | `String`                     | Always set to "RemoteIdentifierSource" (Required)
*[identifierType](#patientidentifiertype)*  | `PatientIdentifierType_UUID` | Source Identifier Type (Required)                                                                                                                                                                                                                                                                                                                                                                              
*name*                                      | `String`                     | Name (Required)                                                                                                                                                                                                                                                                                                                                                                                                
*url*                                       | `URL`                        | Remote Source URL (Required)    
*description*                               | `String`                     | Description
*username*                                  | `String`                     | Remote Source Username
*password*                                  | `String`                     | Remote Source Password

## Create IdentifierPool

> Create IdentifierPool

```shell
POST /idgen/identifiersource                                                                                                                                                                                                                                                                                                                                                                                                                                                                
{
    "sourceType": "IdentifierPool",
    "identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334",
    "name": "IdentifierPool",
    "description": "IdentifierPool",
    "batchSize": 1000,
    "minPoolSize": 500,
    "sequential": true,
    "refillWithScheduledTask": false,
    "sourceUuid": ""
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\n    \"sourceType\": \"IdentifierPool\",\n    \"identifierType\": \"05a29f94-c0ed-11e2-94be-8c13b969e334\",\n    \"name\": \"IdentifierPool\",\n    \"description\": \"IdentifierPool\",\n    \"batchSize\": 1000,\n    \"minPoolSize\": 500,\n    \"sequential\": true,\n    \"refillWithScheduledTask\": false,\n    \"sourceUuid\": \"\"\n}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"sourceType": "IdentifierPool","identifierType": "05a29f94-c0ed-11e2-94be-8c13b969e334","name": "IdentifierPool","description": "IdentifierPool","batchSize": 1000,"minPoolSize": 500,"sequential": true,"refillWithScheduledTask": false,"sourceUuid": ""});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

To create an IdentifierPool you need to specify the below properties. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

Parameter                                   | Type                         | Description
---                                         | ---                          | ---          
*sourceType*                                | `String`                     | Always set to "IdentifierPool" (Required)
*[identifierType](#patientidentifiertype)*  | `PatientIdentifierType_UUID` | Source Identifier Type (Required)
*name*                                      | `String`                     | Name (Required)
*description*                               | `String`                     | Description
*batchSize*                                 | `integer`                    | Batch Size
*minPoolSize*                               | `integer`                    | Minimum Pool Size
*sequential*                                | `String`                     | If true order is Sequential, if false order is Random
*refillWithScheduledTask*                   | `String`                     | If true pool is filled as a background task, if false, when you request an identifier
*sourceUuid*                                | `PatientIdentifierSource_UUID` | UUID of another source that you want to fill this pool from

## Update a PatientIdentifierSource

> Update a PatientIdentifierSource

There are 3 types of PatientIdentifierSource you can update via REST API:

- SequentialIdentifierGenerator

- RemoteIdentifierSource

- IdentifierPool

## Update SequentialIdentifierGenerator

> Update SequentialIdentifierGenerator

```shell
POST /idgen/identifiersource/:uuid
{
    "name": "New identifier",
    "description": "Description",
    "firstIdentifierBase": 10000,
    "baseCharacterSet": "0123456789ACDEFGHJKLMNPRTUVWXY",
    "prefix": "",
    "suffix": "",
    "minLength": 3,
    "maxLength": 10
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"New identifier\",\"description\": \"Description\",\"firstIdentifierBase\": 10000,\"baseCharacterSet\": \"0123456789ACDEFGHJKLMNPRTUVWXY\",\"prefix\": \"\",\"suffix\": \"\",\"minLength\": 3,\"maxLength\": 10}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Content-Type", "application/json");
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");

var raw = JSON.stringify({"name": "New identifier","description": "Description","firstIdentifierBase": 10000,"baseCharacterSet": "0123456789ACDEFGHJKLMNPRTUVWXY","prefix": "","suffix": "","minLength": 3,"maxLength": 10});

var requestOptions = {
  method: 'POST',
  headers: requestHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

To update a SequentialIdentifierGenerator you need to specify the below properties. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

Parameter                                   | Type                         | Description
---                                         | ---                          | ---              
*name*                                      | `String`                     | Name (Required)
*baseCharacterSet*                          | `String`                     | Character set for generating identifiers (Required)
*firstIdentifierBase*                       | `integer`                    | Base of first generated identifier (Required)
*description*                               | `String`                     | Description
*prefix*                                    | `String`                     | Identifier Prefix
*suffix*                                    | `String`                     | Identifier Suffix
*minLength*                                 | `integer`                    | Minimum Identifier length
*maxLength*                                 | `integer`                    | Maximum Identifier length          

## Update RemoteIdentifierSource

> Update RemoteIdentifierSource

```shell
POST /idgen/identifiersource/:uuid                                                                                                                                                                                                                                                                                                                                                                                                                                                          
{
    "name": "RemoteIdentifierSource",
    "description": "RemoteIdentifierSource",
    "url": "http://example.com",
    "username": "",
    "password": ""
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"RemoteIdentifierSource\",\"description\": \"RemoteIdentifierSource\",\"url\": \"http://example.com\",\"username\": \"\",\"password\": \"\"} ");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"name": "RemoteIdentifierSource","description": "RemoteIdentifierSource","url": "http://example.com","username": "","password": ""} );                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

To update a RemoteIdentifierSource you need to specify the below properties. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

Parameter                                   | Type                         | Description
---                                         | ---                          | ---           
*name*                                      | `String`                     | Name (Required)
*url*                                       | `URL`                        | Remote Source URL (Required)
*description*                               | `String`                     | Description
*username*                                  | `String`                     | Remote Source Username
*password*                                  | `String`                     | Remote Source Password

## Update IdentifierPool

> Update IdentifierPool

```shell
POST /idgen/identifiersource/:uuid                                                                                                                                                                                                                                                                                                                                                                                                                                                      
{
    "name": "IdentifierPool",
    "description": "IdentifierPool",
    "batchSize": 1000,
    "minPoolSize": 500,
    "sequential": true,
    "refillWithScheduledTask": false,
    "sourceUuid": ""
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"IdentifierPool\",\"description\": \"IdentifierPool\",\"batchSize\": 1000,\"minPoolSize\": 500,\"sequential\": true,\"refillWithScheduledTask\": false,\"sourceUuid\": \"\"}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"name": "IdentifierPool","description": "IdentifierPool","batchSize": 1000,"minPoolSize": 500,"sequential": true,"refillWithScheduledTask": false,"sourceUuid": ""});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

To update an IdentifierPool you need to specify the below properties. If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Properties

Parameter                                   | Type                         | Description
---                                         | ---                          | ---          
*name*                                      | `String`                     | Name (Required)
*description*                               | `String`                     | Description
*batchSize*                                 | `integer`                    | Batch Size
*minPoolSize*                               | `integer`                    | Minimum Pool Size
*sequential*                                | `String`                     | If true order is Sequential, if false order is Random
*refillWithScheduledTask*                   | `String`                     | If true pool is filled as a background task, if false, when you request an identifier
*sourceUuid*                                | `PatientIdentifierSource_UUID` | UUID of another source that you want to fill this pool from

## Delete a PatientIdentifierSource

> Delete a PatientIdentifierSource

```shell
DELETE /idgen/identifiersource/:uuid?purge=true
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid?purge=true")
  .method("DELETE", body)
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
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

Deletes or retires a target PatientIdentifierSource by its UUID. Returns a `404 Not Found` status if patient not exists. If the user is not logged in to perform this action, a `401 Unauthorized` status returned.

### Query Parameters

Parameter   | Type      | Description
---         | ---       | ---
*uuid*      | `String`  | UUID of PatientIdentifierSource to delete
*purge*     | `Boolean` | The resource will be retired unless purge = 'true'


## Export PatientIdentifiers from Source

> Export PatientIdentifiers from Source

```shell
POST /idgen/identifiersource
{
    "generateIdentifiers": true,
    "sourceUuid": "691eed12-c0f1-11e2-94be-8c13b969e334",
    "numberToGenerate": 10
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\n    \"generateIdentifiers\": true,\n    \"sourceUuid\": \"691eed12-c0f1-11e2-94be-8c13b969e334\",\n    \"numberToGenerate\": 10\n}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"generateIdentifiers": true,"sourceUuid": "691eed12-c0f1-11e2-94be-8c13b969e334","numberToGenerate": 10});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```  

> Success Response

```response
{
    "identifiers": [
        "1018P3",
        "1018R1",
        "1018TY",
        "1018UW",
        "1018VU",
        "1018WR",
        "1018XN",
        "1018YL",
        "10190J",
        "10191G"
    ]
}
```

You can export new identifiers from given source in batch by POSTing with properties below:

### Properties

Parameter                                   | Type                           | Description
---                                         | ---                            | ---           
*generateIdentifiers*                       | `Boolean`                      | Always set to "true" (Required)
*sourceUuid*                                | `PatientIdentifierSource_UUID` | Source UUID to generate identifiers from
*numberToGenerate*                          | `integer`                      | Number of identifiers you want to generate


## Reserve PatientIdentifiers in Source

> Reserve PatientIdentifiers in Source

```shell
POST /idgen/identifiersource/:uuid
{
    "reservedIdentifiers": "10501A,10502A,10503A,10504A,10505A"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\"reservedIdentifiers\": \"10501A,10502A,10503A,10504A,10505A\"}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"reservedIdentifiers": "10501A,10502A,10503A,10504A,10505A"});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```

You can reserve number of provided identifiers by sending POST request with below properties:

Works only with SequentialIdentifierGenerator Source type!  

### Properties

Parameter                                   | Type                           | Description
---                                         | ---                            | ---           
*reservedIdentifiers*                       | `String`                       | Identifiers to be reserved, divided by ","


## Upload PatientIdentifiers from Source

> Upload PatientIdentifiers from Source

```shell
POST /idgen/identifiersource/:uuid
{
    "operation": "uploadFromSource",
    "batchSize": 10
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\"operation\": \"uploadFromSource\",\"batchSize\": 10}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"operation": "uploadFromSource","batchSize": 10});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```

You can fill pool of identifiers from another source by sending POST request with below properties:

Works only with IdentifierPool Source type with set "sourceUuid"!  

## Upload PatientIdentifiers from Request Body

> Upload PatientIdentifiers from Request Body

```shell
POST /idgen/identifiersource/:uuid
{
    "operation": "uploadFromFile",
    "identifiers": "10501A,10502A,10503A,10504A,10505A"
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
MediaType mediaType = MediaType.parse("application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
RequestBody body = RequestBody.create(mediaType, "{\"operation\": \"uploadFromFile\",\"identifiers\": \"10501A,10502A,10503A,10504A,10505A\"}");                              
Request request = new Request.Builder()                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .url("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid")                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  .method("POST", body)                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")                                                                                                                                                                                                                                                                                                                                                                                                                                 
  .addHeader("Content-Type", "application/json")                                                                                                                                                                                                                                                                                                                                                                                                                                            
  .addHeader("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633")                                                                                                                                                                                                                                                                                                                                                                                                                       
  .build();                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
Response response = client.newCall(request).execute();                                                                                                                                                                                                                                                                                                                                                                                                                                      
```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

```javascript
var requestHeaders = new Headers();                                                                                                                                                                                                                                                                                                                                                                                                                                                         
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");                                                                                                                                                                                                                                                                                                                                                                                                                       
requestHeaders.append("Content-Type", "application/json");                                                                                                                                                                                                                                                                                                                                                                                                                                  
requestHeaders.append("Cookie", "JSESSIONID=24D0761924138ED7E55C2CB6806B0633");                                                                                                                                                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var raw = JSON.stringify({"operation": "uploadFromFile","identifiers": "10501A,10502A,10503A,10504A,10505A"});                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
var requestOptions = {                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  method: 'POST',                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
  headers: requestHeaders,                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
  body: raw,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
  redirect: 'follow'                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
};                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
fetch("/openmrs/ws/rest/v1/idgen/identifiersource/:uuid", requestOptions)                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(response => response.text())                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  .then(result => console.log(result))                                                                                                                                                                                                                                                                                                                                                                                                                                                      
  .catch(error => console.log('error', error));                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
```

You can fill pool of identifiers from another source by sending POST request with below properties:

Works only with IdentifierPool Source type!
