title: GetMessageResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/getmessageresponse
author: GameSparks
description: 
post_id: 4322
created: 2014/08/04 15:33:47
created_gmt: 2014/08/04 15:33:47
comment_status: open
post_name: getmessageresponse
status: publish
post_type: post

<!--A response containing the message data for a given message -->

# GetMessageResponse

A response containing the message data for a given message

#### Parameters

Name : TypeDescription

message:JSON

The message data

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