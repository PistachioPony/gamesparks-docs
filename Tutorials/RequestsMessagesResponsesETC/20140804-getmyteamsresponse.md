title: GetMyTeamsResponse
link: https://docs.gamesparks.net/documentation/response-api/teams-response-api/getmyteamsresponse
author: GameSparks
description: 
post_id: 4352
created: 2014/08/04 15:33:07
created_gmt: 2014/08/04 15:33:07
comment_status: open
post_name: getmyteamsresponse
status: publish
post_type: post

<!--A response containing team data for teams that a player belong to -->

# GetMyTeamsResponse

A response containing team data for teams that a player belong to

#### Parameters

Name : TypeDescription

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

teams:Team

The team data

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