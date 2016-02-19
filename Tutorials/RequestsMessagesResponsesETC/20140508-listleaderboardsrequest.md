title: ListLeaderboardsRequest
link: https://docs.gamesparks.net/documentation/request-api/leaderboards-request-api/listleaderboardsrequest
author: gabriel.page
description: 
post_id: 2238
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: listleaderboardsrequest
status: publish
post_type: post

<!--Returns a list of all leaderboards configured in the game. -->

# ListLeaderboardsRequest

Returns a list of all leaderboards configured in the game.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListLeaderboardsRequest"
    }

## Example Response
    
    
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