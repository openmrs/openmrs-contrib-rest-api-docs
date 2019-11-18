# Authentication

* Almost every API endpoint(other than the `/session` endpoint) in  OpenMRS API requires authentication 
  in order to interact.

* Currently, only BASIC authentication is supported. Along with the HTTP request, a request header of 
  `Authorization: Basic <base64 of username:password>` needs to be sent.

* Alternatively, a session token can be used to interact with the API endpoints.

## Retrieve session token

The session token is retrieved using Basic authentication on the `/session` endpoint. The response will 
include a `JSESSIONID` in the header. This session ID is also included in the response objec

```console
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

The `sessionId` token should be passed with all subsequent calls as a cookie named `JSESSIONID`.

## Logout User/End session

```console
DELETE /openmrs/ws/rest/v1/session -H 'Accept: application/json'
-H 'Authorization: Basic Auth' (required to indetify the user)
```

## Changing Password

<b>Since version 2.17 of the webservices.rest module:</b>

* An administrator (with the `EDIT_USER_PASSWORDS` privilege) can change the password for other users by 
  posting a new password to `/password/:target_user_uuid`.

```console
POST /openmrs/ws/rest/v1/password/:target_user_uuid 
{
  "newPassword" : "newPassword"
}
``` 

* After authenticating user can change their own password, by posting to `/password`

```console
POST /openmrs/ws/rest/v1/password 
{
  "oldPassword" : "oldPassword",
  "newPassword" : "newPassword"
}
```

## Getting all location without authentication

While fetching individual locations requires authentication, you can get a list of available locations by passing 
the special `tag` "Login Location" as a query parameter.

```console
GET /openmrs/ws/rest/v1/location?tag=Login+Location' 
```
