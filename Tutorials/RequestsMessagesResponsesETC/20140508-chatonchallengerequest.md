title: ChatOnChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/chatonchallengerequest
author: gabriel.page
description: 
post_id: 2226
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: chatonchallengerequest
status: publish
post_type: post

<!--Sends a message to all players involved in the challenge. The current player must be involved in the challenge for the message to be sent. -->

# ChatOnChallengeRequest

Sends a message to all players involved in the challenge. The current player must be involved in the challenge for the message to be sent.

As the message is sent to all players, the current player will also see details of the message in the response. Read the section on response message aggregation for a description of this.

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

The ID does not match a challenge the current player is involved with

  


## Example Request
    
    
    {
      "@class" : ".ChatOnChallengeRequest",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "message" : "A challenge message"
    }

## Example Response
    
    
    {
      "@class" : ".ChatOnChallengeResponse",
      "challengeInstanceId" : "524c13c7e4b0f3abf2b1ddc0",
      "scriptData" : { }
    }