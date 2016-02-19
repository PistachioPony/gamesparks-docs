title: TeamChatMessage
link: https://docs.gamesparks.net/documentation/message-api/teams-message-api/teamchatmessage
author: GameSparks
description: 
post_id: 5777
created: 2015/01/14 12:23:49
created_gmt: 2015/01/14 12:23:49
comment_status: open
post_name: teamchatmessage
status: publish
post_type: post

<!--A message sent from a player to an entire team. -->

# TeamChatMessage

A message sent from a player to an entire team.

## Fields

Name : TypeDescription

@class:String
.TeamChatMessage

chatMessageId:string

The identifier for this message as it appears in the chat history.

fromId:string

The player's id who is sending the message.

message:string

The message to send to the team.

messageId:string

A unique identifier for this message.

notification:boolean

Flag indicating whether this message could be sent as a push notification or not.

ownerId:string

The id of the owner

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

teamId:string

The id of the team

teamType:string

The team type

title:string

A textual title for the message.

who:string

The name of the player who is sending the message.

  


## Example Message
    
    
    {
      "@class" : ".TeamChatMessage",
      "chatMessageId" : "528b3301e4b09c9ee84978eb",
      "fromId" : "528b3301e4b09c9ee84978eb",
      "message" : "Hi, have you seen that new game called Time Pilot 84?",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "ownerId" : "...",
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "teamId" : "...",
      "teamType" : "...",
      "title" : "A message title",
      "who" : "Player One"
    }