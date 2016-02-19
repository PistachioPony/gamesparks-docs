title: GooglePlayBuyGoodsRequest
link: https://docs.gamesparks.net/documentation/request-api/store-request-api/googleplaybuygoodsrequest
author: gabriel.page
description: 
post_id: 2258
created: 2014/05/08 11:12:41
created_gmt: 2014/05/08 11:12:41
comment_status: closed
post_name: googleplaybuygoodsrequest
status: publish
post_type: post

<!--Processes the response from a Google Play in app purchase flow. -->

# GooglePlayBuyGoodsRequest

Processes the response from a Google Play in app purchase flow.

The GameSparks platform will validate the signature and signed data with the Google Play Public Key configured against the game.

The orderId in the data will be recorded and the request will be rejected if the orderId has previously been processed, this prevents replay attacks.

Once verfied, the players account will be credited with the Virtual Good, or Virtual Currency the purchase contains. The virtual good will be looked up by matching the productId in the signed data with the 'Google Product ID' configured against the virtual good.

It is critical that the signedData is sent exactly as it is returned form google, including any whitespace. Any modification of the signedData will cause the verification process to fail.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

signature:string
Yes

The value obtained from data.getStringExtra("INAPP_DATA_SIGNATURE");

signedData:string
Yes

The value obtained from data.getStringExtra("INAPP_PURCHASE_DATA")

uniqueTransactionByPlayer:boolean
No

If set to true, the transactionId from this receipt will not be globally valdidated, this will mean replays between players are possible.

#### Errors

NameValueDescription

verificationError
5

The orderId in the signedData has previously been processed

verificationError
4

The google play public key is not configured against the game

verificationError
3

There was an error connecting to the google play service

verificationError
2

The signature does not match the signed data

verificationError
1

No matching virtual good can be found

  


## Example Request
    
    
    {
      "@class" : ".GooglePlayBuyGoodsRequest",
      "signature" : "googleplaysignature",
      "signedData" : "googleplaysigneddata",
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