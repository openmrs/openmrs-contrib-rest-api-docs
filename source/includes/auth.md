# Authentication

* Almost every API endpoint(other than the `/session` endpoint) in  OpenMRS API requires authentication 
  in order to interact.

* Currently, only BASIC authentication is supported. Along with the HTTP request, a request header of 
  `Authorization: Basic <base64 of username:password>` needs to be sent.

* Alternatively, a session token can be used to interact with the API endpoints.

* For example the base64 encoding of `admin:Admin123` is `YWRtaW46QWRtaW4xMjM=`


## Retrieve session token

> Retrieve session token

```shell
GET /openmrs/ws/rest/v1/session 
  -H 'Authorization: Basic Auth <base64 encoded username:password'
```

```java
	OkHttpClient client = new OkHttpClient().newBuilder()
			.build();
	Request request = new Request.Builder()
			.url("/openmrs/ws/rest/v1/session")
			.method("GET", null)
			.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
			.build();
	Response response = client.newCall(request).execute();

```
```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=2D158E83ACFB788998C7DB495F07C1B9");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/session", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

> Success Response

```response
{
    "sessionId": "2D158E83ACFB788998C7DB495F07C1B9",
    "authenticated": true,
    "user": {
        "uuid": "45ce6c2e-dd5a-11e6-9d9c-0242ac150002",
        "display": "admin",
        "username": "admin",
        "systemId": "admin",
        "userProperties": {
            "loginAttempts": "0",
            "emrapi.lastViewedPatientIds": "508,509,511,512,513,514,515,516,517,510,518,519,520,521,522,523,524,507,44,525"
        },
        "person": {
            "uuid": "24252571-dd5a-11e6-9d9c-0242ac150002"
        },
        "privileges": [],
        "roles": [
            {
                "uuid": "8d94f852-c2cc-11de-8d13-0010c6dffd0f",
                "name": "System Developer"
            },
            {
                "uuid": "8d94f280-c2cc-11de-8d13-0010c6dffd0f",
                "name": "Provider"
            }
        ]
    },
    "locale": "en_GB",
    "allowedLocales": [
        "en",
        "en_GB",
        "es",
        "fr",
        "it",
        "pt"
    ],
    "sessionLocation": null
}
```

 

* The session token is retrieved using Basic authentication on the `/session` endpoint. The response will include a `JSESSIONID` in the header. This session ID is also included in the response object



* The session token is retrieved using Basic authentication on the `/session` endpoint. The response will include a `JSESSIONID` in the header. This session ID is also included in the response object


* The `sessionId` token should be passed with all subsequent calls as a cookie named `JSESSIONID`.

## Logout User/End session

> Logout User/End session

```shell
DELETE /openmrs/ws/rest/v1/session -H 'Accept: application/json'
-H 'Authorization: Basic Auth' (required to identify the user)
```

```java
	OkHttpClient client = new OkHttpClient().newBuilder().build();
	Request request = new Request.Builder()
		.url("/openmrs/ws/rest/v1/session")
		.method("DELETE", null)
		.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
		.build();
	Response response = client.newCall(request).execute();		
```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=2D158E83ACFB788998C7DB495F07C1B9");

var requestOptions = {
  method: 'DELETE',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/session", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```



## Changing Password

> Password change By Admin

```shell
POST /openmrs/ws/rest/v1/password/:target_user_uuid 
{
  "newPassword" : "newPassword"
}
``` 

```java

	OkHttpClient client = new OkHttpClient().newBuilder()
			.build();
	MediaType mediaType = MediaType.parse("application/json");
	
	//password should contain atleast 1 integer
	RequestBody body = RequestBody.create(mediaType, "{ \r\n    \"newPassword\" : \"password1\"\r\n}");
	Request request = new Request.Builder()
			.url("/openmrs/ws/rest/v1/password/45ce6c2e-dd5a-11e6-9d9c-0242ac150002")
			.method("POST", body)
			.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
			.addHeader("Content-Type", "application/json")
			.build();
	Response response = client.newCall(request).execute();
}

```
```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=2D158E83ACFB788998C7DB495F07C1B9");

var raw = JSON.stringify({"newPassword":"newPassword1"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/password/45ce6c2e-dd5a-11e6-9d9c-0242ac150002", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


<b>Since version 2.17 of the webservices.rest module:</b>

* An administrator (with the `EDIT_USER_PASSWORDS` privilege) can change the password for other users by 
  posting a new password to `/password/:target_user_uuid`.
* The examples returns a `500 Internal server Error` status if we try to change the password associated with the admin user.so we should use a suitable user's UUID.
* The new password must contain atleast one integer.

> Password change By Users

```shell
POST /openmrs/ws/rest/v1/password 
{
  "oldPassword" : "oldPassword",
  "newPassword" : "newPassword"
}
```

```java
	OkHttpClient client = new OkHttpClient().newBuilder().build();
	MediaType mediaType = MediaType.parse("application/json");
	
	RequestBody body = RequestBody.create(mediaType, "{\r\n  \"oldPassword\" : \"Admin123\",\r\n  \"newPassword\" : \"newPassword1\"\r\n}");
	Request request = new Request.Builder()
	  .url("/openmrs/ws/rest/v1/password")
	  .method("POST", body)
	  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
	  .addHeader("Content-Type", "application/json")
	  .build();
	Response response = client.newCall(request).execute();
```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "JSESSIONID=2D158E83ACFB788998C7DB495F07C1B9");

var raw = JSON.stringify({"oldPassword":"Admin123","newPassword":"newPassword1"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/password \n", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```


* After authenticating user can change their own password, by posting to `/password`.
* The new password must contain atleast one integer.

## Getting all location without authentication

> Getting all location without authentication

```shell
GET /openmrs/ws/rest/v1/location?tag=Login+Location' 
```
```java

	OkHttpClient client = new OkHttpClient().newBuilder()
			.build();
	Request request = new Request.Builder()
			.url("/openmrs/ws/rest/v1/location?tag=Login+Location")
			.method("GET", null)
			.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
			.build();
	Response response = client.newCall(request).execute();

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Authorization", "Basic YWRtaW46QWRtaW4xMjM=");
myHeaders.append("Cookie", "JSESSIONID=2D158E83ACFB788998C7DB495F07C1B9");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://demo.openmrs.org/openmrs/ws/rest/v1/location?tag=Login+Location'\n", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```


* While fetching individual locations requires authentication, you can get a list of available locations by passing 
the special `tag` "Login Location" as a query parameter.


