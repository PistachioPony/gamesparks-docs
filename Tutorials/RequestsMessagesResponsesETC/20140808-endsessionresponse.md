title: EndSessionResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/endsessionresponse
author: GameSparks
description: 
post_id: 4484
created: 2014/08/08 08:43:42
created_gmt: 2014/08/08 08:43:42
comment_status: closed
post_name: endsessionresponse
status: publish
post_type: post

<!--A response to a send session request  -->

# EndSessionResponse

A response to a send session request 

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
      "@class" : ".EndSessionResponse",
      "scriptData" : { }
    }