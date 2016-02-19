title: MatchmakingResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/matchmakingresponse
author: GameSparks
description: 
post_id: 9659
created: 2015/11/16 15:09:13
created_gmt: 2015/11/16 15:09:13
comment_status: closed
post_name: matchmakingresponse
status: publish
post_type: post

<!--A response to a matchmaking request -->

# MatchmakingResponse

A response to a matchmaking request

#### Parameters

Name : TypeDescription

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
      "@class" : ".MatchmakingResponse",
      "scriptData" : { }
    }