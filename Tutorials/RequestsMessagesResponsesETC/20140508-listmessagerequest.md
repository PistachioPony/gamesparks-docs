title: ListMessageRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/listmessagerequest
author: gabriel.page
description: 
post_id: 2252
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: listmessagerequest
status: publish
post_type: post

<!--Returns the list of the current players messages / notifications. -->

# ListMessageRequest

Returns the list of the current players messages / notifications.

The list only contains un-dismissed messages, to dismiss a message see DismissMessageRequest Read the section on Messages to the the complete list of messages and their meaning.

#### Parameters

Name : TypeRequiredDescription

entryCount:number
No

The number of items to return in a page (default=50)

include:string
No

An optional filter that limits the message types returned

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
      "@class" : ".ListMessageRequest",
      "entryCount" : 20,
      "include" : "UNSEEN",
      "offset" : 5
    }

## Example Response
    
    
    {
      "@class" : ".ListMessageResponse",
      "messageList" : [ [ {
        "@class" : ".NewHighScoreMessage",
        "messageId" : "524d2e60e4b0f3abf2b23b64",
        "notification" : true,
        "summary" : "NewHighScoreMessage",
        "leaderboardData" : {
          "HS" : 10000,
          "GL" : "TRACK1",
          "userId" : "524d2c02e4b0f3abf2b23a72",
          "city" : "York",
          "country" : "GB",
          "userName" : "Harry Amehhaficgih Adeagbosen"
        },
        "leaderboardShortCode" : "TRACK1"
      }, {
        "@class" : ".AchievementEarnedMessage",
        "messageId" : "524d2e60e4b0f3abf2b23b65",
        "notification" : true,
        "summary" : "AchievementEarnedMessage",
        "achievementName" : "Track 1 Achievement 1",
        "achievementShortCode" : "T1A1"
      } ] ],
      "scriptData" : { }
    }