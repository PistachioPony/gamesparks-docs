title: GetUploadedResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/getuploadedresponse
author: GameSparks
description: 
post_id: 4335
created: 2014/08/04 15:33:43
created_gmt: 2014/08/04 15:33:43
comment_status: open
post_name: getuploadedresponse
status: publish
post_type: post

<!--A reponse containing a time sensitive URL to a piece of content that was previously uploaded to the GameSparks platform by a player. -->

# GetUploadedResponse

A reponse containing a time sensitive URL to a piece of content that was previously uploaded to the GameSparks platform by a player.

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

size:number

The size of the file in bytes

url:string

A time sensitive URL to a piece of content

  


## Example
    
    
    {
      "@class" : ".GetUploadedResponse",
      "scriptData" : { },
      "size" : 100000,
      "url" : "http://gamesparksbinaries.blob.core.windows.net/upload-1234/c8bb7124f05b4a08ab4f4b2772b30d0a-map-data.xml..."
    }