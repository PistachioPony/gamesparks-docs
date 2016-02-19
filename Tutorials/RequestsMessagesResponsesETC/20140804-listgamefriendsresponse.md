title: ListGameFriendsResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/listgamefriendsresponse
author: GameSparks
description: 
post_id: 4341
created: 2014/08/04 15:33:42
created_gmt: 2014/08/04 15:33:42
comment_status: open
post_name: listgamefriendsresponse
status: publish
post_type: post

<!--A response containing the list of the current players game friends. -->

# ListGameFriendsResponse

A response containing the list of the current players game friends.

#### Parameters

Name : TypeDescription

friends:Player

A list of JSON objects containing game friend data

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
  


## Example
    
    
    {
      "@class" : ".ListGameFriendsResponse",
      "friends" : [ {
        "achievements" : [ "..." ],
        "displayName" : "...",
        "externalIds" : "...",
        "id" : "...",
        "online" : false,
        "scriptData" : { },
        "virtualGoods" : [ "..." ]
      } ],
      "scriptData" : { }
    }