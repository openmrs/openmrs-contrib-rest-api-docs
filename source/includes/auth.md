# Authentication

* Almost every API endpoint(other than the /session endpoint) in  OpenMRS API requires an authenticated user in order to interact.

* There is a filter defined on the module that intercepts all calls and authenticates the given request. 

* Currently, only BASIC authentication is supported. Along with the HTTP request, a request header of <b> Authorization: Basic 
(base64 of username:password) </b> needs to be sent.

<b>Alternatively, a session token can be used to interact with the API endpoints.</b>

## Retrieve session token

```console
GET /openmrs/ws/rest/v1/session 
-H 'Authorization: Basic Auth' (required to indetify the user)
```

This token should be passed with all subsequent calls as a cookie named <b>jsessionid=token</b>.

## Logout User/End session

```console
DELETE /openmrs/ws/rest/v1/session -H 'Accept: application/json'
-H 'Authorization: Basic Auth' (required to indetify the user)
```

## Changing Password

<b>Since version 2.17 of the webservices.rest module:</b>

* An administrator (with the EDIT_USER_PASSWORDS privilege) can change the password for other users.

```console
POST /openmrs/ws/rest/v1/password/target_user-UUID 
{
  "oldPassword" : "oldPassword",
  "newPassword" : "newPassword"
}
``` 

* After authenticating user can change their own password, by

```console
POST /openmrs/ws/rest/v1/password 
{
  "oldPassword" : "oldPassword",
  "newPassword" : "newPassword"
}
```

## Getting all location without authentication

Fetching locations requires you to <b> authenticate the user first </b>.If it is required to display all locations prior to login 
or without authentication you can do it by 

```console
GET /openmrs/ws/rest/v1/location?tag=Login%25Location' 
```
