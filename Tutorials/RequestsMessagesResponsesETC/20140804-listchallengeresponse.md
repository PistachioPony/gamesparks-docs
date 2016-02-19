title: ListChallengeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/listchallengeresponse
author: GameSparks
description: 
post_id: 4324
created: 2014/08/04 15:33:45
created_gmt: 2014/08/04 15:33:45
comment_status: open
post_name: listchallengeresponse
status: publish
post_type: post

<!--A response containing challenges that are in the state that was specified in the request -->

# ListChallengeResponse

A response containing challenges that are in the state that was specified in the request

#### Parameters

Name : TypeDescription

challengeInstances:Challenge

A list of JSON objects representing the challenges.

### Challenge

A nested object that represents the challenge data.

Name:TypeDescription

accepted:PlayerDetail
A list of PlayerDetail objects that represents the players that have accepted this challenge.

### PlayerDetail

An object representing a player's id and name

Name:TypeDescription

externalIds:JSON
A player's external identifiers

id:string
A player's id

name:string
A player's name

challengeId:string
A unique identifier for this challenge.

challengeMessage:string
The message included in the challenge by the challenging player who created the challenge.

challengeName:string
The name of the challenge that this message relates to.

challenged:PlayerDetail
A list of PlayerDetail objects that represents the players that were challenged in this challenge.

### PlayerDetail

An object representing a player's id and name

Name:TypeDescription

externalIds:JSON
A player's external identifiers

id:string
A player's id

name:string
A player's name

challenger:PlayerDetail
Details of the player who issued this challenge.

### PlayerDetail

An object representing a player's id and name

Name:TypeDescription

externalIds:JSON
A player's external identifiers

id:string
A player's id

name:string
A player's name

currency1Wager:number
The amount of type 1 currency that has been wagered on this challenge.

currency2Wager:number
The amount of type 2 currency that has been wagered on this challenge.

currency3Wager:number
The amount of type 3 currency that has been wagered on this challenge.

currency4Wager:number
The amount of type 4 currency that has been wagered on this challenge.

currency5Wager:number
The amount of type 5 currency that has been wagered on this challenge.

currency6Wager:number
The amount of type 6 currency that has been wagered on this challenge.

declined:PlayerDetail
A list of PlayerDetail objects that represents the players that have declined this challenge.

### PlayerDetail

An object representing a player's id and name

Name:TypeDescription

externalIds:JSON
A player's external identifiers

id:string
A player's id

name:string
A player's name

endDate:date
The date when the challenge ends.

expiryDate:date
The latest date that a player can accept the challenge.

maxTurns:number
The maximum number of turns that this challenge is configured for.

nextPlayer:string
In a turn based challenge this fields contains the player's id whose turn it is next.

scriptData:ScriptData
ScriptData is arbitrary data that can be stored in a challenge instance by a Cloud Code script.

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Name:TypeDescription

myKey:string
An arbitrary data key

myValue:JSON
An arbitrary data value.

shortCode:string
The challenge's short code.

startDate:date
The date when the challenge starts.

state:string
One of these possible state values: ISSUED, EXPIRED, ACCEPTED, DECLINED, COMPLETE, WITHDRAWN, RUNNING, WAITING, RECEIVED

turnCount:PlayerTurnCount
A collection containing the number of turns taken by each player that has accepted the challenge.

### PlayerTurnCount

Represents the number of turns a player has taken in a turn based challenge.

Name:TypeDescription

count:string
The number of turns that the player has taken so far during this challenge.

playerId:string
The unique player id.

requestId:string

The ID of the corresponding Request

scriptData:ScriptData

A JSON Map of any data added either to the Request or the Response by your Cloud Code

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Name:TypeDescription

myKey:string
An arbitrary data key

myValue:JSON
An arbitrary data value.
  


## Example
    
    
    {
      "@class" : ".ListChallengeResponse",
      "challengeInstances" : [ {
        "accepted" : [ {
          "externalIds" : {
            "FB" : "1234",
            "TW" : "2345"
          },
          "id" : "52a5cc00e4b0a0eeaadfe3a1",