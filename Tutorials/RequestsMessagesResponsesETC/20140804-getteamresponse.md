title: GetTeamResponse
link: https://docs.gamesparks.net/documentation/response-api/teams-response-api/getteamresponse
author: GameSparks
description: 
post_id: 4353
created: 2014/08/04 15:33:05
created_gmt: 2014/08/04 15:33:05
comment_status: open
post_name: getteamresponse
status: publish
post_type: post

<!--A response containing the details of the requested teams -->

# GetTeamResponse

A response containing the details of the requested teams

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

teams:Team

A JSON array of teams.

### Team

A nested object that represents the team.

Name:TypeDescription

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

teamId:string
The Id of the team

teamType:string
The team type
  


## Example
    
    
    {
      "@class" : ".GetTeamResponse",
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
      "teamType" : "...",
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