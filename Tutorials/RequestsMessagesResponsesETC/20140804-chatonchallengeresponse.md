title: ChatOnChallengeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/chatonchallengeresponse
author: GameSparks
description: 
post_id: 4317
created: 2014/08/04 15:35:10
created_gmt: 2014/08/04 15:35:10
comment_status: open
post_name: chatonchallengeresponse
status: publish
post_type: post

<!--A response to a chat on challenge request -->

# ChatOnChallengeResponse

A response to a chat on challenge request

#### Parameters

Name : TypeDescription

challengeInstanceId:string

The challenge instance id

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
      "@class" : ".ChatOnChallengeResponse",
      "challengeInstanceId" : "524c13c7e4b0f3abf2b1ddc0",
      "scriptData" : { }
    }