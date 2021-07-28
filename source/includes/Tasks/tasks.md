# Task

## Available operations for Task

1. [List tasks](#list-tasks)
2. [Create a task](#create-a-task)
3. [Update a task](#update-a-task)
4. [Delete a task](#delete-a-task)
5. [Modify state of tasks](#modify-state-of-tasks)


## List tasks

> List tasks

```shell
GET /taskdefinition
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/taskdefinition
&v=default")
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

fetch("/openmrs/ws/rest/v1/taskdefinition", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Success Response

```response**
{
    "results": [
        {
            "uuid": "8c17b376-1a2b-11e1-a51a-00248140a5eb",
            "name": "Auto Close Visits Task",
            "description": "Stops all active visits that match the visit type(s) specified by the value of the global property 'visits.autoCloseVisitType'",
            "taskClass": "org.openmrs.scheduler.tasks.AutoCloseVisitsTask",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/taskdefinition/8c17b376-1a2b-11e1-a51a-00248140a5eb",
                    "resourceAlias": "taskdefinition"
                }
            ]
        },
        {
            "uuid": "eb9e447d-5ef9-4771-9e88-21916340b69c",
            "name": "Initialize Logic Rule Providers",
            "description": null,
            "taskClass": "org.openmrs.logic.task.InitializeLogicRuleProvidersTask",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/taskdefinition/eb9e447d-5ef9-4771-9e88-21916340b69c",
                    "resourceAlias": "taskdefinition"
                }
            ]
        },
        {
            "uuid": "0f49b674-f1d8-4b63-a4b3-d9422027e6af",
            "name": "Process HL7 Task",
            "description": null,
            "taskClass": "org.openmrs.scheduler.tasks.ProcessHL7InQueueTask",
            "links": [
                {
                    "rel": "self",
                    "uri": "http://localhost:8080/openmrs/ws/rest/v1/taskdefinition/0f49b674-f1d8-4b63-a4b3-d9422027e6af",
                    "resourceAlias": "taskdefinition"
                }
            ]
        }
    ]
}
```

You can add an `q=registered` parameter to return only tasks that are available to be scheduled. Otherwise will return all schedules tasks.
If not logged in to perform this action, a `401 Unauthorized` status is returned.

### Query Parameters

| Parameter        | Type           | Description                           |
| ---------------- | -------------- | ------------------------------------- |
| _q_ | `String`      | If set to "registered", will return only tasks that are available to be scheduled               |


## List task by name or id.

> List task by name or id

```shell
GET /taskdefinition/:name_or_id
```

```java

OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/taskdefinition/:name_or_id")
  .method("GET", null)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=3EFCD2FD54D00BE8491DFFD43AA706DC")
  .build();
Response response = client.newCall(request).execute();

```

```javascript

var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=3EFCD2FD54D00BE8491DFFD43AA706DC");

var requestOptions = {
  method: 'GET',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/taskdefinition/:name_or_id", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

Retrieve a Task by its Name or Id. Returns a `404 Not Found` status if Task does not exist. If user not logged in to perform this action, a `401 Unauthorized` status returned.


## Create a task

> Create a task

```shell
POST /taskdefinition
{
    "name": "task",
    "description": "description",
    "taskClass": "org.openmrs.scheduler.tasks.ProcessHL7InQueueTask",
    "startTime": "2021-06-30T19:14:14.000+0200",
    "repeatInterval": "5",
    "startOnStartup": true,
    "properties": {}
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"task\",\"description\": \"description\",\"taskClass\": \"org.openmrs.scheduler.tasks.ProcessHL7InQueueTask\",\"startTime\": \"2021-06-30T19:14:14.000+0200\",\"repeatInterval\": \"5\",\"startOnStartup\": true,\"properties\": {}}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/taskdefinition")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"name": "task","description": "description","taskClass": "org.openmrs.scheduler.tasks.ProcessHL7InQueueTask","startTime": "2021-06-30T19:14:14.000+0200","repeatInterval": "5","startOnStartup": true,"properties": {}});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/taskdefinition", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can create a new task by providing the attributes below.
If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter                   | Type                   | Description
--------------------------- | ---------------------- | ----
*name*                      | `String`               | Name of the task
*description*               | `String`               | Description of the task
*taskClass*                 | `String`               | Name of task's class that implements Task interface
*startTime*                 | `Date`                 | Date when the task will first start
*repeatInterval*            | `String`               | Number of seconds that this task will repeatedly run after
*properties*                | `Map<String,String>`   | Map of custom task's properties


## Update a Task

> Update a Task

```shell
POST /taskdefinition/:name_or_id
{
    "name": "task",
    "description": "description",
    "taskClass": "org.openmrs.scheduler.tasks.ProcessHL7InQueueTask",
    "startTime": "2021-06-30T19:14:14.000+0200",
    "repeatInterval": "5",
    "startOnStartup": true,
    "properties": {}
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\": \"task\",\"description\": \"description\",\"taskClass\": \"org.openmrs.scheduler.tasks.ProcessHL7InQueueTask\",\"startTime\": \"2021-06-30T19:14:14.000+0200\",\"repeatInterval\": \"5\",\"startOnStartup\": true,\"properties\": {}}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/taskdefinition/:name_or_id")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"name": "task","description": "description","taskClass": "org.openmrs.scheduler.tasks.ProcessHL7InQueueTask","startTime": "2021-06-30T19:14:14.000+0200","repeatInterval": "5","startOnStartup": true,"properties": {}});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/taskdefinition/:name_or_id", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can update existing task by its id or name. To update one, you have to provide the attributes below.
Returns a `404 Not Found` status if Task does not exist.
If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter                   | Type                   | Description
--------------------------- | ---------------------- | ----
*name*                      | `String`               | Name of the task
*description*               | `String`               | Description of the task
*taskClass*                 | `String`               | Name of task's class that implements Task interface
*startTime*                 | `Date`                 | Date when the task will first start
*repeatInterval*            | `String`               | Number of seconds that this task will repeatedly run after
*properties*                | `Map<String,String>`   | Map of custom task's properties


