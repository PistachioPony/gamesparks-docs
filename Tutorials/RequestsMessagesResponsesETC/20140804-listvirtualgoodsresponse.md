title: ListVirtualGoodsResponse
link: https://docs.gamesparks.net/documentation/response-api/store-response-api/listvirtualgoodsresponse
author: GameSparks
description: 
post_id: 4349
created: 2014/08/04 15:33:06
created_gmt: 2014/08/04 15:33:06
comment_status: open
post_name: listvirtualgoodsresponse
status: publish
post_type: post

<!--A response containing the list of configured virtual goods. -->

# ListVirtualGoodsResponse

A response containing the list of configured virtual goods.

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

virtualGoods:VirtualGood

A list of JSON objects containing virtual goods data

### VirtualGood

A nested object that represents the virtual good.

Name:TypeDescription

WP8StoreProductId:string
The Windows Phone 8 productId of the item.

amazonStoreProductId:string
The Amazon Store productId of the item.

currency1Cost:number
The Currency1 cost of the Virtual Good

currency2Cost:number
The Currency2 cost of the Virtual Good

currency3Cost:number
The Currency3 cost of the Virtual Good

currency4Cost:number
The Currency4 cost of the Virtual Good

currency5Cost:number
The Currency5 cost of the Virtual Good

currency6Cost:number
The Currency6 cost of the Virtual Good

description:string
The description of the Virtual Good

googlePlayProductId:string
The google play productId of the item.

iosAppStoreProductId:string
The iOS AppStore productId of the item.

maxQuantity:number
The maximum number of the Virtual Good that can be owned at one time

name:string
The name of the Virtual Good

propertySet:JSON
The custom property set configured on the item.

shortCode:string
The short code of the Virtual Good

tags:string
The tags of the Virtual Good

type:string
The type of the virtual good, "VGOOD" or "CURRENCY"

w8StoreProductId:string
The Windows 8 productId of the item.
  


## Example
    
    
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