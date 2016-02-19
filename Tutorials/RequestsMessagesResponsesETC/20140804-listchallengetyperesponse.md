title: ListChallengeTypeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/listchallengetyperesponse
author: GameSparks
description: 
post_id: 4325
created: 2014/08/04 15:33:46
created_gmt: 2014/08/04 15:33:46
comment_status: open
post_name: listchallengetyperesponse
status: publish
post_type: post

<!--A response containing the list of configured challenge types in the game -->

# ListChallengeTypeResponse

A response containing the list of configured challenge types in the game

#### Parameters

Name : TypeDescription

challengeTemplates:ChallengeType

A list of JSON objects containing the challenge templates for the game

### ChallengeType

Name:TypeDescription

challengeShortCode:string
The shortCode for this challenge.

description:string
The description of this challenge.

getleaderboardName:string
The name of the leaderboard for this challenge.

name:string
The name of this challenge.

tags:string
The tags for this challenge.

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
      "@class" : ".ListChallengeTypeResponse",
      "challengeTemplates" : [ {
        "challengeShortCode" : "...",
        "description" : "...",
        "getleaderboardName" : "...",
        "name" : "...",
        "tags" : "..."
      } ],
      "scriptData" : { }
    }