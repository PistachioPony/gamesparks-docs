title: ListTeamChatRequest
link: https://docs.gamesparks.net/documentation/request-api/teams-request-api/listteamchatrequest
author: GameSparks
description: 
post_id: 5790
created: 2015/01/14 12:23:48
created_gmt: 2015/01/14 12:23:48
comment_status: open
post_name: listteamchatrequest
status: publish
post_type: post

<!--Get a list of the messages sent to the team (by players using SendTeamChatMessageRequest). -->

# ListTeamChatRequest

Get a list of the messages sent to the team (by players using SendTeamChatMessageRequest).

#### Parameters

Name : TypeRequiredDescription

entryCount:number
No

The number of messages to return (default=50)

offset:number
No

The offset (nth message) to start from (default=0)

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


## Example Request
    
    
    {
      "@class" : ".ListTeamChatRequest",
      "entryCount" : 20,
      "offset" : 50,
      "ownerId" : "12345",
      "teamId" : "12345",
      "teamType" : "SQUAD"
    }

## Example Response
    
    
    {
      "@class" : ".ListTeamChatResponse",
      "scriptData" : { }
    }