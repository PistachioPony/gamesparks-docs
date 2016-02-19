title: GetPropertyResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/getpropertyresponse
author: GameSparks
description: 
post_id: 8393
created: 2015/08/10 08:53:50
created_gmt: 2015/08/10 08:53:50
comment_status: closed
post_name: getpropertyresponse
status: publish
post_type: post

<!--A response containing the requested property -->

# GetPropertyResponse

A response containing the requested property

#### Parameters

Name : TypeDescription

property:JSON

The property value

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
      "@class" : ".GetPropertyResponse",
      "property" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
      "scriptData" : { }
    }