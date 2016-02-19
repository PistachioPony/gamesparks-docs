title: GetMessageRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/getmessagerequest
author: gabriel.page
description: 
post_id: 2248
created: 2014/05/08 11:10:21
created_gmt: 2014/05/08 11:10:21
comment_status: closed
post_name: getmessagerequest
status: publish
post_type: post

<!--Returns the full details of a message. -->

# GetMessageRequest

Returns the full details of a message.

#### Parameters

Name : TypeRequiredDescription

messageId:string
Yes

The messageId of the message retreive

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".GetMessageRequest",
      "messageId" : "524d2e60e4b0f3abf2b23b65"
    }

## Example Response
    
    
    {
      "@class" : ".GetMessageResponse",
      "message" : {
        "@class" : ".AchievementEarnedMessage",
        "messageId" : "524d2e60e4b0f3abf2b23b65",
        "notification" : true,
        "summary" : "AchievementEarnedMessage",
        "achievementName" : "Track 1 Achievement 1",
        "achievementShortCode" : "T1A1"
      },
      "scriptData" : { }
    }