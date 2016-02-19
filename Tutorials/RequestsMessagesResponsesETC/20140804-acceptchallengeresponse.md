title: AcceptChallengeResponse
link: https://docs.gamesparks.net/documentation/response-api/multiplayer-response-api/acceptchallengeresponse
author: GameSparks
description: 
post_id: 4316
created: 2014/08/04 15:35:11
created_gmt: 2014/08/04 15:35:11
comment_status: open
post_name: acceptchallengeresponse
status: publish
post_type: post

<!--A response containing the challenge instance id that was accepted. -->

# AcceptChallengeResponse

A response containing the challenge instance id that was accepted.

#### Parameters

Name : TypeDescription

challengeInstanceId:string

The ID of the challenge

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
      "@class" : ".AcceptChallengeResponse",
      "challengeInstanceId" : "524d4721e4b0f3abf2b2446a",
      "scriptData" : { }
    }