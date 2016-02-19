title: GetRunningTotalsRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/getrunningtotalsrequest
author: gabriel.page
description: 
post_id: 2241
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: getrunningtotalsrequest
status: publish
post_type: post

<!--Get the aggregation data for a group of the player's friends given running total specified by short code. -->

# GetRunningTotalsRequest

Get the aggregation data for a group of the player's friends given running total specified by short code.

#### Parameters

Name : TypeRequiredDescription

friendIds:string[]
No

A friend id or an array of friend ids

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

shortCode:string
Yes

The short code of the running total

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".GetRunningTotalsRequest",
      "friendIds" : [ "524c13c7e4b0f3abf2b1ddc0" ],
      "shortCode" : "HIGH_SCORE"
    }

## Example Response
    
    
    {
      "@class" : ".GetRunningTotalsResponse",
      "runningTotals" : "...",
      "scriptData" : { }
    }