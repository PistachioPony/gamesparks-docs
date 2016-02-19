title: ListMessageSummaryResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/listmessagesummaryresponse
author: GameSparks
description: 
post_id: 4344
created: 2014/08/04 15:33:07
created_gmt: 2014/08/04 15:33:07
comment_status: open
post_name: listmessagesummaryresponse
status: publish
post_type: post

<!--A response containing  a summary of the list of the current players messages / notifications. -->

# ListMessageSummaryResponse

A response containing a summary of the list of the current players messages / notifications.

#### Parameters

Name : TypeDescription

messageList:JSON

A list of JSON objects containing player message summaries

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