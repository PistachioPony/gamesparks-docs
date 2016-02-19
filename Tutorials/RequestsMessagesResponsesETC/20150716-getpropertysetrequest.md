title: GetPropertySetRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/getpropertysetrequest
author: GameSparks
description: 
post_id: 8363
created: 2015/07/16 21:26:55
created_gmt: 2015/07/16 21:26:55
comment_status: open
post_name: getpropertysetrequest
status: publish
post_type: post

<!--Get the property set for the given short Code. -->

# GetPropertySetRequest

Get the property set for the given short Code.

#### Parameters

Name : TypeRequiredDescription

propertySetShortCode:string
Yes

The shortCode of the property set to return.

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

propertySet
NOT_FOUND

No propertySet with given shortCode could be found.

  


## Example Request
    
    
    {
      "@class" : ".GetPropertySetRequest",
      "propertySetShortCode" : "set1"
    }

## Example Response
    
    
    {
      "@class" : ".GetPropertySetResponse",
      "propertySet" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
      "scriptData" : { }
    }