title: SendTeamChatMessageResponse
link: https://docs.gamesparks.net/documentation/response-api/teams-response-api/sendteamchatmessageresponse
author: GameSparks
description: 
post_id: 5805
created: 2015/01/14 12:23:47
created_gmt: 2015/01/14 12:23:47
comment_status: open
post_name: sendteamchatmessageresponse
status: publish
post_type: post

<!--A response to a send team message request. -->

# SendTeamChatMessageResponse

A response to a send team message request.

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
  


## Example
    
    
    {
      "@class" : ".SendTeamChatMessageResponse",
      "scriptData" : { }
    }