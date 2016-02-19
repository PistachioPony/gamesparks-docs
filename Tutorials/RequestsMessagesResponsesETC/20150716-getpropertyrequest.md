title: GetPropertyRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/getpropertyrequest
author: GameSparks
description: 
post_id: 8361
created: 2015/07/16 21:26:54
created_gmt: 2015/07/16 21:26:54
comment_status: open
post_name: getpropertyrequest
status: publish
post_type: post

<!--Get the property for the given short Code. -->

# GetPropertyRequest

Get the property for the given short Code.

#### Parameters

Name : TypeRequiredDescription

propertyShortCode:string
Yes

The shortCode of the property to return.

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

property
NOT_FOUND

No property with given shortCode could be found.

  


## Example Request
    
    
    {
      "@class" : ".GetPropertyRequest",
      "propertyShortCode" : "prop1"
    }

## Example Response
    
    
    {
      "@class" : ".GetPropertyResponse",
      "property" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
      "scriptData" : { }
    }