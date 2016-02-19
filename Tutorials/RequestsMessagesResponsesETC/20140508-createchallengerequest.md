title: CreateChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/createchallengerequest
author: gabriel.page
description: 
post_id: 2227
created: 2014/05/08 11:13:56
created_gmt: 2014/05/08 11:13:56
comment_status: closed
post_name: createchallengerequest
status: publish
post_type: post

<!--Issues a challenge to a group of players from the currently signed in player. -->

# CreateChallengeRequest

Issues a challenge to a group of players from the currently signed in player.

The endTime field must be present unless the challenge template has an achievement set in the 'First to Achievement' field.

The usersToChallenge field must be present for this request if the acessType is PRIVATE (which is the default).

#### Parameters

Name : TypeRequiredDescription

accessType:string
No

Who can join this challenge. Either PUBLIC, PRIVATE or FRIENDS

autoStartJoinedChallengeOnMaxPlayers:boolean
No

Whether this challenge should automatically start when a new player joins and maxPlayers is reached

challengeMessage:string
No

An optional message to include with the challenge

challengeShortCode:string
Yes

The short code of the challenge

currency1Wager:number
No

The ammount of currency type 1 that the player is wagering on this challenge

currency2Wager:number
No

The ammount of currency type 2 that the player is wagering on this challenge

currency3Wager:number
No

The ammount of currency type 3 that the player is wagering on this challenge

currency4Wager:number
No

The ammount of currency type 4 that the player is wagering on this challenge

currency5Wager:number
No

The ammount of currency type 5 that the player is wagering on this challenge

currency6Wager:number
No

The ammount of currency type 6 that the player is wagering on this challenge

eligibilityCriteria:JSON
No

Criteria for who can and cannot find and join this challenge (when the accessType is PUBLIC or FRIENDS).

endTime:date
No

The time at which this challenge will end

expiryTime:date
No

The latest time that players can join this challenge

maxAttempts:number
No

The maximum number of attempts 

maxPlayers:number
No

The maximum number of players that are allowed to join this challenge

minPlayers:number
No

The minimum number of players that are allowed to join this challenge

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

silent:boolean
No

If True no messaging is triggered

startTime:date
No

The time at which this challenge will begin

usersToChallenge:string[]
No

A player id or an array of player ids who will recieve this challenge

#### Errors

NameValueDescription

challengeInstanceId
INVALID

The ID does not match a challenge the user is involved with

eligibilityCriteria
{ "XXX" : "UNRECOGNISED"}

XXX is not a valid field of eligibilityCriteria

eligibilityCriteria
{ "segments" : {"XXX" : "MALFORMED"}}

The value provided for XXX is not in the correct format

  


## Example Request
    
    
    {
      "@class" : ".CreateChallengeRequest",
      "accessType" : "PUBLIC",
      "autoStartJoinedChallengeOnMaxPlayers" : false,
      "challengeMessage" : "Who is king of the track?",
      "challengeShortCode" : "FASTEST_LAP",
      "currency1Wager" : 10,
      "currency2Wager" : 10,
      "currency3Wager" : 10,
      "currency4Wager" : 10,
      "currency5Wager" : 10,
      "currency6Wager" : 10,
      "eligibilityCriteria" : {
        "segments" : {
          "segment1" : [ "value1", "value2" ],
          "segment2" : "value2"
        }
      },
      "endTime" : "2015-12-30T12:00Z",
      "expiryTime" : "2015-12-30T12:00Z",
      "maxAttempts" : 12,
      "maxPlayers" : 25,
      "minPlayers" : 5,
      "silent" : true,
      "startTime" : "2015-12-30T12:00Z",
      "usersToChallenge" : [ "524c13c7e4b0f3abf2b1ddc0" ]
    }

## Example Response
    
    
    {
      "@class" : ".CreateChallengeResponse",
      "challengeInstanceId" : "524d4877e4b0f3abf2b244f7",
      "scriptData" : { }
    }