title: GetMyTeamsRequest
link: https://docs.gamesparks.net/documentation/request-api/teams-request-api/getmyteamsrequest
author: GameSparks
description: 
post_id: 4451
created: 2014/08/08 08:41:00
created_gmt: 2014/08/08 08:41:00
comment_status: closed
post_name: getmyteamsrequest
status: publish
post_type: post

<!--Get the teams that the player is in. Can be filtered on team type and also on those teams that the player owns. -->

# GetMyTeamsRequest

Get the teams that the player is in. Can be filtered on team type and also on those teams that the player owns.

#### Parameters

Name : TypeRequiredDescription

ownedOnly:boolean
No

Set to true to only get teams owned by the player

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

teamTypes:string[]
No

The type of teams to get

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".GetMyTeamsRequest",
      "ownedOnly" : true,
      "teamTypes" : [ "["SQUADS", "PLATOONS"]" ]
    }

## Example Response
    
    
    {
      "@class" : ".GetMyTeamsResponse",
      "scriptData" : { },
      "teams" : [ {
        "members" : [ {
          "achievements" : [ "..." ],
          "displayName" : "...",
          "externalIds" : "...",
          "id" : "...",
          "online" : false,
          "scriptData" : { },
          "virtualGoods" : [ "..." ]
        } ],
        "owner" : {
          "achievements" : [ "..." ],
          "displayName" : "...",
          "externalIds" : "...",
          "id" : "...",
          "online" : false,
          "scriptData" : { },
          "virtualGoods" : [ "..." ]
        },
        "teamId" : "...",
        "teamType" : "..."
      } ]
    }