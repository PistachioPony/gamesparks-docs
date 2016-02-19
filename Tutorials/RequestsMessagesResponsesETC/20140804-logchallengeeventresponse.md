title: LogChallengeEventResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/logchallengeeventresponse
author: GameSparks
description: 
post_id: 4326
created: 2014/08/04 15:33:45
created_gmt: 2014/08/04 15:33:45
comment_status: open
post_name: logchallengeeventresponse
status: publish
post_type: post

<!--A response to a log challenge event request  -->

# LogChallengeEventResponse

A response to a log challenge event request 

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
      "@class" : ".LogChallengeEventResponse",
      "scriptData" : { }
    }