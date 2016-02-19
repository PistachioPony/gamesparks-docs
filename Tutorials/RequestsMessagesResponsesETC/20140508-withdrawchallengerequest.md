title: WithdrawChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/withdrawchallengerequest
author: gabriel.page
description: 
post_id: 2235
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: withdrawchallengerequest
status: publish
post_type: post

<!--Withdraws a challenge previously issued by the current player. -->

# WithdrawChallengeRequest

Withdraws a challenge previously issued by the current player.

This can only be done while the challenge is in the ISSUED state. Once it's been accepted the challenge can not be withdrawn.

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

The ID does not match a challenge in the ISSUED state that was issued by the current player

  


## Example Request
    
    
    {
      "@class" : ".WithdrawChallengeRequest",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "message" : "A challenge message"
    }

## Example Response
    
    
    {
      "@class" : ".WithdrawChallengeResponse",
      "challengeInstanceId" : "524d4101e4b0f3abf2b2421c",
      "scriptData" : { }
    }