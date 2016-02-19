title: JoinChallengeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/joinchallengeresponse
author: GameSparks
description: 
post_id: 4323
created: 2014/08/04 15:33:46
created_gmt: 2014/08/04 15:33:46
comment_status: open
post_name: joinchallengeresponse
status: publish
post_type: post

<!--A response to a player joining a challenge -->

# JoinChallengeResponse

A response to a player joining a challenge

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
      "@class" : ".JoinChallengeResponse",
      "scriptData" : { }
    }