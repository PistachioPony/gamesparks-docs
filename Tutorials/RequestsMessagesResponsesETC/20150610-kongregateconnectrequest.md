title: KongregateConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/kongregateconnectrequest
author: GameSparks
description: 
post_id: 8045
created: 2015/06/10 14:46:46
created_gmt: 2015/06/10 14:46:46
comment_status: closed
post_name: kongregateconnectrequest
status: publish
post_type: post

<!--Allows a Kongregate account to be used as an authentication mechanism. -->

# KongregateConnectRequest

Allows a Kongregate account to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the Kongregate platform and store them within GameSparks.

If the Kongregate user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the Kongregate user is not already registered with the game, the Kongregate user will be linked to the current player.

If the current player has not authenticated and the Kongregate user is not known, a new player will be created using the Kongregate details and the session will be authenticated against the new player.

If the Kongregate user is already known, the session will switch to being the previously created user.

#### Parameters

Name : TypeRequiredDescription

doNotLinkToCurrentPlayer:boolean
No

Indicates that the server should not try to link the external profile with the current player. If false, links the external profile to the currently signed in player. If true, creates a new player and links the external profile to them. Defaults to false.

errorOnSwitch:boolean
No

Indicates whether the server should return an error if an account switch would have occurred, rather than switching automatically. Defaults to false.

gameAuthToken:string
No

The gameAuthToken, together with the userID are used by the client to make authenticated requests on behalf of the end user.

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

userId:string
No

The userID, together with the gameAuthToken are used by the client to make authenticated requests on behalf of the end user.

#### Errors

NameValueDescription

userId
ACCOUNT_ALREADY_LINKED

The current user has a Kongregate profile and it's not the profile they have just tried to log in with

gameAuthToken
NOTAUTHENTICATED

The system was unable to authenticate the user id

gameAuthToken
NOTAUTHENTICATED

The system was unable to authenticate the user

userId
REQUIRED

The userId is required but not provided

gameAuthToken
REQUIRED

The gameAuthToken is required but not provided

  


## Example Request
    
    
    {
      "@class" : ".KongregateConnectRequest",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "gameAuthToken" : "abc1234",
      "segments" : {
        "PROFILE" : "P1"
      },
      "switchIfPossible" : false,
      "syncDisplayName" : false,
      "userId" : "1234"
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