title: GooglePlusConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/googleplusconnectrequest
author: GameSparks
description: 
post_id: 5555
created: 2014/11/06 15:07:58
created_gmt: 2014/11/06 15:07:58
comment_status: closed
post_name: googleplusconnectrequest
status: publish
post_type: post

<!--Allows either a Google Plus access code to be used as an authentication mechanism. -->

# GooglePlusConnectRequest

Allows either a Google Plus access code to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the Google Plus platform and store them within GameSparks.

GameSparks will determine the player's friends and whether any of them are currently registered with the game.

If the Google Plus user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the Google Plus user is not already registered with the game, the Google Plus user will be linked to the current player.

If the current player has not authenticated and the Google Plus user is not known, a new player will be created using the Google Plus details and the session will be authenticated against the new player.

If the Google Plus user is already known, the session will switch to being the previously created user.

#### Parameters

Name : TypeRequiredDescription

accessToken:string
No

The access token is used when using the service id and certificate.

code:string
No

The access code is used by the client to make authenticated requests on behalf of the end user. Requires clientId and clientsecret to be set

doNotLinkToCurrentPlayer:boolean
No

Indicates that the server should not try to link the external profile with the current player. If false, links the external profile to the currently signed in player. If true, creates a new player and links the external profile to them. Defaults to false.

errorOnSwitch:boolean
No

Indicates whether the server should return an error if an account switch would have occurred, rather than switching automatically. Defaults to false.

redirectUri:string
No

Only required when the access code has been granted using an explicit redirectUri, for example when using the mechanism described in https://developers.google.com/+/web/signin/server-side-flow

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

code
NOTAUTHENTICATED

The system was unable to authenticate the code

accessToken|code
REQUIRED

Both the code and the accessToken are missing

GOOGLE_PLUS
NOT_CONFIGURED

The game has not been configured with the required Google Plus integration credentials

  


## Example Request
    
    
    {
      "@class" : ".GooglePlusConnectRequest",
      "accessToken" : "1/nBuJkI_xqMnVf_KZ09rEJpPSgo-ZDB7LKEWCZKeUaQU",
      "code" : "1/nBuJkI_xqMnVf_KZ09rEJpPSgo-ZDB7LKEWCZKeUaQU",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "redirectUri" : "postmessage",
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