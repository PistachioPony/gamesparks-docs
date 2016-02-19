title: ListMessageSummaryRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/listmessagesummaryrequest
author: gabriel.page
description: 
post_id: 2253
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: listmessagesummaryrequest
status: publish
post_type: post

<!--Returns a summary of the list of the current players messages / notifications. -->

# ListMessageSummaryRequest

Returns a summary of the list of the current players messages / notifications.

The list only contains un-dismissed messages, to dismiss a message see DismissMessageRequest.

The full message can be retrieved using GetMessageRequest Read the section on Messages to see the complete list of messages and their meanings.

#### Parameters

Name : TypeRequiredDescription

entryCount:number
No

The number of items to return in a page (default=50)

offset:number
No

The offset (page number) to start from (default=0)

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListMessageSummaryRequest",
      "entryCount" : 200,
      "offset" : 5
    }

## Example Response
    
    
    {
      "@class" : ".ListMessageSummaryResponse",
      "messageList" : [ [ {
        "@class" : ".NewHighScoreMessage",
        "messageId" : "524d2e60e4b0f3abf2b23b64",
        "summary" : "Hey Gabriel, you've got a new high score"
      }, {
        "@class" : ".AchievementEarnedMessage",
        "messageId" : "524d2e60e4b0f3abf2b23b65",
        "summary" : "AchievementEarnedMessage"
      } ] ],
      "scriptData" : { }
    }