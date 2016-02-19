title: FriendMessage
link: https://docs.gamesparks.net/documentation/message-api/player-message-api/friendmessage
author: gabriel.page
description: 
post_id: 1534
created: 2014/01/27 11:14:19
created_gmt: 2014/01/27 11:14:19
comment_status: closed
post_name: friendmessage
status: publish
post_type: post

<!--A message sent from a player to one of his social network friends. -->

# FriendMessage

A message sent from a player to one of his social network friends.

## Fields

Name : TypeDescription

@class:String
.FriendMessage

fromId:string

The player's id who is sending the message.

message:string

The player's message.

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

who:string

The name of the player who is sending the message.

  


## Example Message
    
    
    {
      "@class" : ".FriendMessage",
      "fromId" : "528b3301e4b09c9ee84978eb",
      "message" : "Hi, have you seen that new game called Time Pilot 84?",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "title" : "A message title",
      "who" : "Player One"
    }