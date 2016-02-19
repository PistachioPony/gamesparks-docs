title: TwitterConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/twitterconnectrequest
author: gabriel.page
description: 
post_id: 2224
created: 2014/05/08 11:12:43
created_gmt: 2014/05/08 11:12:43
comment_status: closed
post_name: twitterconnectrequest
status: publish
post_type: post

<!--Allows a Twitter account to be used as an authentication mechanism. -->

# TwitterConnectRequest

Allows a Twitter account to be used as an authentication mechanism.

Once authenticated the platform can determine the current players details from the Twitter platform and store them within GameSparks.

GameSparks will determine the player's friends and whether any of them are currently registered with the game.

If the Twitter user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the Twitter user is not already registered with the game, the Twitter user will be linked to the current player.

If the current player has not authenticated and the Twitter user is not known, a new player will be created using the Twitter details and the session will be authenticated against the new player.

If the Twitter user is already known, the session will switch to being the previously created user.

#### Parameters

Name : TypeRequiredDescription

accessSecret:string
No

The accessSecret is obtained at the same time as the accessToken, and is required to sign requests to Twitter's services that require the accessToken.

accessToken:string
No

The accessToken represents a player's permission to share access to their account with your application.

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
NOTAUTHENTICATED

The system was unable to authenticate the token

accessToken
ACCOUNT_ALREADY_LINKED

The current user has a Twitter profile and it's not the profile they have just tried to log in with

accessToken
REQUIRED

Parameter accessToken is required but was not provided

accessSecret
REQUIRED

Parameter accessSecret is required but was not provided

  


## Example Request
    
    
    {
      "@class" : ".TwitterConnectRequest",
      "accessSecret" : "mytwitteraccesssecret",
      "accessToken" : "mytwitteraccesstoken",
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