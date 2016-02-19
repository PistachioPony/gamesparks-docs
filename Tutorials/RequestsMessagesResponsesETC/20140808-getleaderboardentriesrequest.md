title: GetLeaderboardEntriesRequest
link: https://docs.gamesparks.net/documentation/request-api/leaderboards-request-api/getleaderboardentriesrequest
author: GameSparks
description: 
post_id: 4443
created: 2014/08/08 08:41:04
created_gmt: 2014/08/08 08:41:04
comment_status: closed
post_name: getleaderboardentriesrequest
status: publish
post_type: post

<!--Get the leaderboard entry data for the current player or a given player.  -->

# GetLeaderboardEntriesRequest

Get the leaderboard entry data for the current player or a given player. 

For each leaderboard it returns the hichest score the player has

#### Parameters

Name : TypeRequiredDescription

challenges:string[]
No

The challenge leaderboards to return entries for

inverseSocial:boolean
No

Returns the leaderboard excluding the player's social friends

leaderboards:string[]
No

The list of leaderboards shortcodes

player:string
No

The player id. Leave out to use the current player id

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

social:boolean
No

Set to true to include the player's game friends

teamTypes:string[]
No

The types of team to apply this request to

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".GetLeaderboardEntriesRequest",
      "challenges" : [ "["527f08e1e4b01fdedfa52d41"]" ],
      "inverseSocial" : true,
      "leaderboards" : [ "["HIGH_SCORES", "LAP_TIMES"]" ],
      "player" : "537f08e1e4b01fdedfa52c49",
      "social" : true,
      "teamTypes" : [ "["SQUAD"]" ]
    }

## Example Response
    
    
    {
      "@class" : ".GetLeaderboardEntriesResponse",
      "results" : ""HS": {"userId":"537f08e1e4b01fdedfa52c49","SCORE": 123,"city":"York","country":"GB","userName":"","when":"2014-07-17T12:18Z","rank": 1  }",
      "scriptData" : { }
    }