title: GetUploadUrlRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/getuploadurlrequest
author: gabriel.page
description: 
post_id: 2242
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: getuploadurlrequest
status: publish
post_type: post

<!--Returns a secure, time sensitive URL to allow the game to upload a piece of player content to the GameSparks platform. -->

# GetUploadUrlRequest

Returns a secure, time sensitive URL to allow the game to upload a piece of player content to the GameSparks platform.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

uploadData:JSON
No

Optional meta data which is stored against the player's uploaded content

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".GetUploadUrlRequest",
      "uploadData" : [ {
        "type" : "IMAGE"
      } ]
    }

## Example Response
    
    
    {
      "@class" : ".GetUploadUrlResponse",
      "scriptData" : { },
      "url" : "https://gsbeta-service1.gamesparks.net/upload/..."
    }