title: GameCenterConnectRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/gamecenterconnectrequest
author: GameSparks
description: 
post_id: 8041
created: 2015/06/10 14:46:48
created_gmt: 2015/06/10 14:46:48
comment_status: closed
post_name: gamecenterconnectrequest
status: publish
post_type: post

<!--Allows an Apple account that has GameCenter to be used as an authentication mechanism. -->

# GameCenterConnectRequest

Allows an Apple account that has GameCenter to be used as an authentication mechanism.

The request must supply the GameCenter user details, such as the player id and username.

If the GameCenter user is already linked to a player, the current session will switch to the linked player.

If the current player has previously created an account using either DeviceAuthentictionRequest or RegistrationRequest AND the GameCenter user is not already registered with the game, the GameCenter user will be linked to the current player.

If the current player has not authenticated and the GameCenter user is not known, a new player will be created using the GameCenter details and the session will be authenticated against the new player.

If the GameCenter user is already known, the session will switch to being the previously created user.

This API call requires the output details from GKLocalPlayer.generateIdentityVerificationSignatureWithCompletionHandler on your iOS device

#### Parameters

Name : TypeRequiredDescription

displayName:string
No

The display of the current player from GameCenter. This will be used as the displayName of the gamesparks player if created (or syncDisplayname is true)

doNotLinkToCurrentPlayer:boolean
No

Indicates that the server should not try to link the external profile with the current player. If false, links the external profile to the currently signed in player. If true, creates a new player and links the external profile to them. Defaults to false.

errorOnSwitch:boolean
No

Indicates whether the server should return an error if an account switch would have occurred, rather than switching automatically. Defaults to false.

externalPlayerId:string
No

The game center id of the current player. This value obtained be obtained from GKLocalPlayer playerID

publicKeyUrl:string
No

The url from where we will download the public key. This value should be obtained from generateIdentityVerificationSignatureWithCompletionHandler. 

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

salt:string
No

The salt is needed in order to prevent request forgery. This value should be obtained from generateIdentityVerificationSignatureWithCompletionHandler and should be base64 encoded using [salt base64Encoding]

segments:JSON
No

An optional segment configuration for this request.

signature:string
No

The signature is needed to validate that the request is genuine and that we can save the player. This value should be obtained from generateIdentityVerificationSignatureWithCompletionHandler and should be base64 encoded using [signature base64Encoding]

switchIfPossible:boolean
No

Indicates that the server should switch to the supplied profile if it isalready associated to a player. Defaults to false.

syncDisplayName:boolean
No

Indicates that the associated players displayName should be kept in syn with this profile when it's updated by the external provider.

timestamp:number
No

The timestamp is needed to validate the request signature. This value should be obtained from generateIdentityVerificationSignatureWithCompletionHandler

#### Errors

NameValueDescription

externalPlayerId
ACCOUNT_ALREADY_LINKED

The current user has a GameCenter profile and it's not the profile they have just tried to log in with

signature
NOTAUTHENTICATED

The system was unable to validate the request

publicKeyUrl
REQUIRED

The publicKeyUrl is required but not provided

timestamp
REQUIRED

The timestamp is required but not provided

timestamp
EXPIRED

The request expired

signature
REQUIRED

The signature is required but not provided

salt
REQUIRED

The salt is required but not provided

externalPlayerId
REQUIRED

The externalPlayerId is required but not provided

displayName
REQUIRED

The displayName is required but not provided

  


## Example Request
    
    
    {
      "@class" : ".GameCenterConnectRequest",
      "displayName" : "myUser",
      "doNotLinkToCurrentPlayer" : false,
      "errorOnSwitch" : false,
      "externalPlayerId" : "1234567890",
      "publicKeyUrl" : "https://sandbox.gc.apple.com/public-key/gc-sb-2.cer",
      "salt" : "nahtin==",
      "segments" : {
        "PROFILE" : "P1"
      },
      "signature" : "nahtin==",
      "switchIfPossible" : false,
      "syncDisplayName" : false,
      "timestamp" : 1234567890
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