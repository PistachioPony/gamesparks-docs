title: AnalyticsRequest
link: https://docs.gamesparks.net/documentation/request-api/analytics-request-api/analyticsrequest
author: gabriel.page
description: 
post_id: 2218
created: 2014/05/08 11:13:56
created_gmt: 2014/05/08 11:13:56
comment_status: closed
post_name: analyticsrequest
status: publish
post_type: post

<!--Records some custom analytical data. -->

# AnalyticsRequest

Records some custom analytical data.

Simple analytics, where you just need to track the number of times something happened, just take a key parameter. We'll record the players id against the data to allow you to report on averages per user

Timed analytics allow you to send start and end timer requests, and with this data GameSparks can track the length of time something takes.

If an end request is sent without a matching start timer the request will fail silently and your analytics data might not contain what you expect.

If both start and end are supplied, the request will be treated as a start timer.

An additional data payload can be attached to the event for advanced reporting. This data can be a string, number or JSON object.

If a second start timer is created using a key that has already had a start timer created without an end, the previous one will be marked as abandoned.

#### Parameters

Name : TypeRequiredDescription

data:JSON
No

Custom data payload

end:boolean
No

Use the value true to indicate it's an end timer

key:string
No

The key you want to track this analysis with.

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

start:boolean
No

Use the value true to indicate it's a start timer

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".AnalyticsRequest",
      "data" : "...",
      "end" : true,
      "key" : "123",
      "start" : true
    }

## Example Response
    
    
    {
      "@class" : ".AnalyticsResponse",
      "scriptData" : { }
    }