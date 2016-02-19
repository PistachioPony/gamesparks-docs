title: ScriptMessage
link: https://docs.gamesparks.net/documentation/message-api/misc-message-api/scriptmessage
author: gabriel.page
description: 
post_id: 1531
created: 2014/01/27 11:14:59
created_gmt: 2014/01/27 11:14:59
comment_status: closed
post_name: scriptmessage
status: publish
post_type: post

<!--A message sent from a Cloud Code script to one or more players. -->

# ScriptMessage

A message sent from a Cloud Code script to one or more players.

See the Spark.sendMessage function in the Cloud Code - Java Script API documentation.

## Fields

Name : TypeDescription

@class:String
.ScriptMessage

data:JSON

JSON data sent from a Cloud Code script.

extCode:string

The extension code used wen creating this script message

messageId:string

A unique identifier for this message.

notification:boolean

Flag indicating whether this message could be sent as a push notification or not.

scriptData:ScriptData

ScriptData is arbitrary data that can be stored in a message by a Cloud Code script.

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Name:TypeDescription

myKey:string
An arbitrary data key

myValue:JSON
An arbitrary data value.

subTitle:string

A textual title for the message.

summary:string

A textual summary describing the message's purpose.

title:string

A textual title for the message.

  


## Example Message
    
    
    {
      "@class" : ".ScriptMessage",
      "data" : "{"alert" : "You've just won a car!"}",
      "extCode" : "...",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "title" : "A message title"
    }