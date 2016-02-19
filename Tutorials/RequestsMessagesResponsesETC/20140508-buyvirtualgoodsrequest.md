title: BuyVirtualGoodsRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/buyvirtualgoodsrequest
author: gabriel.page
description: 
post_id: 2256
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: buyvirtualgoodsrequest
status: publish
post_type: post

<!--Purchases a virtual good with an in game currency. Once purchased the virtual good will be added to the players account. -->

# BuyVirtualGoodsRequest

Purchases a virtual good with an in game currency. Once purchased the virtual good will be added to the players account.

#### Parameters

Name : TypeRequiredDescription

currencyType:number
Yes

Which virtual currency to use. (1 to 6)

quantity:number
Yes

The number of items to purchase

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

shortCode:string
Yes

The short code of the virtual good to be purchased

#### Errors

NameValueDescription

currencyType
UNRECOGNISED

Not a valid currency, valid values are 1 to 6

currency1
INSUFFICIENT_FUNDS

The player does not have enough currency 1 funds to complete the purchase

currency2
INSUFFICIENT_FUNDS

The player does not have enough currency 2 funds to complete the purchase

currency3
INSUFFICIENT_FUNDS

The player does not have enough currency 3 funds to complete the purchase

currency4
INSUFFICIENT_FUNDS

The player does not have enough currency 4 funds to complete the purchase

currency5
INSUFFICIENT_FUNDS

The player does not have enough currency 5 funds to complete the purchase

currency6
INSUFFICIENT_FUNDS

The player does not have enough currency 6 funds to complete the purchase

  


## Example Request
    
    
    {
      "@class" : ".BuyVirtualGoodsRequest",
      "currencyType" : 2,
      "quantity" : 1,
      "shortCode" : "SWORD1"
    }

## Example Response
    
    
    {
      "@class" : ".BuyVirtualGoodResponse",
      "boughtItems" : [ {
        "quantity" : 0,
        "shortCode" : "..."
      } ],
      "currency1Added" : 1,
      "currency2Added" : 1,
      "currency3Added" : 1,
      "currency4Added" : 1,
      "currency5Added" : 1,
      "currency6Added" : 1,
      "currencyConsumed" : 1,
      "currencyType" : 1,
      "scriptData" : { }
    }