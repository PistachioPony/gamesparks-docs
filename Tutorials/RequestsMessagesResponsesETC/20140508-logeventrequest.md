title: LogEventRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/logeventrequest
author: gabriel.page
description: 
post_id: 2254
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: logeventrequest
status: publish
post_type: post

<!--Allows a user defined event to be triggered. -->

# LogEventRequest

Allows a user defined event to be triggered.

This call differs from most as it does not have a fixed format. The @class and eventKey attributes are common, but the rest of the attributes are as defined in the Event object configured in the dev portal.

The example below shows a request to an event with a short code of HS with 2 attributes, 'HS' & 'GL'.

#### Parameters

Name : TypeRequiredDescription

eventKey:string
Yes

The short code of the event to trigger

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".LogEventRequest",
      "eventKey" : "SCORE"
    }

## Example Response
    
    
    {
      "@class" : ".LogEventResponse",
      "scriptData" : { }
    }