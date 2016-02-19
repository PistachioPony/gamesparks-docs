title: GameSparksErrorResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/gamesparkserrorresponse
author: GameSparks
description: 
post_id: 4604
created: 2014/08/14 10:26:17
created_gmt: 2014/08/14 10:26:17
comment_status: closed
post_name: gamesparkserrorresponse
status: publish
post_type: post

<!--A response containing the details of an error -->

# GameSparksErrorResponse

A response containing the details of an error

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
      "@class" : ".GameSparksErrorResponse",
      "scriptData" : { }
    }