title: ConsumeVirtualGoodResponse
link: https://docs.gamesparks.net/documentation/response-api/store-response-api/consumevirtualgoodresponse
author: GameSparks
description: 
post_id: 4348
created: 2014/08/04 15:33:06
created_gmt: 2014/08/04 15:33:06
comment_status: open
post_name: consumevirtualgoodresponse
status: publish
post_type: post

<!--A response to a consume virtual goods response -->

# ConsumeVirtualGoodResponse

A response to a consume virtual goods response

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
      "@class" : ".ConsumeVirtualGoodResponse",
      "scriptData" : { }
    }