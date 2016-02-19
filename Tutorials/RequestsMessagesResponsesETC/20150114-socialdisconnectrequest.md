title: SocialDisconnectRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/socialdisconnectrequest
author: GameSparks
description: 
post_id: 5671
created: 2015/01/14 12:23:48
created_gmt: 2015/01/14 12:23:48
comment_status: open
post_name: socialdisconnectrequest
status: publish
post_type: post

<!--Allows a player's internal profile to be disconnected from an external system to which it is linked.  Any friends linked as result of this connection will be removed. -->

# SocialDisconnectRequest

Allows a player's internal profile to be disconnected from an external system to which it is linked. Any friends linked as result of this connection will be removed.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

systemId:string
No

The external system from which to disconnect this profile.

#### Errors

NameValueDescription

systemId
REQUIRED

A systemId from which to disconnect must be provided

systemId
NOT_CONNECTED

The player does not have a connection with the provided system.

userName
CHANGE_REQUIRED

If the player's userName was derived from the profile they are disconnecting from, they must change it before they can disconnect. The userName can be changed via a ChangeUserDetailsRequest.

password
NOT_SET

Before disconnecting, if the player has no other connected profiles then they must have a password set in order to be able to authenticate in the future. A password can be set via a ChangeUserDetailsRequest.

  


## Example Request
    
    
    {
      "@class" : ".SocialDisconnectRequest",
      "systemId" : "FB"
    }

## Example Response
    
    
    {
      "@class" : ".SocialDisconnectResponse",
      "scriptData" : { }
    }