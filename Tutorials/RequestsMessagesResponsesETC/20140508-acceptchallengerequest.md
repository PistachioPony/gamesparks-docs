title: AcceptChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/acceptchallengerequest
author: gabriel.page
description: 
post_id: 2225
created: 2014/05/08 11:12:43
created_gmt: 2014/05/08 11:12:43
comment_status: closed
post_name: acceptchallengerequest
status: publish
post_type: post

<!--Accepts a challenge that has been issued to the current player. -->

# AcceptChallengeRequest

Accepts a challenge that has been issued to the current player.

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

The ID does not match a challenge the user is involved with

  


## Example Request
    
    
    {
      "@class" : ".AcceptChallengeRequest",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "message" : "A challenge message"
    }

## Example Response
    
    
    {
      "@class" : ".AcceptChallengeResponse",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "scriptData" : { }
    }