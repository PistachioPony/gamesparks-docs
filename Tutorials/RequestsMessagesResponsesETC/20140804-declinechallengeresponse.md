title: DeclineChallengeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/declinechallengeresponse
author: GameSparks
description: 
post_id: 4319
created: 2014/08/04 15:35:10
created_gmt: 2014/08/04 15:35:10
comment_status: open
post_name: declinechallengeresponse
status: publish
post_type: post

<!--A response containing the challenge instance id of the challenge that was declined -->

# DeclineChallengeResponse

A response containing the challenge instance id of the challenge that was declined

#### Parameters

Name : TypeDescription

challengeInstanceId:string

The challenge instance id

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
      "@class" : ".DeclineChallengeResponse",
      "challengeInstanceId" : "524d4877e4b0f3abf2b244f7",
      "scriptData" : { }
    }