title: PSNConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/psnconnectrequest
author: GameSparks
description: 
post_id: 9633
created: 2015/11/16 14:32:32
created_gmt: 2015/11/16 14:32:32
comment_status: closed
post_name: psnconnectrequest
status: publish
post_type: post

<!--Allows a PSN account to be used as an authentication mechanism. -->

# PSNConnectRequest

Allows a PSN account to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the PSN platform and store them within GameSparks.

GameSparks will determine the player's friends and whether any of them are currently registered with the game.

If the PSN user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the PSN user is not already registered with the game, the PSN user will be linked to the current player.

If the current player has not authenticated and the PSN user is not known, a new player will be created using the PSN details and the session will be authenticated against the new player.

If the PSN user is already known, the session will switch to being the previously created user.

#### Parameters

Name : TypeRequiredDescription

authorizationCode:string
No

The authorization code obtained from PSN, as described here https://ps4.scedev.net/resources/documents/SDK/latest/NpAuth-Reference/0008.html

doNotLinkToCurrentPlayer:boolean
No

Indicates that the server should not try to link the external profile with the current player. If false, links the external profile to the currently signed in player. If true, creates a new player and links the external profile to them. Defaults to false.

errorOnSwitch:boolean
No

Indicates whether the server should return an error if an account switch would have occurred, rather than switching automatically. Defaults to false.

redirectUri:string
No

When using the authorization code obtained from PlayStation®4/PlayStation®Vita/PlayStation®3, this is not required.

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

PSN
NOT_CONFIGURED

The game does not have the PSN integration details configured.

authorizationCode
NOTAUTHENTICATED

The system was unable to authenticate the authorizationCode

authorizationCode
ACCOUNT_ALREADY_LINKED

The current user has a PSN profile and it's not the profile they have just tried to log in with

authorizationCode
REQUIRED

Parameter authorizationCode is required but was not provided

  


## Example Request
    
    
    {
      "@class" : ".PSNConnectRequest",
      "authorizationCode" : "UhGYiW",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "redirectUri" : "UhGYiW",
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