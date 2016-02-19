title: AuthenticationRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/authenticationrequest
author: gabriel.page
description: 
post_id: 2220
created: 2014/05/08 11:13:56
created_gmt: 2014/05/08 11:13:56
comment_status: closed
post_name: authenticationrequest
status: publish
post_type: post

<!--Provides authentication using a username/password combination. -->

# AuthenticationRequest

Provides authentication using a username/password combination.

The username will have been previously created using a RegistrationRequest.

#### Parameters

Name : TypeRequiredDescription

password:string
Yes

The previously registered password

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

userName:string
Yes

The previously registered player name

#### Errors

NameValueDescription

DETAILS
UNRECOGNISED

The userName password combination did not match any existing account

DETAILS
LOCKED

There have been too many failed login attempts with these details, the account has been locked temporarily

  


## Example Request
    
    
    {
      "@class" : ".AuthenticationRequest",
      "password" : "mypassword",
      "userName" : "gabriel"
    }

## Example Response
    
    
    {
      "@class" : ".AuthenticationResponse",
      "authToken" : "524c13c7e4b0f3abf2b1ddc0",
      "displayName" : "Nick",
      "newPlayer" : false,
      "scriptData" : { },
      "switchSummary" : {
        "achievements" : [ "..." ],
        "displayName" : "...",
        "externalIds" : "...",
        "id" : "...",
        "online" : false,
        "scriptData" : { },
        "virtualGoods" : [ "..." ]
      },
      "userId" : "523b0628e4b0aba320077410"
    }