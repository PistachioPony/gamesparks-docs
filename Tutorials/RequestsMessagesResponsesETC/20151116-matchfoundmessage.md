title: MatchFoundMessage
link: https://docs.gamesparks.net/documentation/message-api/multiplayer-message-api/matchfoundmessage
author: GameSparks
description: 
post_id: 9627
created: 2015/11/16 14:28:42
created_gmt: 2015/11/16 14:28:42
comment_status: closed
post_name: matchfoundmessage
status: publish
post_type: post

<!--A message indicating that a match has been found -->

# MatchFoundMessage

A message indicating that a match has been found

## Fields

Name : TypeDescription

@class:String
.MatchFoundMessage

accessToken:string

The accessToken used to authenticate this player for this match

host:string

The host to connect to for this match

matchGroup:string

The group the player was assigned in the matchmaking request

matchId:string

The id for this match instance

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

port:number

The port to connect to for this match

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
      "@class" : ".MatchFoundMessage",
      "accessToken" : "accesstoken",
      "host" : "localhost",
      "matchGroup" : "group1",
      "matchId" : "523b0628e4b0aba320077409",
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
      "port" : 5000,
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "title" : "A message title"
    }