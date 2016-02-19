title: ListInviteFriendsResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/listinvitefriendsresponse
author: GameSparks
description: 
post_id: 4342
created: 2014/08/04 15:33:08
created_gmt: 2014/08/04 15:33:08
comment_status: closed
post_name: listinvitefriendsresponse
status: private
post_type: post

<!--A response containing a list of non game friends. -->

# ListInviteFriendsResponse

A response containing a list of non game friends.

#### Parameters

Name : TypeDescription

friends:InvitableFriend

A list of JSON objects containing gME friend data

### InvitableFriend

A nested object that represents the invitable friend.

Name:TypeDescription

displayName:string
The display name of the External Friend

id:string
The ID of the External Friend

profilePic:string
The profile picture URL of the External Friend

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
      "@class" : ".ListInviteFriendsResponse",
      "friends" : [ {
        "displayName" : "...",
        "id" : "...",
        "profilePic" : "..."
      } ],
      "scriptData" : { }
    }