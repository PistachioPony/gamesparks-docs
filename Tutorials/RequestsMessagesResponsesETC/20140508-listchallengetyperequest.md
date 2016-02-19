title: ListChallengeTypeRequest
link: https://docs.gamesparks.net/documentation/request-api/multiplayer-request-api/listchallengetyperequest
author: gabriel.page
description: 
post_id: 2233
created: 2014/05/08 11:13:57
created_gmt: 2014/05/08 11:13:57
comment_status: closed
post_name: listchallengetyperequest
status: publish
post_type: post

<!--Returns the list of configured challenge types. -->

# ListChallengeTypeRequest

Returns the list of configured challenge types.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListChallengeTypeRequest"
    }

## Example Response
    
    
    {
      "@class" : ".ListChallengeTypeResponse",
      "challengeTemplates" : [ {
        "challengeShortCode" : "...",
        "description" : "...",
        "getleaderboardName" : "...",
        "name" : "...",
        "tags" : "..."
      } ],
      "scriptData" : { }
    }