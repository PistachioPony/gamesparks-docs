title: XBOXLiveConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/xboxliveconnectrequest
author: GameSparks
description: 
post_id: 6024
created: 2015/02/12 17:27:42
created_gmt: 2015/02/12 17:27:42
comment_status: open
post_name: xboxliveconnectrequest
status: publish
post_type: post

<!--Allows an Xbox Live Shared Token String to be used as an authentication mechanism. -->

# XBOXLiveConnectRequest

Allows an Xbox Live Shared Token String to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the Xbox Live and store them within GameSparks.

GameSparks will determine the player's friends and whether any of them are currently registered with the game.

If the Xbox user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the Xbox user is not already registered with the game, the Xbox user will be linked to the current player.

If the current player has not authenticated and the Xbox user is not known, a new player will be created using the Xbox details and the session will be authenticated against the new player.

If the Xbox user is already known, the session will switch to being the previously created user.

#### Parameters

Name : TypeRequiredDescription

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

stsTokenString:string
No

The access token is used by the client to make authenticated requests on behalf of the end user.

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

The current user has a Xbox profile and it's not the profile they have just tried to log in with

code
NOTAUTHENTICATED

The system was unable to authenticate the code

accessToken
NOTAUTHENTICATED

The system was unable to authenticate the token

  


## Example Request
    
    
    {
      "@class" : ".XBOXLiveConnectRequest",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "segments" : {
        "PROFILE" : "P1"
      },
      "stsTokenString" : "CAAB72Fsyk4MBANwlJMC4dn6ZB29lyzhQxYVNDn8JeJbg7jam6cFwwzzZBrggfUgK8d3Iov5AXdkkN1Bo8XptwM77pZCYd59ZAEe33ZCDrfq9Rll5PszQ1sUUqK3PaxTkp0pezb1YWBAZCZBcdbzn9ECE963lCG3Hmpp3jZAhhOpIuyOqNhkp788cSS8F1wSOQjkZD",
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