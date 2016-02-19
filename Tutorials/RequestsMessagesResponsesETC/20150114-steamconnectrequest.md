title: SteamConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/steamconnectrequest
author: GameSparks
description: 
post_id: 5663
created: 2015/01/14 12:23:49
created_gmt: 2015/01/14 12:23:49
comment_status: open
post_name: steamconnectrequest
status: publish
post_type: post

<!--Allows a Steam sessionTicket to be used as an authentication mechanism. -->

# SteamConnectRequest

Allows a Steam sessionTicket to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the Steam platform and store them within GameSparks.

GameSparks will determine the player's friends and whether any of them are currently registered with the game.

If the Steam user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the Steam user is not already registered with the game, the Steam user will be linked to the current player.

If the current player has not authenticated and the Steam user is not known, a new player will be created using the Steam details and the session will be authenticated against the new player.

If the Steam user is already known, the session will switch to being the previously created user.

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

sessionTicket:string
No

The hex encoded UTF-8 string representation of the ticket acquired calling the Steam SDKs GetAuthSessionTicket.

switchIfPossible:boolean
No

Indicates that the server should switch to the supplied profile if it isalready associated to a player. Defaults to false.

syncDisplayName:boolean
No

Indicates that the associated players displayName should be kept in syn with this profile when it's updated by the external provider.

#### Errors

NameValueDescription

sessionTicket
ACCOUNT_ALREADY_LINKED

The current user has a Steam profile and it's not the profile they have just tried to log in with

sessionTicket
NOTAUTHENTICATED

The system was unable to authenticate the sessionTicket

sessionTicket
REQUIRED

Parameter sessionTicket is required but was not provided

  


## Example Request
    
    
    {
      "@class" : ".SteamConnectRequest",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "segments" : {
        "PROFILE" : "P1"
      },
      "sessionTicket" : "140000003B97E8705D3D98D39C0C41010100100125E96D541800000001...",
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