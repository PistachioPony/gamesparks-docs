title: ListGameFriendsRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/listgamefriendsrequest
author: gabriel.page
description: 
post_id: 2250
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: listgamefriendsrequest
status: publish
post_type: post

<!--Returns the list of the current players game friends. -->

# ListGameFriendsRequest

Returns the list of the current players game friends.

A Game friend is someone in their social network who also plays the game.

Against each friend, and indicator is supplied to show whether the friend is currently connected to the GameSparks service

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListGameFriendsRequest"
    }

## Example Response
    
    
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