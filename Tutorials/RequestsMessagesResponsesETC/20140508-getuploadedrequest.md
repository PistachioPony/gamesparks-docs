title: GetUploadedRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/getuploadedrequest
author: gabriel.page
description: 
post_id: 2243
created: 2014/05/08 11:10:22
created_gmt: 2014/05/08 11:10:22
comment_status: closed
post_name: getuploadedrequest
status: publish
post_type: post

<!--Returns a secure, time sensitive URL to a piece of content that was previously uploaded to the GameSparks platform by a player. -->

# GetUploadedRequest

Returns a secure, time sensitive URL to a piece of content that was previously uploaded to the GameSparks platform by a player.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

uploadId:string
No

The system generated id of the uploaded item

#### Errors

NameValueDescription

uploadId
INVALID

The upload id was invalid

  


## Example Request
    
    
    {
      "@class" : ".GetUploadedRequest",
      "uploadId" : "524c13c7e4b0f3abf2b1ddc0"
    }

## Example Response
    
    
    {
      "@class" : ".GetUploadedResponse",
      "scriptData" : { },
      "size" : 100000,
      "url" : "http://gamesparksbinaries.blob.core.windows.net/upload-1234/c8bb7124f05b4a08ab4f4b2772b30d0a-map-data.xml..."
    }