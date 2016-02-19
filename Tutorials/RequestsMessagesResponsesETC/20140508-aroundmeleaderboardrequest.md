title: AroundMeLeaderboardRequest
link: https://docs.gamesparks.net/documentation/request-api/leaderboards-request-api/aroundmeleaderboardrequest
author: gabriel.page
description: 
post_id: 2236
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: aroundmeleaderboardrequest
status: publish
post_type: post

<!--Returns leaderboard data that is adjacent to the currently signed in player's position within the given leaderboard. -->

# AroundMeLeaderboardRequest

Returns leaderboard data that is adjacent to the currently signed in player's position within the given leaderboard.

#### Parameters

Name : TypeRequiredDescription

challengeInstanceId:string
No

The challenge instance to get the leaderboard data for

customIdFilter:JSON
No

An optional filter on the customIds.

dontErrorOnNotSocial:boolean
No

The default behaviour on a social request is to error if the player has no friends (NOTSOCIAL). Set this flag to suppress that error and return the player's leaderboard entry instead.

entryCount:number
Yes

The number of items to return in a page (default=50)

friendIds:string[]
No

A friend id or an array of friend ids to use instead of the player's social friends

includeFirst:number
No

Number of entries to include from head of the list

includeLast:number
No

Number of entries to include from tail of the list

inverseSocial:boolean
No

Returns the leaderboard excluding the player's social friends

leaderboardShortCode:string
No

The short code of the leaderboard

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

social:boolean
No

If True returns a leaderboard of the player's social friends

teamIds:string[]
No

The IDs of the teams you are interested in

teamTypes:string[]
No

The type of team you are interested in

#### Errors

NameValueDescription

leaderboardShortCode|challengeInstanceId
ONLY_ONE

Both shortCode and challengeInstanceId were supplied, only one should be supplied

leaderboardShortCode|challengeInstanceId
REQUIRED

Both shortCode and challengeInstanceId were missing

leaderboardShortCode
INVALID

The shortCode does not match a configured leaderboard

challengeInstanceId
NO_LEADERBOARD

The challengeInstanceId maps to a challenge without a leaderboard configured

challengeInstanceId
INVALID

The challengeInstanceId supplied did not match a challenge related to the current play

challengeInstanceVersion
INVALID

The challengeInstance predates support for this request type

  


## Example Request
    
    
    {
      "@class" : ".AroundMeLeaderboardRequest",
      "challengeInstanceId" : "523b0628e4b0aba320077410",
      "customIdFilter" : {
        "carType" : "bigCar"
      },
      "dontErrorOnNotSocial" : false,
      "entryCount" : 100,
      "friendIds" : [ "524c13c7e4b0f3abf2b1ddc0" ],
      "includeFirst" : 10,
      "includeLast" : 10,
      "inverseSocial" : true,
      "leaderboardShortCode" : "HIGHSCORE",
      "social" : true,
      "teamIds" : [ "["123", "345"]" ],
      "teamTypes" : [ "["SQUAD", "FRIENDS"]" ]
    }

## Example Response
    
    
    {
      "@class" : ".AroundMeLeaderboardResponse",
      "challengeInstanceId" : "523b0628e4b0aba320077410",
      "data" : [ {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      } ],
      "first" : [ {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      } ],
      "last" : [ {
        "city" : "York",
        "country" : "GB",
        "externalIds" : "12",
        "id" : "52933b2fe4b0cb288bca09a3",
        "rank" : 12,
        "userId" : "52933b2fe4b0cb288bca09a3",
        "userName" : "Player One",
        "when" : "2013-11-25T13:01Z"
      } ],
      "leaderboardShortCode" : "WHSLB.SCHEDULED.2014-04-30-14-49",
      "scriptData" : { },
      "social" : true
    }