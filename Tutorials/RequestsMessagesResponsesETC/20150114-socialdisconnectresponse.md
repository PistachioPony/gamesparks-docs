title: SocialDisconnectResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/socialdisconnectresponse
author: GameSparks
description: 
post_id: 5685
created: 2015/01/14 12:23:47
created_gmt: 2015/01/14 12:23:47
comment_status: open
post_name: socialdisconnectresponse
status: publish
post_type: post

<!--A response to a SocialDisconnectRequest -->

# SocialDisconnectResponse

A response to a SocialDisconnectRequest

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
      "@class" : ".SocialDisconnectResponse",
      "scriptData" : { }
    }