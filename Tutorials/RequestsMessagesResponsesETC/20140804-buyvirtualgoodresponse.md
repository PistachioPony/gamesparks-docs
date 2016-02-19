title: BuyVirtualGoodResponse
link: https://docs.gamesparks.net/documentation/response-api/store-response-api/buyvirtualgoodresponse
author: GameSparks
description: 
post_id: 4347
created: 2014/08/04 15:33:08
created_gmt: 2014/08/04 15:33:08
comment_status: open
post_name: buyvirtualgoodresponse
status: publish
post_type: post

<!--A response containing details of the bought items -->

# BuyVirtualGoodResponse

A response containing details of the bought items

#### Parameters

Name : TypeDescription

boughtItems:Boughtitem

A JSON object containing details of the bought items

### Boughtitem

A nested object that represents a bought item.

Name:TypeDescription

quantity:number
The quantity of the bought item

shortCode:string
The short code of the bought item

currency1Added:number

How much currency type 1 was added

currency2Added:number

How much currency type 2 was added

currency3Added:number

How much currency type 3 was added

currency4Added:number

How much currency type 4 was added

currency5Added:number

How much currency type 5 was added

currency6Added:number

How much currency type 6 was added

currencyConsumed:number

For a buy with currency request, how much currency was used

currencyType:number

For a buy with currency request, which currency type was used

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
  


## Example
    
    
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