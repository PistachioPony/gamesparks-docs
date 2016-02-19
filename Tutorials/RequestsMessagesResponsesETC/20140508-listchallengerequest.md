title: ListChallengeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/listchallengerequest
author: gabriel.page
description: 
post_id: 2232
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: listchallengerequest
status: publish
post_type: post

<!--Returns a list of challenges in the state defined in the 'state' field. -->

# ListChallengeRequest

Returns a list of challenges in the state defined in the 'state' field.

The response can be further filtered by passing a shortCode field which will limit the returned lists to challenges of that short code.

Valid states are:

WAITING : The challenge has been issued and accepted and is waiting for the start date.

RUNNING : The challenge is active.

ISSUED : The challenge has been issued by the current player and is waiting to be accepted.

RECEIVED : The challenge has been issued to the current player and is waiting to be accepted.

COMPLETE : The challenge has completed.

DECLINED : The challenge has been issued by the current player and has been declined.

#### Parameters

Name : TypeRequiredDescription

entryCount:number
No

The number of items to return in a page (default=50)

offset:number
No

The offset (page number) to start from (default=0)

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

shortCode:string
No

The type of challenge to return

state:string
No

The state of the challenged to be returned

states:string[]
No

The states of the challenges to be returned

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListChallengeRequest",
      "entryCount" : 100,
      "offset" : 200,
      "shortCode" : "FASTEST_LAP",
      "state" : "ISSUED",
      "states" : [ "ISSUED" ]
    }

## Example Response
    
    
    {
      "@class" : ".ListChallengeResponse",
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