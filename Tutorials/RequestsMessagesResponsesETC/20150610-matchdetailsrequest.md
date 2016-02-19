title: MatchDetailsRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/matchdetailsrequest
author: GameSparks
description: 
post_id: 8059
created: 2015/06/10 14:46:42
created_gmt: 2015/06/10 14:46:42
comment_status: closed
post_name: matchdetailsrequest
status: publish
post_type: post

<!--Find the details of an existing match this player belongs to, using the matchId -->

# MatchDetailsRequest

Find the details of an existing match this player belongs to, using the matchId

#### Parameters

Name : TypeRequiredDescription

matchId:string
Yes

The matchId to find the details of

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

setRealtimeEnabled:void
No

Adds realtime server details if the match has been created using Cloud Code and it has not been realtime enabled

#### Errors

NameValueDescription

matchId
NOT_FOUND

No match found with given matchId for this player

  


## Example Request
    
    
    {
      "@class" : ".MatchDetailsRequest",
      "matchId" : "matchId",
      "setRealtimeEnabled" : { }
    }

## Example Response
    
    
    {
      "@class" : ".MatchDetailsResponse",
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