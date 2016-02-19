title: ListInviteFriendsRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/listinvitefriendsrequest
author: gabriel.page
description: 
post_id: 2251
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: listinvitefriendsrequest
status: private
post_type: post

<!--Returns a list of non game friends. -->

# ListInviteFriendsRequest

Returns a list of non game friends.

A non game friend is someone in their social network who does not play the game.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListInviteFriendsRequest",
      "requestId" : "1380550918297"
    }

## Example Response
    
    
    {
      "@class" : ".ListInviteFriendsResponse",
      "friends" : [ {
        "displayName" : "...",
        "id" : "...",
        "profilePic" : "..."
      }, {
        "displayName" : "...",
        "id" : "...",
        "profilePic" : "..."
      }, {
        "displayName" : "...",
        "id" : "...",
        "profilePic" : "..."
      } ],
      "requestId" : "1405688659417",
      "scriptData" : {
        "myKey" : "myKey",
        "myValue" : "123"
      }
    }