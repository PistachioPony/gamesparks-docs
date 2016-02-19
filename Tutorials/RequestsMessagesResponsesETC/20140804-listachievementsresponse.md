title: ListAchievementsResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/listachievementsresponse
author: GameSparks
description: 
post_id: 4340
created: 2014/08/04 15:33:42
created_gmt: 2014/08/04 15:33:42
comment_status: open
post_name: listachievementsresponse
status: publish
post_type: post

<!--A reponse containing the game's achievments and an indication of whether the player has earned it -->

# ListAchievementsResponse

A reponse containing the game's achievments and an indication of whether the player has earned it

#### Parameters

Name : TypeDescription

achievements:Achievement

A list of JSON achievment objects

### Achievement

A nested object that represents the achievement data.

Name:TypeDescription

description:string
The desciption of the Achievement

earned:boolean
Whether to current player has earned the achievement

name:string
The name of the Achievement

propertySet:JSON
The custom property set configured on this Achievement

shortCode:string
The shortCode of the Achievement

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
      "@class" : ".ListAchievementsResponse",
      "achievements" : [ {
        "description" : "...",
        "earned" : false,
        "name" : "...",
        "propertySet" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
        "shortCode" : "..."
      } ],
      "scriptData" : { }
    }