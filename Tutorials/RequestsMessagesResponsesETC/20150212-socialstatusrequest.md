title: SocialStatusRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/socialstatusrequest
author: GameSparks
description: 
post_id: 5899
created: 2015/02/12 17:27:41
created_gmt: 2015/02/12 17:27:41
comment_status: open
post_name: socialstatusrequest
status: publish
post_type: post

<!--Returns detials of the current social connections of this player. Each connection . -->

# SocialStatusRequest

Returns detials of the current social connections of this player. Each connection .

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".SocialStatusRequest"
    }

## Example Response
    
    
    {
      "@class" : ".SocialStatusResponse",
      "scriptData" : { },
      "statuses" : [ {
        "active" : false,
        "expires" : "2015-12-30T12:00Z",
        "systemId" : "FB"
      } ]
    }