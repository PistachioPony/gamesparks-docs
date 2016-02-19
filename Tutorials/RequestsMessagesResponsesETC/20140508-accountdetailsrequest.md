title: AccountDetailsRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/accountdetailsrequest
author: gabriel.page
description: 
post_id: 2245
created: 2014/05/08 11:10:22
created_gmt: 2014/05/08 11:10:22
comment_status: closed
post_name: accountdetailsrequest
status: publish
post_type: post

<!--Retrieves the details of the current authenticated player. -->

# AccountDetailsRequest

Retrieves the details of the current authenticated player.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription   


## Example Request
    
    
    {
      "@class" : ".AccountDetailsRequest"
    }

## Example Response
    
    
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