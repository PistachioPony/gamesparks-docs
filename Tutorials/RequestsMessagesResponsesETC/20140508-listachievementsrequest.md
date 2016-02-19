title: ListAchievementsRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/listachievementsrequest
author: gabriel.page
description: 
post_id: 2249
created: 2014/05/08 11:10:21
created_gmt: 2014/05/08 11:10:21
comment_status: closed
post_name: listachievementsrequest
status: publish
post_type: post

<!--Retrieves a list of the configured achievements in the game, along with whether the current player has earned the achievement. -->

# ListAchievementsRequest

Retrieves a list of the configured achievements in the game, along with whether the current player has earned the achievement.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListAchievementsRequest"
    }

## Example Response
    
    
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