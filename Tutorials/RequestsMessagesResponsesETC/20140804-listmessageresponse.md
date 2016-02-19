title: ListMessageResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/listmessageresponse
author: GameSparks
description: 
post_id: 4343
created: 2014/08/04 15:33:08
created_gmt: 2014/08/04 15:33:08
comment_status: open
post_name: listmessageresponse
status: publish
post_type: post

<!--A response containing the list of the current players messages / notifications. -->

# ListMessageResponse

A response containing the list of the current players messages / notifications.

#### Parameters

Name : TypeDescription

messageList:JSON

A list of JSON objects containing player messages

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