## Delete a Task

> Delete a Task

```shell
DELETE /taskdefinition/:uuid?purge=true
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = RequestBody.create(mediaType, "");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/taskdefinition/:uuid?purge=true")
  .method("DELETE", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Cookie", "JSESSIONID=154692F02BBBC664825F3C4C224A474B")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var requestHeaders = new Headers();
requestHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
requestHeaders.append("Cookie", "JSESSIONID=955E778A4F700C5AA9651DAF6FC9DDDA");

var requestOptions = {
  method: 'DELETE',
  headers: requestHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/taskdefinition/:uuid?purge=true", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

Deletes (purges) a Task by its name or id. Returns a `404 Not Found` status if the task does not exist. If not logged in to perform this action, a `401 Unauthorized` status is returned.

Voiding tasks is not supported.


## Modify state of tasks

> Modify state of tasks

```shell
POST /taskaction
{
    "action": "RESCHEDULETASK",
    "tasks": ["Auto Close Visits Task"]
}
```

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"action\": \"RESCHEDULETASK\",\"tasks\": [\"Auto Close Visits Task\"]}");
Request request = new Request.Builder()
  .url("/openmrs/ws/rest/v1/taskaction")
  .method("POST", body)
  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
  .addHeader("Content-Type", "application/json")
  .addHeader("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=DF385B2E6E39E0BB49BB7E079BF31C44");

var raw = JSON.stringify({"action": "RESCHEDULETASK","tasks": ["Auto Close Visits Task"]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("/openmrs/ws/rest/v1/taskaction", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

You can execute the following actions on tasks:

* schedule tasks `SCHEDULETASK`
* stop tasks `SHUTDOWNTASK`
* run tasks `RUNTASK`
* restart tasks `RESCHEDULETASK`
* restart all tasks `RESCHEDULEALLTASKS`
* delete tasks `DELETE`

If you are not logged in to perform this action, a `401 Unauthorized` status is returned.

### Attributes

Parameter                   | Type                   | Description
--------------------------- | ---------------------- | ----
*action*                    | `String`               | One of the following actions: `[SCHEDULETASK, SHUTDOWNTASK, RESCHEDULETASK, RESCHEDULEALLTASKS, DELETE, RUNTASK]`
*tasks*                     | `Array[]: String`      | List of tasks' ids or names that will be involved in the action above. Not provided with `RESCHEDULEALLTASKS` action.
