title: GetChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/getchallengerequest
author: gabriel.page
description: 
post_id: 2230
created: 2014/05/08 11:13:58
created_gmt: 2014/05/08 11:13:58
comment_status: closed
post_name: getchallengerequest
status: publish
post_type: post

<!--Gets the details of a challenge. The current player must be involved in the challenge for the request to succeed. -->

# GetChallengeRequest

Gets the details of a challenge. The current player must be involved in the challenge for the request to succeed.

#### Parameters

Name : TypeRequiredDescription

challengeInstanceId:string
Yes

The ID of the challenge

message:string
No

An optional message to send with the challenge

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

challengeInstanceId
INVALID

The supplied challengeInstanceId does not match a challenge related to the current player

  


## Example Request
    
    
    {
      "@class" : ".GetChallengeRequest",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "message" : "A challenge message"
    }

## Example Response
    
    
    {
      "@class" : ".GetChallengeResponse",
      "challenge" : {
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
      },
      "scriptData" : { }
    }