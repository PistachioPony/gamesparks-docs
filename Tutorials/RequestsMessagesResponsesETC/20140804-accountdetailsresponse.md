title: AccountDetailsResponse
link: https://docs.gamesparks.net/documentation/response-api/player-response-api/accountdetailsresponse
author: GameSparks
description: 
post_id: 4337
created: 2014/08/04 15:33:44
created_gmt: 2014/08/04 15:33:44
comment_status: open
post_name: accountdetailsresponse
status: publish
post_type: post

<!--A response containing the player's data. -->

# AccountDetailsResponse

A response containing the player's data.

#### Parameters

Name : TypeDescription

achievements:string

A JSON object containing the player's achievments

currency1:number

The amount of type 1 currency that the player holds

currency2:number

The amount of type 2 currency that the player holds

currency3:number

The amount of type 3 currency that the player holds

currency4:number

The amount of type 4 currency that the player holds

currency5:number

The amount of type 5 currency that the player holds

currency6:number

The amount of type 6 currency that the player holds

displayName:string

The player's display name

externalIds:JSON

A JSON object containing the player's external account details

location:Location

A JSON object containing the player's location

### Location

Location details.

Name:TypeDescription

city:string
The city

country:string
The country

latitide:Float
The latitude

longditute:Float
The longditute

requestId:string

The ID of the corresponding Request

reservedCurrency1:JSON

The amount of type 1 currency that the player holds which is currently reserved

reservedCurrency2:JSON

The amount of type 2 currency that the player holds which is currently reserved

reservedCurrency3:JSON

The amount of type 3 currency that the player holds which is currently reserved

reservedCurrency4:JSON

The amount of type 4 currency that the player holds which is currently reserved

reservedCurrency5:JSON

The amount of type 5 currency that the player holds which is currently reserved

reservedCurrency6:JSON

The amount of type 6 currency that the player holds which is currently reserved

userId:string

The player's id

virtualGoods:JSON

A JSON object containing the virtual goods that the player owns

  


## Example
    
    
    {
      "@class" : ".AccountDetailsResponse",
      "achievements" : [ "["T1A1"]" ],
      "currency1" : 1,
      "currency2" : 1,
      "currency3" : 1,
      "currency4" : 1,
      "currency5" : 1,
      "currency6" : 1,
      "displayName" : "Nick",
      "externalIds" : {
        "FB" : "123123123123",
        "TW" : "321321312312"
      },
      "location" : {
        "city" : "...",
        "country" : "...",
        "latitide" : { },
        "longditute" : { }
      },
      "reservedCurrency1" : "1",
      "reservedCurrency2" : "1",
      "reservedCurrency3" : "1",
      "reservedCurrency4" : "1",
      "reservedCurrency5" : "1",
      "reservedCurrency6" : "1",
      "userId" : "523b0628e4b0aba320077410",
      "virtualGoods" : {
        "SWORD" : 2,
        "MUSHROOM" : 1
      }
    }