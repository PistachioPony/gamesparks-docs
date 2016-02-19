title: QQConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/qqconnectrequest
author: GameSparks
description: 
post_id: 8761
created: 2015/10/20 13:25:32
created_gmt: 2015/10/20 13:25:32
comment_status: open
post_name: qqconnectrequest
status: publish
post_type: post

<!--Allows a QQ access token to be used as an authentication mechanism. -->

# QQConnectRequest

Allows a QQ access token to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the QQ platform and store them within GameSparks.

If the QQ user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthenticationRequest or RegistrationRequest AND the QQ user is not already registered with the game, the QQ user will be linked to the current player.

If the current player has not authenticated and the QQ user is not known, a new player will be created using the QQ details and the session will be authenticated against the new player.

If the QQ user is already known, the session will switch to being the previously created user.

#### Parameters

Name : TypeRequiredDescription

accessToken:string
No

The access token is used by the client to make authenticated requests on behalf of the end user.

doNotLinkToCurrentPlayer:boolean
No

Indicates that the server should not try to link the external profile with the current player. If false, links the external profile to the currently signed in player. If true, creates a new player and links the external profile to them. Defaults to false.

errorOnSwitch:boolean
No

Indicates whether the server should return an error if an account switch would have occurred, rather than switching automatically. Defaults to false.

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

segments:JSON
No

An optional segment configuration for this request.

switchIfPossible:boolean
No

Indicates that the server should switch to the supplied profile if it isalready associated to a player. Defaults to false.

syncDisplayName:boolean
No

Indicates that the associated players displayName should be kept in syn with this profile when it's updated by the external provider.

#### Errors

NameValueDescription

accessToken
ACCOUNT_ALREADY_LINKED

The current user has a QQ profile and it's not the profile they have just tried to log in with

accessToken
NOTAUTHENTICATED

The system was unable to authenticate the token

accessToken
REQUIRED

The accessToken is missing

  


## Example Request
    
    
    {
      "@class" : ".QQConnectRequest",
      "accessToken" : "43E9534E912AS35&2E8F0836C1E",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "segments" : {
        "PROFILE" : "P1"
      },
      "switchIfPossible" : false,
      "syncDisplayName" : false
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