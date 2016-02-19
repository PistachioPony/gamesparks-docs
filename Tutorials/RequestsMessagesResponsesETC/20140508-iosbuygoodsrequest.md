title: IOSBuyGoodsRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/iosbuygoodsrequest
author: gabriel.page
description: 
post_id: 2259
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: iosbuygoodsrequest
status: publish
post_type: post

<!--Processes a transaction receipt from an App Store in app purchase. -->

# IOSBuyGoodsRequest

Processes a transaction receipt from an App Store in app purchase.

The GameSparks platform will validate the receipt with Apple and process the response. The transaction_id in the response will be recorded and the request will be rejected if the transaction_id has previously been processed, this prevents replay attacks.

Once verified, the players account will be credited with the Virtual Good, or Virtual Currency the purchase contains. The virtual good will be looked up by matching the product_id in the response with the 'IOS Product ID' configured against the virtual good.

#### Parameters

Name : TypeRequiredDescription

receipt:string
Yes

The receipt obtained from SKPaymentTransaction. transactionReceipt

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

sandbox:boolean
No

Should the sandbox account be used

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

The Apple servers failed to verify the receipt

verificationError
3

There was an error connecting to the Apple server

verificationError
5

The transaction_id has been processed before

  


## Example Request
    
    
    {
      "@class" : ".IOSBuyGoodsRequest",
      "receipt" : "appstorereceiptdata",
      "sandbox" : true,
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