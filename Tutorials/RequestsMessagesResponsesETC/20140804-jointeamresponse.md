title: JoinTeamResponse
link: https://docs.gamesparks.net/documentation/response-api/teams-response-api/jointeamresponse
author: GameSparks
description: 
post_id: 4354
created: 2014/08/04 15:33:06
created_gmt: 2014/08/04 15:33:06
comment_status: open
post_name: jointeamresponse
status: publish
post_type: post

<!--A response to a player joining a team or a request for team data -->

# JoinTeamResponse

A response to a player joining a team or a request for team data

#### Parameters

Name : TypeDescription

members:Player

The team members

### Player

A nested object that represents a player.

Name:TypeDescription

achievements:string
The achievements of the Player

displayName:string
The display name of the Player

externalIds:JSON
The external Id's of the Player

id:string
The id of the Player

online:boolean
The online status of the Player

scriptData:JSON
The script data of the Player

virtualGoods:string
The virtual goods of the Player

owner:Player

A summary of the owner

### Player

A nested object that represents a player.

Name:TypeDescription

achievements:string
The achievements of the Player

displayName:string
The display name of the Player

externalIds:JSON
The external Id's of the Player

id:string
The id of the Player

online:boolean
The online status of the Player

scriptData:JSON
The script data of the Player

virtualGoods:string
The virtual goods of the Player

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

teamId:string

The Id of the team

teamType:string

The team type

  


## Example
    
    
    {
      "@class" : ".JoinTeamResponse",
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