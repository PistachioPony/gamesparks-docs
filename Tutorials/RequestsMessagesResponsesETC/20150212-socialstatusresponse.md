title: SocialStatusResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/socialstatusresponse
author: GameSparks
description: 
post_id: 5903
created: 2015/02/12 17:27:41
created_gmt: 2015/02/12 17:27:41
comment_status: open
post_name: socialstatusresponse
status: publish
post_type: post

<!--A response containing the details of a the players social connections -->

# SocialStatusResponse

A response containing the details of a the players social connections

#### Parameters

Name : TypeDescription

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

statuses:SocialStatus

A list of social statuses.

### SocialStatus

A the details of a social connection

Name:TypeDescription

active:boolean
When the token is still active.

expires:date
When the token expires (if available).

systemId:string
The identifier of the external platform.
  


## Example
    
    
    {
      "@class" : ".SocialStatusResponse",
      "scriptData" : { },
      "statuses" : [ {
        "active" : false,
        "expires" : "2015-12-30T12:00Z",
        "systemId" : "FB"
      } ]
    }