title: MatchUpdatedMessage
link: https://docs.gamesparks.net/documentation/message-api/multiplayer-message-api/matchupdatedmessage
author: GameSparks
description: 
post_id: 9631
created: 2015/11/16 14:30:42
created_gmt: 2015/11/16 14:30:42
comment_status: closed
post_name: matchupdatedmessage
status: publish
post_type: post

<!--A message indicating that there has been an update to a pending match request, but it is not yet complete -->

# MatchUpdatedMessage

A message indicating that there has been an update to a pending match request, but it is not yet complete

## Fields

Name : TypeDescription

@class:String
.MatchUpdatedMessage

matchGroup:string

The group the player was assigned in the matchmaking request

matchShortCode:string

The shortCode of the match type this message for

messageId:string

A unique identifier for this message.

notification:boolean

Flag indicating whether this message could be sent as a push notification or not.

participants:Participant

The participants in this match

### Participant

A nested object that represents a participant in a match.

Name:TypeDescription

achievements:string
The achievements of the Player

displayName:string
The display name of the Player

externalIds:JSON
The external Id's of the Player

id:string
The id of the Player

online:boolean
The online status of the Player

peerId:number
The peerId of this participant within the match

scriptData:JSON
The script data of the Player

virtualGoods:string
The virtual goods of the Player

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
      "@class" : ".MatchUpdatedMessage",
      "matchGroup" : "group1",
      "matchShortCode" : "match1",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "participants" : [ {
        "achievements" : [ "..." ],
        "displayName" : "...",
        "externalIds" : "...",
        "id" : "...",
        "online" : false,
        "peerId" : 1,
        "scriptData" : { },
        "virtualGoods" : [ "..." ]
      } ],
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "title" : "A message title"
    }