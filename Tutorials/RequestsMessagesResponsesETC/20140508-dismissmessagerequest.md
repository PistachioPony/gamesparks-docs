title: DismissMessageRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/dismissmessagerequest
author: gabriel.page
description: 
post_id: 2247
created: 2014/05/08 11:10:21
created_gmt: 2014/05/08 11:10:21
comment_status: closed
post_name: dismissmessagerequest
status: publish
post_type: post

<!--Allows a message to be dismissed. Once dismissed the message will no longer appear in either ListMessageResponse or ListMessageSummaryResponse. -->

# DismissMessageRequest

Allows a message to be dismissed. Once dismissed the message will no longer appear in either ListMessageResponse or ListMessageSummaryResponse.

#### Parameters

Name : TypeRequiredDescription

messageId:string
Yes

The messageId of the message to dismiss

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".DismissMessageRequest",
      "messageId" : "524d2e60e4b0f3abf2b23b65"
    }

## Example Response
    
    
    {
      "@class" : ".DismissMessageResponse",
      "scriptData" : { }
    }