title: ConsumeVirtualGoodRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/consumevirtualgoodrequest
author: gabriel.page
description: 
post_id: 2257
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: consumevirtualgoodrequest
status: publish
post_type: post

<!--Consumes a given amount of the specified virtual good. -->

# ConsumeVirtualGoodRequest

Consumes a given amount of the specified virtual good.

#### Parameters

Name : TypeRequiredDescription

quantity:number
Yes

The amount of virtual goods to be consumed

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

shortCode:string
Yes

The short code of the virtual good to be consumed

#### Errors

NameValueDescription

qty
INSUFFICIENT

The player does not have sufficient virtual goods for shortcode specified

  


## Example Request
    
    
    {
      "@class" : ".ConsumeVirtualGoodRequest",
      "quantity" : 4,
      "shortCode" : "MUSHROOM"
    }

## Example Response
    
    
    {
      "@class" : ".ConsumeVirtualGoodResponse",
      "scriptData" : { }
    }