title: ListVirtualGoodsRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/listvirtualgoodsrequest
author: gabriel.page
description: 
post_id: 2260
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: listvirtualgoodsrequest
status: publish
post_type: post

<!--Returns the list of configured virtual goods. -->

# ListVirtualGoodsRequest

Returns the list of configured virtual goods.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

tags:string[]
No

A filter to only include goods with the given tags. Each good must have all the provided tags.

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".ListVirtualGoodsRequest",
      "tags" : [ "['TAG1']" ]
    }

## Example Response
    
    
    {
      "@class" : ".ListVirtualGoodsResponse",
      "scriptData" : { },
      "virtualGoods" : [ {
        "WP8StoreProductId" : "...",
        "amazonStoreProductId" : "...",
        "currency1Cost" : 0,
        "currency2Cost" : 0,
        "currency3Cost" : 0,
        "currency4Cost" : 0,
        "currency5Cost" : 0,
        "currency6Cost" : 0,
        "description" : "...",
        "googlePlayProductId" : "...",
        "iosAppStoreProductId" : "...",
        "maxQuantity" : 0,
        "name" : "...",
        "propertySet" : "{"property1" : { "key" : "value" }, "property2" : ["val1", "val2"]",
        "shortCode" : "...",
        "tags" : "...",
        "type" : "...",
        "w8StoreProductId" : "..."
      } ]
    }