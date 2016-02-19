title: DeclineChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/declinechallengerequest
author: gabriel.page
description: 
post_id: 2228
created: 2014/05/08 11:13:56
created_gmt: 2014/05/08 11:13:56
comment_status: closed
post_name: declinechallengerequest
status: publish
post_type: post

<!--Declines a challenge that has been issued to the current player. -->

# DeclineChallengeRequest

Declines a challenge that has been issued to the current player.

#### Parameters

Name : TypeRequiredDescription

challengeInstanceId:string
Yes

The ID of the challenge

message:string
No

An optional message to send with the challenge

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

challengeInstanceId
INVALID

The ID does not match a challenge that has been issued

  


## Example Request
    
    
    {
      "@class" : ".DeclineChallengeRequest",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "message" : "A challenge message"
    }

## Example Response
    
    
    {
      "@class" : ".DeclineChallengeResponse",
      "challengeInstanceId" : "524d4877e4b0f3abf2b244f7",
      "scriptData" : { }
    }