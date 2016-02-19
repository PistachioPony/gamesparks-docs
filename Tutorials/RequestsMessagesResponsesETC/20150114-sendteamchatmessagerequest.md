title: SendTeamChatMessageRequest
link: https://docs.gamesparks.net/documentation/request-api/teams-request-api/sendteamchatmessagerequest
author: GameSparks
description: 
post_id: 5791
created: 2015/01/14 12:23:48
created_gmt: 2015/01/14 12:23:48
comment_status: open
post_name: sendteamchatmessagerequest
status: publish
post_type: post

<!--Send a message to all the players who are member of the given team -->

# SendTeamChatMessageRequest

Send a message to all the players who are member of the given team

#### Parameters

Name : TypeRequiredDescription

message:string
No

The message to send

ownerId:string
No

The team owner to find, used in combination with teamType. If not supplied the current players id will be used

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

teamId:string
No

The teamId to find (may be null if teamType supplied)

teamType:string
No

The teamType to find, used in combination with the current player, or the player defined by ownerId

#### Errors

NameValueDescription

team
INVALID

No team exists for the given details

team
NOT_A_MEMBER

The current player is not a member of the team they are trying to message

  


## Example Request
    
    
    {
      "@class" : ".SendTeamChatMessageRequest",
      "message" : "Let's storm the castle!",
      "ownerId" : "12345",
      "teamId" : "12345",
      "teamType" : "SQUAD"
    }

## Example Response
    
    
    {
      "@class" : ".SendTeamChatMessageResponse",
      "scriptData" : { }
    }