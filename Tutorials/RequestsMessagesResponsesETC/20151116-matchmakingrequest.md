title: MatchmakingRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/matchmakingrequest
author: GameSparks
description: 
post_id: 9637
created: 2015/11/16 14:33:02
created_gmt: 2015/11/16 14:33:02
comment_status: closed
post_name: matchmakingrequest
status: publish
post_type: post

<!--Register this player for matchmaking, using the given skill and matchShortCode. -->

# MatchmakingRequest

Register this player for matchmaking, using the given skill and matchShortCode.

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

  


## Example Request
    
    
    {
      "@class" : ".MatchmakingRequest",
      "action" : "cancel",
      "matchGroup" : "group1",
      "matchShortCode" : "match1",
      "skill" : 25
    }

## Example Response
    
    
    {
      "@class" : ".MatchmakingResponse",
      "scriptData" : { }
    }