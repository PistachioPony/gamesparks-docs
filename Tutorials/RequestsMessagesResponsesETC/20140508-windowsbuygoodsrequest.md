title: WindowsBuyGoodsRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/windowsbuygoodsrequest
author: gabriel.page
description: 
post_id: 2261
created: 2014/05/08 11:10:21
created_gmt: 2014/05/08 11:10:21
comment_status: closed
post_name: windowsbuygoodsrequest
status: publish
post_type: post

<!--Processes a transaction receipt from a windows store purchase. -->

# WindowsBuyGoodsRequest

Processes a transaction receipt from a windows store purchase.

The GameSparks platform will validate the receipt using the signature embedded in the xml. The Id in the xml will be recorded and the request will be rejected if the Id has previously been processed, this prevents replay attacks.

Once verified, the players account will be credited with the Virtual Good, or Virtual Currency the purchase contains. The virtual good will be looked up by matching the productId in the xml with the 'WP8 Product ID' configured against the virtual good.

#### Parameters

Name : TypeRequiredDescription

platform:string
No

Allows you to specify the platform

receipt:string
Yes

The xml reciept returned from the windows phone 8 store

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

uniqueTransactionByPlayer:boolean
No

If set to true, the transactionId from this receipt will not be globally valdidated, this will mean replays between players are possible.

#### Errors

NameValueDescription

verificationError
1

No matching virtual good can be found

verificationError
2

The XMLSignature validation failed

verificationError
5

The Id in the receipt xml has previously been processed

  


## Example Request
    
    
    {
      "@class" : ".WindowsBuyGoodsRequest",
      "platform" : "PC",
      "receipt" : "xmlreceiptfromwp8store",
      "uniqueTransactionByPlayer" : true
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