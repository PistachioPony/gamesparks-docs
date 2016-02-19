title: LeaderboardsEntriesResponse
link: https://docs.gamesparks.net/documentation/response-api/leaderboards-response-api/leaderboardsentriesresponse
author: GameSparks
description: 
post_id: 10165
created: 2016/01/14 17:07:19
created_gmt: 2016/01/14 17:07:19
comment_status: open
post_name: leaderboardsentriesresponse
status: publish
post_type: post

<!--A response containing leaderboard entry data for a given player -->

# LeaderboardsEntriesResponse

A response containing leaderboard entry data for a given player

#### Parameters

Name : TypeDescription

requestId:string

The ID of the corresponding Request

results:JSON

The leaderboard entry data

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
      "@class" : ".LeaderboardsEntriesResponse",
      "results" : ""HS": [{"userId":"537f08e1e4b01fdedfa52c49","SCORE": 123,"city":"York","country":"GB","userName":"","when":"2014-07-17T12:18Z","rank": 1  }]",
      "scriptData" : { }
    }