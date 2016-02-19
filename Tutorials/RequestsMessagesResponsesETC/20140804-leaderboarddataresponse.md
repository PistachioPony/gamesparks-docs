title: LeaderboardDataResponse
link: https://docs.gamesparks.net/documentation/response-api/leaderboards-response-api/leaderboarddataresponse
author: GameSparks
description: 
post_id: 4329
created: 2014/08/04 15:33:45
created_gmt: 2014/08/04 15:33:45
comment_status: open
post_name: leaderboarddataresponse
status: publish
post_type: post

<!--A response containing leaderboard data -->

# LeaderboardDataResponse

A response containing leaderboard data

#### Parameters

Name : TypeDescription

challengeInstanceId:string

The leaderboard's challenge id

data:LeaderboardData

The leaderboard data

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

first:LeaderboardData

The first item in the leaderboard data

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

last:LeaderboardData

The last item in the leaderboard data

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

leaderboardShortCode:string

The leaderboard short code

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
      "@class" : ".LeaderboardDataResponse",
      "challengeInstanceId" : "523b0628e4b0aba320077410",
      "data" : [ {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      } ],
      "first" : [ {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      } ],
      "last" : [ {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      } ],
      "leaderboardShortCode" : "TRACK1",
      "scriptData" : { }
    }