title: AmazonBuyGoodsRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/amazonbuygoodsrequest
author: GameSparks
description: 
post_id: 5780
created: 2015/01/14 12:23:48
created_gmt: 2015/01/14 12:23:48
comment_status: open
post_name: amazonbuygoodsrequest
status: publish
post_type: post

<!--Processes the receipt from an Amazon in app purchase. -->

# AmazonBuyGoodsRequest

Processes the receipt from an Amazon in app purchase.

The GameSparks platform will validate the amazonUserId and receiptId with Amazon using the Amazon Purchase Secret configured against the game.

The receiptId in the data will be recorded and the request will be rejected if the receiptId has previously been processed, this prevents replay attacks.

Once verfied, the players account will be credited with the Virtual Good, or Virtual Currency the purchase contains. The virtual good will be looked up by matching the productId in the receipt with the 'Amazon Product Id' configured against the virtual good.

#### Parameters

Name : TypeRequiredDescription

amazonUserId:string
Yes

The userId obtained from the UserData within a PurchaseResponse

receiptId:string
Yes

The receiptId obtained from the Receipt within a PurchaseResponse

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

uniqueTransactionByPlayer:boolean
No

If set to true, the transactionId from this receipt will not be globally valdidated, this will mean replays between players are possible.

#### Errors

NameValueDescription

receiptId
REQUIRED

The receiptId is missing

amazonUserId
REQUIRED

The amazonUserId is missing

verificationError
4

The Amazon purchase secret is not configured against the game

verificationError
2

The receiptId is not valid for the given userId and secret

verificationError
1

The receiptId has previously been processed

  


## Example Request
    
    
    {
      "@class" : ".AmazonBuyGoodsRequest",
      "amazonUserId" : "userId",
      "receiptId" : "receiptId",
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