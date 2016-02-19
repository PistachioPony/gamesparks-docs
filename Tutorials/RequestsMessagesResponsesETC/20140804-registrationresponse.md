title: RegistrationResponse
link: https://docs.gamesparks.net/documentation/response-api/authentication-response-api/registrationresponse
author: GameSparks
description: 
post_id: 4315
created: 2014/08/04 15:35:12
created_gmt: 2014/08/04 15:35:12
comment_status: open
post_name: registrationresponse
status: publish
post_type: post

<!--A response to a registration request  -->

# RegistrationResponse

A response to a registration request 

#### Parameters

Name : TypeDescription

authToken:string

44b297a8-162a-4220-8c14-dad9a1946ad2

displayName:string

The player's display name

newPlayer:boolean

Indicates whether the player was created as part of this request

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

switchSummary:Player

A summary of the player that would be switched to. Only returned as part of an error response for a request where automatic switching is disabled.

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

userId:string

The player's id

  


## Example
    
    
    {
      "@class" : ".RegistrationResponse",
      "authToken" : "524c13c7e4b0f3abf2b1ddc0",
      "displayName" : "Nick",
      "newPlayer" : false,
      "scriptData" : { },
      "switchSummary" : {
        "achievements" : [ "..." ],
        "displayName" : "...",
        "externalIds" : "...",
        "id" : "...",
        "online" : false,
        "scriptData" : { },
        "virtualGoods" : [ "..." ]
      },
      "userId" : "523b0628e4b0aba320077410"
    }