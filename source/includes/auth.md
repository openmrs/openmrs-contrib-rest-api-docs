# Authentication

* Almost every API endpoint(other than the `/session` endpoint) in  OpenMRS API requires authentication 
  in order to interact.

* Currently, only BASIC authentication is supported. Along with the HTTP request, a request header of 
  `Authorization: Basic <base64 of username:password>` needs to be sent.

* Alternatively, a session token can be used to interact with the API endpoints.


## Retrieve session token
```shell
GET /openmrs/ws/rest/v1/session 
  -H 'Authorization: Basic Auth <base64 encoded username:password'

HTTP/1.1 200 OK
Set-Cookie: JSESSIONID=FB0629C001449CE14DF1078ACDDBA858; Path=/openmrs; HttpOnly
{
    "authenticated": true,
    "locale": "en_GB",
    "sessionId": "FB0629C001449CE14DF1078ACDDBA858",
    "user": {
        "systemId": "admin",
    }
}
```
```java
	OkHttpClient client = new OkHttpClient().newBuilder()
			.build();
	Request request = new Request.Builder()
			.url("https://demo.openmrs.org/openmrs/ws/rest/v1/session")
			.method("GET", null)
			.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
			.build();
	Response response = client.newCall(request).execute();

```

 

The session token is retrieved using Basic authentication on the `/session` endpoint. The response will include a `JSESSIONID` in the header. This session ID is also included in the response object



The session token is retrieved using Basic authentication on the `/session` endpoint. The response will include a `JSESSIONID` in the header. This session ID is also included in the response object


The `sessionId` token should be passed with all subsequent calls as a cookie named `JSESSIONID`.

## Logout User/End session

```shell
DELETE /openmrs/ws/rest/v1/session -H 'Accept: application/json'
-H 'Authorization: Basic Auth' (required to identify the user)
```

```java
	OkHttpClient client = new OkHttpClient().newBuilder().build();
	Request request = new Request.Builder()
		.url("https://demo.openmrs.org/openmrs/ws/rest/v1/session")
		.method("DELETE", null)
		.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
		.build();
	Response response = client.newCall(request).execute();		
```



## Changing Password
```java

	OkHttpClient client = new OkHttpClient().newBuilder()
			.build();
	MediaType mediaType = MediaType.parse("application/json");
	
	//password should contain atleast 1 integer
	RequestBody body = RequestBody.create(mediaType, "{ \r\n    \"newPassword\" : \"password1\"\r\n}");
	Request request = new Request.Builder()
			.url("https://demo.openmrs.org/openmrs/ws/rest/v1/password/45ce6c2e-dd5a-11e6-9d9c-0242ac150002")
			.method("POST", body)
			.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
			.addHeader("Content-Type", "application/json")
			.build();
	Response response = client.newCall(request).execute();
}

```
```shell
POST /openmrs/ws/rest/v1/password/:target_user_uuid 
{
  "newPassword" : "newPassword"
}
``` 



<b>Since version 2.17 of the webservices.rest module:</b>

* An administrator (with the `EDIT_USER_PASSWORDS` privilege) can change the password for other users by 
  posting a new password to `/password/:target_user_uuid`.
* The new password must contain atleast one integer.

  
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
	  .url("https://demo.openmrs.org/openmrs/ws/rest/v1/password")
	  .method("POST", body)
	  .addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
	  .addHeader("Content-Type", "application/json")
	  .build();
	Response response = client.newCall(request).execute();
```

* After authenticating user can change their own password, by posting to `/password`.
* The new password must contain atleast one integer.

## Getting all location without authentication

```shell
GET /openmrs/ws/rest/v1/location?tag=Login+Location' 
```
```java

	OkHttpClient client = new OkHttpClient().newBuilder()
			.build();
	Request request = new Request.Builder()
			.url("https://demo.openmrs.org/openmrs/ws/rest/v1/location?tag=Login+Location")
			.method("GET", null)
			.addHeader("Authorization", "Basic YWRtaW46QWRtaW4xMjM=")
			.build();
	Response response = client.newCall(request).execute();

```

While fetching individual locations requires authentication, you can get a list of available locations by passing 
the special `tag` "Login Location" as a query parameter.


