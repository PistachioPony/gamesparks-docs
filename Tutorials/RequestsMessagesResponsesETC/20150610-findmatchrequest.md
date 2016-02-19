title: FindMatchRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/findmatchrequest
author: GameSparks
description: 
post_id: 8057
created: 2015/06/10 14:46:44
created_gmt: 2015/06/10 14:46:44
comment_status: closed
post_name: findmatchrequest
status: publish
post_type: post

<!--Find a match for this player, using the given skill and matchShortCode. -->

# FindMatchRequest

Find a match for this player, using the given skill and matchShortCode.

Players looking for a match using the same matchShortCode will be considered for a match, based on the matchConfig.

Each player must match the other for the match to be found.

#### Parameters

Name : TypeRequiredDescription

action:string
No

The action to take on the already in-flight request for this match. Currently supported actions are: 'cancel'

matchGroup:string
No

Optional. Players will be grouped based on the distinct value passed in here, only players in the same group can be matched together

matchShortCode:string
Yes

The shortCode of the match type this player is registering for

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

skill:number
No

The skill of the player looking for a match

#### Errors

NameValueDescription

skill
may not be null

skill must be provided

matchShortCode
may not be null

matchShortCode must be provided

matchShortCode
NOT_FOUND

No matchConfig was found with the given matchShortCode

match
NOT_FOUND

No match was found for the current player

match
HEAD_TO_HEAD_ONLY

To match multiple opponents please use MatchmakingRequest

  


## Example Request
    
    
    {
      "@class" : ".FindMatchRequest",
      "action" : "cancel",
      "matchGroup" : "group1",
      "matchShortCode" : "match1",
      "skill" : 25
    }

## Example Response
    
    
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