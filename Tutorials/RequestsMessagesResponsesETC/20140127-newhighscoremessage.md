title: NewHighScoreMessage
link: https://docs.gamesparks.net/documentation/message-api/leaderboards-message-api/newhighscoremessage
author: gabriel.page
description: 
post_id: 1591
created: 2014/01/27 11:15:03
created_gmt: 2014/01/27 11:15:03
comment_status: closed
post_name: newhighscoremessage
status: publish
post_type: post

<!--A message indicating that the player has achieved a new high score in the game. -->

# NewHighScoreMessage

A message indicating that the player has achieved a new high score in the game.

## Fields

Name : TypeDescription

@class:String
.NewHighScoreMessage

leaderboardData:LeaderboardData

The new leaderboard data associated with this message.

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

leaderboardName:string

The leaderboard's name.

leaderboardShortCode:string

The leaderboard shortcode.

messageId:string

A unique identifier for this message.

notification:boolean

Flag indicating whether this message could be sent as a push notification or not.

rankDetails:LeaderboardRankDetails

The ranking information for the new score.

### LeaderboardRankDetails

Ranking information.

Name:TypeDescription

friendsPassed:LeaderboardData
The leaderboard entries of the players friends that were beaten as part of this score submission.

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

globalCount:number
The number of entries in this leaderboard.

globalFrom:number
The Global Rank of the player in this leaderboard before the score was submitted.

globalFromPercent:number
The old global rank of the player as a percentage of the total number of scores in this leaderboard .

globalTo:number
The Global Rank of the player in this leaderboard after the score was submitted.

globalToPercent:number
The new global rank of the player as a percentage of the total number of scores in this leaderboard .

socialCount:number
The number of friend entries the player has in this leaderboard.

socialFrom:number
The Social Rank of the player in this leaderboard before the score was submitted.

socialFromPercent:number
The old social rank of the player as a percentage of the total number of friend scores in this leaderboard.

socialTo:number
The Social Rank of the player in this leaderboard after the score was submitted.

socialToPercent:number
The old global rank of the player as a percentage of the total number of friend scores in this leaderboard.

topNPassed:LeaderboardData
The leaderboard entries of the global players that were beaten as part of this score submission. Requires Top N to be configured on the leaderboard

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