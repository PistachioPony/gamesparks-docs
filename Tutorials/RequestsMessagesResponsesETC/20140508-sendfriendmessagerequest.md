title: SendFriendMessageRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/sendfriendmessagerequest
author: gabriel.page
description: 
post_id: 2255
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: sendfriendmessagerequest
status: publish
post_type: post

<!--Sends a message to one or more game friend(s). A game friend is someone in the players social network who also plays the game. -->

# SendFriendMessageRequest

Sends a message to one or more game friend(s). A game friend is someone in the players social network who also plays the game.

#### Parameters

Name : TypeRequiredDescription

friendIds:string[]
Yes

One or more friend ID's. This can be supplied as a single string, or a JSON array

message:string
Yes

The message to send

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

friendId
NOT_FRIEND

The friend ID passed is not linked to the current player as a game friend

friendId
INVALID

The value passed is not a valid ID

  


## Example Request
    
    
    {
      "@class" : ".SendFriendMessageRequest",
      "friendIds" : [ "524c13c7e4b0f3abf2b1ddc0" ],
      "message" : "Shall we play a game?"
    }

## Example Response
    
    
    {
      "@class" : ".SendFriendMessageResponse",
      "scriptData" : { }
    }