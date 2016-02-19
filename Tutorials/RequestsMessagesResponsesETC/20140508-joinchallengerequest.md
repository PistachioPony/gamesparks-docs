title: JoinChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/joinchallengerequest
author: gabriel.page
description: 
post_id: 2231
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: joinchallengerequest
status: publish
post_type: post

<!--Allows a player to join an open challenge. -->

# JoinChallengeRequest

Allows a player to join an open challenge.

#### Parameters

Name : TypeRequiredDescription

challengeInstanceId:string
Yes

The ID of the challenge

eligibility:JSON
Yes

Optional. Allows the current player's eligibility to be overridden by what is provided here.

message:string
No

An optional message to send with the challenge

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

challengeInstanceId
UNKNOWN

No challenge could be found with the given challengeInstanceId

JOIN
NOT_FRIEND

The player is trying to join a FRIENDS challenge that is owned by someone with whom they are not a friend

JOIN
Must be a PUBLIC|FRIENDS challenge to join

The player is trying to join a PRIVATE challenge, should use AcceptChallengeRequest instead

eligibility
{ "XXX" : "UNRECOGNISED"}

XXX is not a valid field of eligibility

eligibility
{ "segments" : {"XXX" : "MALFORMED"}}

The value provied for XXX is not in the correct format

eligibility
{ "missingSegments" : {"XXX" : ["YYY", "ZZZ"]}}

To join this challenge the player must have segment XXX with value YYY or ZZZ

eligibility
{ "invalidSegments" : { "actual" : {"XXX" : "YYY"}, "required" : {"XXX" : "ZZZ"}}

This player has segment XXX value YYY however this challenge requires a segment XXX value of ZZZ

  


## Example Request
    
    
    {
      "@class" : ".JoinChallengeRequest",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "eligibility" : {
        "segments" : {
          "segment1" : "value1",
          "segment2" : "value2"
        }
      },
      "message" : "A challenge message"
    }

## Example Response
    
    
    {
      "@class" : ".JoinChallengeResponse",
      "scriptData" : { }
    }