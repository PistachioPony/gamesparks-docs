title: GetPropertySetResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/getpropertysetresponse
author: GameSparks
description: 
post_id: 8395
created: 2015/08/10 08:53:52
created_gmt: 2015/08/10 08:53:52
comment_status: closed
post_name: getpropertysetresponse
status: publish
post_type: post

<!--A response containing the requested property set -->

# GetPropertySetResponse

A response containing the requested property set

#### Parameters

Name : TypeDescription

propertySet:JSON

The property set

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
      "@class" : ".GetPropertySetResponse",
      "propertySet" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
      "scriptData" : { }
    }