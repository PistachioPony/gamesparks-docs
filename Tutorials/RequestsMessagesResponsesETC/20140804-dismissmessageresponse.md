title: DismissMessageResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/dismissmessageresponse
author: GameSparks
description: 
post_id: 4339
created: 2014/08/04 15:33:42
created_gmt: 2014/08/04 15:33:42
comment_status: open
post_name: dismissmessageresponse
status: publish
post_type: post

<!--A response to a dismiss message request -->

# DismissMessageResponse

A response to a dismiss message request

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
      "@class" : ".DismissMessageResponse",
      "scriptData" : { }
    }