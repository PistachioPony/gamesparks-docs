title: GetDownloadableRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/getdownloadablerequest
author: gabriel.page
description: 
post_id: 2240
created: 2014/05/08 11:12:42
created_gmt: 2014/05/08 11:12:42
comment_status: closed
post_name: getdownloadablerequest
status: publish
post_type: post

<!--Returns a secure, time sensitive url to allow the game to download a piece of downloadable content stored in the GameSparks platform. -->

# GetDownloadableRequest

Returns a secure, time sensitive url to allow the game to download a piece of downloadable content stored in the GameSparks platform.

#### Parameters

Name : TypeRequiredDescription

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

shortCode:string
Yes

The short code of the Downloadable item

#### Errors

NameValueDescription

shortCode
INVALID

The short code does not match any Downloadable shortCode

  


## Example Request
    
    
    {
      "@class" : ".GetDownloadableRequest",
      "shortCode" : "LEVEL1_MAP"
    }

## Example Response
    
    
    {
      "@class" : ".GetDownloadableResponse",
      "lastModified" : "2015-12-30T12:00Z",
      "scriptData" : { },
      "shortCode" : "SPLASH_IMAGE",
      "size" : 10000,
      "url" : "http://gamesparksbetabinaries.blob.core.windows.net/game-1234/map.xml.."
    }