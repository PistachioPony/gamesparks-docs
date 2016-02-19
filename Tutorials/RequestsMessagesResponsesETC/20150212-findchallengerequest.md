title: FindChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/findchallengerequest
author: GameSparks
description: 
post_id: 5995
created: 2015/02/12 17:27:42
created_gmt: 2015/02/12 17:27:42
comment_status: open
post_name: findchallengerequest
status: publish
post_type: post

<!--Allows a player to find challenges that they are eligible to join. -->

# FindChallengeRequest

Allows a player to find challenges that they are eligible to join.

#### Parameters

Name : TypeRequiredDescription

accessType:string
Yes

The type of challenge to find, either PUBLIC or FRIENDS. Defaults to FRIENDS

count:number
No

The number of challenges to return (MAX=50)

eligibility:JSON
Yes

Optional. Allows the current player's eligibility to be overridden by what is provided here.

offset:number
No

The offset to start from when returning challenges (used for paging)

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

shortCode:string[]
No

Optional shortCodes to filter the results by challenge type

#### Errors

NameValueDescription

eligibility
{ "XXX" : "UNRECOGNISED"}

XXX is not a valid field of eligibility

eligibility
{ "segments" : {"XXX" : "MALFORMED"}}

The value provied for XXX is not in the correct format

  


## Example Request
    
    
    {
      "@class" : ".FindChallengeRequest",
      "accessType" : "FRIENDS",
      "count" : 25,
      "eligibility" : {
        "segments" : {
          "segment1" : "value1",
          "segment2" : "value2"
        }
      },
      "offset" : 0,
      "shortCode" : [ "["1000_CHAL"]" ]
    }

## Example Response
    
    
    {
      "@class" : ".FindChallengeResponse",
      "challengeInstances" : [ {
        "accepted" : [ {
          "externalIds" : {
            "FB" : "1234",
            "TW" : "2345"
          },
          "id" : "52a5cc00e4b0a0eeaadfe3a1",
          "name" : "Player One"
        } ],
        "challengeId" : "52e0f3d0e4b03e0985bcd774",
        "challengeMessage" : "I will crush you all this time!",
        "challengeName" : "Highest score on level 1 challenge",
        "challenged" : [ {
          "externalIds" : {
            "FB" : "1234",
            "TW" : "2345"
          },
          "id" : "52a5cc00e4b0a0eeaadfe3a1",
          "name" : "Player One"
        } ],
        "challenger" : {
          "externalIds" : {
            "FB" : "1234",
            "TW" : "2345"
          },
          "id" : "52a5cc00e4b0a0eeaadfe3a1",
          "name" : "Player One"
        },
        "currency1Wager" : 10,
        "currency2Wager" : 10,
        "currency3Wager" : 10,
        "currency4Wager" : 44,
        "currency5Wager" : 55,
        "currency6Wager" : 66,
        "declined" : [ {
          "externalIds" : {
            "FB" : "1234",
            "TW" : "2345"
          },
          "id" : "52a5cc00e4b0a0eeaadfe3a1",
          "name" : "Player One"
        } ],
        "endDate" : "2015-12-30T12:00Z",
        "expiryDate" : "2015-12-30T12:00Z",
        "maxTurns" : 20,
        "nextPlayer" : "52a5cc00e4b0a0eeaadfe3a1",
        "scriptData" : { },
        "shortCode" : "CH1",
        "startDate" : "2015-12-30T12:00Z",
        "state" : "RUNNING",
        "turnCount" : [ {
          "count" : "3",
          "playerId" : "52933b2fe4b0cb288bca09a3"
        } ]
      } ],
      "scriptData" : { }
    }