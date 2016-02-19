title: GetRunningTotalsResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/getrunningtotalsresponse
author: GameSparks
description: 
post_id: 4333
created: 2014/08/04 15:33:44
created_gmt: 2014/08/04 15:33:44
comment_status: open
post_name: getrunningtotalsresponse
status: publish
post_type: post

<!--A response containing aggregation data -->

# GetRunningTotalsResponse

A response containing aggregation data

#### Parameters

Name : TypeDescription

requestId:string

The ID of the corresponding Request

runningTotals:JSON

A list of JSON objects representing the aggregation data

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
      "@class" : ".GetRunningTotalsResponse",
      "runningTotals" : "...",
      "scriptData" : { }
    }