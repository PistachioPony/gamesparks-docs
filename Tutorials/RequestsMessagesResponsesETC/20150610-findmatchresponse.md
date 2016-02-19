title: FindMatchResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/findmatchresponse
author: GameSparks
description: 
post_id: 8073
created: 2015/06/10 14:46:14
created_gmt: 2015/06/10 14:46:14
comment_status: closed
post_name: findmatchresponse
status: publish
post_type: post

<!--A response to a find match request -->

# FindMatchResponse

A response to a find match request

#### Parameters

Name : TypeDescription

accessToken:string

The accessToken used to authenticate this player for this match

host:string

The host to connect to for this match

matchId:string

The id for this match instance

opponents:Player

The opponents this player has been matched against

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

peerId:number

The peerId of this player within the match

playerId:string

The id of the current player

port:number

The port to connect to for this match

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
      "@class" : ".FindMatchResponse",
      "accessToken" : "accesstoken",
      "host" : "localhost",
      "matchId" : "523b0628e4b0aba320077409",
      "opponents" : [ {
        "achievements" : [ "..." ],
        "displayName" : "...",
        "externalIds" : "...",
        "id" : "...",
        "online" : false,
        "scriptData" : { },
        "virtualGoods" : [ "..." ]
      } ],
      "peerId" : 1,
      "playerId" : "523b0628e4b0aba320077410",
      "port" : 5000,
      "scriptData" : { }
    }