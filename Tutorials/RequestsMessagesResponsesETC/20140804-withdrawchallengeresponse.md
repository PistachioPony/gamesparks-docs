title: WithdrawChallengeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/withdrawchallengeresponse
author: GameSparks
description: 
post_id: 4327
created: 2014/08/04 15:33:46
created_gmt: 2014/08/04 15:33:46
comment_status: open
post_name: withdrawchallengeresponse
status: publish
post_type: post

<!--A response containing the challenge instance id that was withdrawn by a player -->

# WithdrawChallengeResponse

A response containing the challenge instance id that was withdrawn by a player

#### Parameters

Name : TypeDescription

challengeInstanceId:string

A challenge instance id

requestId:string

The ID of the corresponding Request

scriptData:ScriptData

A JSON Map of any data added either to the Request or the Response by your Cloud Code

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Name:TypeDescription

myKey:string
An arbitrary data key

myValue:JSON
An arbitrary data value.
  


## Example
    
    
    {
      "@class" : ".WithdrawChallengeResponse",
      "challengeInstanceId" : "524d4101e4b0f3abf2b2421c",
      "scriptData" : { }
    }