title: ListLeaderboardsResponse
link: https://docs.gamesparks.net/documentation/response-api/leaderboards-response-api/listleaderboardsresponse
author: GameSparks
description: 
post_id: 4330
created: 2014/08/04 15:33:45
created_gmt: 2014/08/04 15:33:45
comment_status: open
post_name: listleaderboardsresponse
status: publish
post_type: post

<!--A response containing a list of all leaderboards configured in the game. -->

# ListLeaderboardsResponse

A response containing a list of all leaderboards configured in the game.

#### Parameters

Name : TypeDescription

leaderboards:Leaderboard

A list of JSON object containing leaderboard meta data

### Leaderboard

A nested object that represents the leaderboard configuration data.

Name:TypeDescription

description:string
The leaderboard's description.

name:string
The leaderboard's name.

propertySet:JSON
The custom property set configured on this Leaderboard

shortCode:string
The leaderboard's short code.

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
      "@class" : ".ListLeaderboardsResponse",
      "leaderboards" : [ {
        "description" : "Fastest laps in 50cc class",
        "name" : "High Scores",
        "propertySet" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
        "shortCode" : "LB1"
      } ],
      "scriptData" : { }
    }