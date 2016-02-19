title: GetDownloadableResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/getdownloadableresponse
author: GameSparks
description: 
post_id: 4332
created: 2014/08/04 15:33:44
created_gmt: 2014/08/04 15:33:44
comment_status: open
post_name: getdownloadableresponse
status: publish
post_type: post

<!--A response containing the download URL for a downloadable item -->

# GetDownloadableResponse

A response containing the download URL for a downloadable item

#### Parameters

Name : TypeDescription

lastModified:date

The date when the downloadable item was last modified

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

shortCode:string

The short code of the item

size:number

The size of the item in bytes

url:string

The download URL

  


## Example
    
    
    {
      "@class" : ".GetDownloadableResponse",
      "lastModified" : "2015-12-30T12:00Z",
      "scriptData" : { },
      "shortCode" : "SPLASH_IMAGE",
      "size" : 10000,
      "url" : "http://gamesparksbetabinaries.blob.core.windows.net/game-1234/map.xml.."
    }