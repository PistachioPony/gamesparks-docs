title: LogChallengeEventRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/logchallengeeventrequest
author: gabriel.page
description: 
post_id: 2234
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: logchallengeeventrequest
status: publish
post_type: post

<!--Allows a user defined event to be triggered. The event will be posted to the challenge specified. -->

# LogChallengeEventRequest

Allows a user defined event to be triggered. The event will be posted to the challenge specified.

This call differs from most as it does not have a fixed format. The @class, challengeInstanceId and eventKey attributes are common, but the rest of the attributes are as defined in the Event object configured in the dev portal.

The example below shows a request to en event with a short code of HS with 2 attributes, 'HS' & 'GL'.

#### Parameters

Name : TypeRequiredDescription

challengeInstanceId:string
Yes

The ID challenge instance to target

eventKey:string
Yes

The short code of the event to trigger

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

challengeInstanceId
INVALID

The challengeInstanceId does not match a challenge the user has access to

[attribute short code] 
REQUIRED

Each attribute defined in the event must be supplied.

  


## Example Request
    
    
    {
      "@class" : ".LogChallengeEventRequest",
      "challengeInstanceId" : "524d2c02e4b0f3abf2b23a72",
      "eventKey" : "SCORE"
    }

## Example Response
    
    
    {
      "@class" : ".LogChallengeEventResponse",
      "scriptData" : { }
    }