title: GetUploadUrlResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/getuploadurlresponse
author: GameSparks
description: 
post_id: 4334
created: 2014/08/04 15:33:42
created_gmt: 2014/08/04 15:33:42
comment_status: open
post_name: getuploadurlresponse
status: publish
post_type: post

<!--A response containing a time sensitive URL to allow the game to upload a piece of player content to the GameSparks platform -->

# GetUploadUrlResponse

A response containing a time sensitive URL to allow the game to upload a piece of player content to the GameSparks platform

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

url:string

The time sensitive upload URL

  


## Example
    
    
    {
      "@class" : ".GetUploadUrlResponse",
      "scriptData" : { },
      "url" : "https://gsbeta-service1.gamesparks.net/upload/..."
    }