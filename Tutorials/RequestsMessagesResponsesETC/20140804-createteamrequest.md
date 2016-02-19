title: CreateTeamRequest
link: https://docs.gamesparks.net/documentation/request-api/teams-request-api/createteamrequest
author: GameSparks
description: 
post_id: 4232
created: 2014/08/04 15:33:04
created_gmt: 2014/08/04 15:33:04
comment_status: open
post_name: createteamrequest
status: publish
post_type: post

<!--Allows a new team to be created. -->

# CreateTeamRequest

Allows a new team to be created.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

teamId:string
No

An optional teamId to use

teamName:string
Yes

A display name to use

teamType:string
Yes

The type of team to be created

#### Errors

NameValueDescription

teamType
INVALID

The team type short code supplied does not exist

teamType
MAX_OWNED_REACHED

The current player has reached the ownership limit of the supplied teamType

teamType
MAX_TEAMS_REACHED

The current player has reached the membership limit of the supplied teamType

teamId
NOT_UNIQUE

The teamId supplied already exists

  


## Example Request
    
    
    {
      "@class" : ".CreateTeamRequest",
      "teamId" : "12345",
      "teamName" : "my team",
      "teamType" : "SQUAD"
    }

## Example Response
    
    
    {
      "@class" : ".CreateTeamResponse",
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
      "scriptData" : { },
      "teamId" : "...",
      "teamType" : "..."
    }