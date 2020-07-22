# System Information

## System Information Overview

* System Information directly fetches the system information from AdministrationService and displays it by splitting it into name value pairs across 5 headers in legacy UI module.

   Header | Brief Description         
   --|--
1.   OpenMRS Information | This section holds information like OpenMRS Version Snapshot and other system wide informations like System Date and Time. 
2.   Java Runtime Environment Information | This section has the relevant Java parameters along with the the operating system and its architecture information.For e.g. `Operating System` : `Linux`
3.   Memory Information | This section holds the total , free and the maximum heap Size memory information of the system.
4.   Database Information | This section has the relevant information about the database.  For  e.g. `Database Schema name` : `openmrs-db`  
5.   Module Information | This section has the record of all the snapshot versions for each of the current modules. For e.g. `Allergy UI Module` : `1.8.3-SNAPSHOT`
 
  

## Available operations for systeminformation type.

## List System Inforamation

> List system information

```shell

GET /systeminformation?limit=5&startIndex=0&v=default

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://qa-refapp.openmrs.org/openmrs/ws/rest/v1/systeminformation?limit=5&startIndex=0&v=default
")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=DECF639CF6A8545F34637E1F339972D8")
  .build();
Response response = client.newCall(request).execute();

```

* Fetch all System Information that match any specified parameters otherwise fetch all the System Information if no query parameters specified. 
* If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *limit* | `integer`| use this parameter to limit the number of results to be returned 
    *startIndex*| `integer` | the offset where to start the query
    *v* | `String` | the required representation to return (i.e., ref, default, full or custom )

