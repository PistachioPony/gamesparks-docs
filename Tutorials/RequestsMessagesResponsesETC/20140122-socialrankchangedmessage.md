title: SocialRankChangedMessage
link: https://docs.gamesparks.net/documentation/message-api/leaderboards-message-api/socialrankchangedmessage
author: gabriel.page
description: 
post_id: 1535
created: 2014/01/22 15:48:17
created_gmt: 2014/01/22 15:48:17
comment_status: closed
post_name: socialrankchangedmessage
status: publish
post_type: post

<!--This message is sent to players when their rank in a leaderboard changes with respect to the rank of their social network friends. -->

# SocialRankChangedMessage

This message is sent to players when their rank in a leaderboard changes with respect to the rank of their social network friends.

## Fields

Name : TypeDescription

@class:String
.SocialRankChangedMessage

gameId:number

The game id that this message relates to.

leaderboardName:string

The leaderboard's name.

leaderboardShortCode:string

The leaderboard shortcode.

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

them:LeaderboardData

The score details of the player whose score the receiving player has passed.

### LeaderboardData

Leaderboard entry data

As well as the parameters below there may be others depending on your game's configuration.

Name:TypeDescription

city:string
The city where the player was located when they logged this leaderboard entry.

country:string
The country code where the player was located when they logged this leaderboard entry.

externalIds:JSON
The players rank.

id:string
The unique leaderboard id.

rank:number
The players rank.

userId:string
The unique player id for this leaderboard entry.

userName:string
The players display name.

when:string
The date when this leaderboard entry was created.

title:string

A textual title for the message.

you:LeaderboardData

The score details of the receiving player.

### LeaderboardData

Leaderboard entry data

As well as the parameters below there may be others depending on your game's configuration.

Name:TypeDescription

city:string
The city where the player was located when they logged this leaderboard entry.

country:string
The country code where the player was located when they logged this leaderboard entry.

externalIds:JSON
The players rank.

id:string
The unique leaderboard id.

rank:number
The players rank.

userId:string
The unique player id for this leaderboard entry.

userName:string
The players display name.

when:string
The date when this leaderboard entry was created.
  


## Example Message
    
    
    {
      "@class" : ".SocialRankChangedMessage",
      "gameId" : 10106,
      "leaderboardName" : "Leaderboard One",
      "leaderboardShortCode" : "LB1",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "them" : {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      },
      "title" : "A message title",
      "you" : {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      }
    }