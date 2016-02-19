title: RegistrationRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/registrationrequest
author: gabriel.page
description: 
post_id: 2223
created: 2014/05/08 11:12:43
created_gmt: 2014/05/08 11:12:43
comment_status: closed
post_name: registrationrequest
status: publish
post_type: post

<!--Allows a new player to be created using a username, password display name. -->

# RegistrationRequest

Allows a new player to be created using a username, password display name.

#### Parameters

Name : TypeRequiredDescription

displayName:string
Yes

A display name to use

password:string
Yes

The previously registered password

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

segments:JSON
No

An optional segment configuration for this request.

userName:string
Yes

The previously registered player name

#### Errors

NameValueDescription

USERNAME
TAKEN

The userName supplied is already in use.

  


## Example Request
    
    
    {
      "@class" : ".RegistrationRequest",
      "displayName" : "my nickname",
      "password" : "mypassword",
      "segments" : {
        "PROFILE" : "P1"
      },
      "userName" : "gabriel"
    }

## Example Response
    
    
    {
      "@class" : ".RegistrationResponse",
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