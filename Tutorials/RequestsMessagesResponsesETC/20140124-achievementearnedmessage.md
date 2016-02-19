title: AchievementEarnedMessage
link: https://docs.gamesparks.net/documentation/message-api/player-message-api/achievementearnedmessage
author: gabriel.page
description: 
post_id: 1533
created: 2014/01/24 13:55:30
created_gmt: 2014/01/24 13:55:30
comment_status: closed
post_name: achievementearnedmessage
status: publish
post_type: post

<!--Message sent to a player when they have been awarded an achievement within the game. -->

# AchievementEarnedMessage

Message sent to a player when they have been awarded an achievement within the game.

This message may be triggered by a leaderboard or a script.

The player may have gained a virtual good or virtual currency as a result of gaining the award.

## Fields

Name : TypeDescription

@class:String
.AchievementEarnedMessage

achievementName:string

The name of achievement.

achievementShortCode:string

The short code of the achievement.

currency1Earned:string

The amount of type 1 currency earned.

currency2Earned:string

The amount of type 2 currency earned.

currency3Earned:string

The amount of type 2 currency earned.

currency4Earned:string

The amount of type 4 currency earned.

currency5Earned:string

The amount of type 5 currency earned.

currency6Earned:string

The amount of type 6 currency earned.

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

virtualGoodEarned:string

The name of the virtual good that was earned.

  


## Example Message
    
    
    {
      "@class" : ".AchievementEarnedMessage",
      "achievementName" : "Cleared level 1",
      "achievementShortCode" : "ACH1",
      "currency1Earned" : "92",
      "currency2Earned" : "26",
      "currency3Earned" : "15",
      "currency4Earned" : "44",
      "currency5Earned" : "55",
      "currency6Earned" : "66",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "title" : "A message title",
      "virtualGoodEarned" : "Boomerang"
    }