title: EndSessionRequest
link: https://docs.gamesparks.net/documentation/request-api/analytics-request-api/endsessionrequest
author: gabriel.page
description: 
post_id: 2219
created: 2014/05/08 11:13:56
created_gmt: 2014/05/08 11:13:56
comment_status: closed
post_name: endsessionrequest
status: publish
post_type: post

<!--Records the end of the current player's active session. -->

# EndSessionRequest

Records the end of the current player's active session.

The SDK will automatically create a new session ID when the application is started, this method can be useful to call when the app goes into the background to allow reporting on player session length.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".EndSessionRequest"
    }

## Example Response
    
    
    {
      "@class" : ".EndSessionResponse",
      "scriptData" : { }
    }