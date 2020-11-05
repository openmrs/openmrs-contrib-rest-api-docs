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

GET /systeminformation

```

> Success Response

```response

{
    "systemInfo": {
        "SystemInfo.title.openmrsInformation": {
            "SystemInfo.OpenMRSInstallation.systemDate": "2020-10-14",
            "SystemInfo.OpenMRSInstallation.systemTime": "20:05:43",
            "SystemInfo.OpenMRSInstallation.openmrsVersion": "2.3.0  Build b3ade0",
            "SystemInfo.hostname": "f945457f1f48"
        },
        "SystemInfo.title.javaRuntimeEnvironmentInformation": {
            "SystemInfo.JavaRuntimeEnv.operatingSystem": "Linux",
            "SystemInfo.JavaRuntimeEnv.operatingSystemArch": "amd64",
            "SystemInfo.JavaRuntimeEnv.operatingSystemVersion": "4.4.0-190-generic",
            "SystemInfo.JavaRuntimeEnv.javaVersion": "1.8.0_212",
            "SystemInfo.JavaRuntimeEnv.javaVendor": "Oracle Corporation",
            "SystemInfo.JavaRuntimeEnv.jvmVersion": "25.212-b01",
            "SystemInfo.JavaRuntimeEnv.jvmVendor": "Oracle Corporation",
            "SystemInfo.JavaRuntimeEnv.javaRuntimeName": "OpenJDK Runtime Environment",
            "SystemInfo.JavaRuntimeEnv.javaRuntimeVersion": "1.8.0_212-8u212-b01-1~deb9u1-b01",
            "SystemInfo.JavaRuntimeEnv.userName": "root",
            "SystemInfo.JavaRuntimeEnv.systemLanguage": "en",
            "SystemInfo.JavaRuntimeEnv.systemTimezone": "Etc/UTC",
            "SystemInfo.JavaRuntimeEnv.fileSystemEncoding": "UTF-8",
            "SystemInfo.JavaRuntimeEnv.userDirectory": "/usr/local/tomcat",
            "SystemInfo.JavaRuntimeEnv.tempDirectory": "/usr/local/tomcat/temp"
        },
        "SystemInfo.title.memoryInformation": {
            "SystemInfo.Memory.totalMemory": "607 MB",
            "SystemInfo.Memory.freeMemory": "350 MB",
            "SystemInfo.Memory.maximumHeapSize": "683 MB"
        },
        "SystemInfo.title.dataBaseInformation": {
            "SystemInfo.Database.name": "\"openmrs-db\"",
            "SystemInfo.Database.connectionURL": "jdbc:mysql://openmrs-referenceapplication-mysql:3306/\"openmrs-db\"?autoReconnect=true&sessionVariables=default_storage_engine=InnoDB&useUnicode=true&characterEncoding=UTF-8",
            "SystemInfo.Database.userName": "\"openmrs-user\"",
            "SystemInfo.Database.driver": null,
            "SystemInfo.Database.dialect": null
        },
        "SystemInfo.title.moduleInformation": {
            "SystemInfo.Module.repositoryPath": "/usr/local/tomcat/.OpenMRS/modules",
            "Atlas Module": "2.2 ",
            "Form Entry App Module": "1.4.2 ",
            "Reporting": "1.20.0 ",
            "Metadata Sharing": "1.6.0 ",
            "ID Generation": "4.5.0 ",
            "Allergy UI Module": "1.8.2 ",
            "EMR API Module": "1.28.0 ",
            "Registration App Module": "1.16.0 ",
            "HTML Form Entry UI Framework Integration Module": "1.10.0 ",
            "App Framework Module": "2.14.0 ",
            "Reporting REST": "1.11.0 ",
            "Reference Metadata Module": "2.10.2 ",
            "Metadata Mapping": "1.3.4 ",
            "Admin UI Module": "1.3.0 ",
            "OpenMRS UI Framework": "3.17.0 ",
            "Reference Application Module": "2.10.0 ",
            "Metadata Deploy": "1.11.0 ",
            "App UI Module": "1.12.0 ",
            "Reporting Compatibility": "2.0.6 ",
            "HTML Widgets": "1.10.0 ",
            "Serialization Xstream": "0.2.14 ",
            "Address Hierarchy": "2.11.0 ",
            "Registration Core Module": "1.9.0 ",
            "Attachments": "2.2.0 ",
            "Core Apps Module": "1.28.0 ",
            "Event Module": "2.7.0 ",
            "Provider Management Module": "2.10.0 ",
            "Calculation": "1.2 ",
            "Appointment Scheduling UI Module": "1.9.0 ",
            "Open Web Apps Module": "1.10.0 ",
            "HTML Form Entry": "3.10.0 ",
            "FHIR Module": "1.20.0 ",
            "UI Commons Module": "2.12.0 ",
            "Reporting UI Module": "1.6.0 ",
            "Appointment Scheduling Module": "1.12.0 ",
            "Rest Web Services OMOD": "2.28.0.df1459 ",
            "Legacy UI Module": "1.6.0 ",
            "Data Exchange Module": "1.3.4 ",
            "Reference Demo Data Module": "1.4.5 ",
            "UI Library Module": "2.0.6 "
        }
    }
}

```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/systeminformation")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=ACC5AAAB3FE29B0A1A2C239EC00B8710");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/systeminformation", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* Fetch all System Information that match any specified parameters otherwise fetch all the System Information if no query parameters specified. 
* If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

### Query Parameters

    Parameter | Type | Description
    --- | --- | ---
    *limit* | `integer`| use this parameter to limit the number of results to be returned 
    *startIndex*| `integer` | the offset where to start the query
    *v* | `String` | the required representation to return (i.e., ref, default, full or custom )

