title: DeviceAuthenticationRequest
link: https://docs.gamesparks.net/documentation/request-api/authentication-request-api/deviceauthenticationrequest
author: gabriel.page
description: 
post_id: 2221
created: 2014/05/08 11:13:56
created_gmt: 2014/05/08 11:13:56
comment_status: closed
post_name: deviceauthenticationrequest
status: publish
post_type: post

<!--Allows a device id to be used to create an anonymous profile in the game. -->

# DeviceAuthenticationRequest

Allows a device id to be used to create an anonymous profile in the game.

This allows the player to be tracked and have data stored against them before using FacebookConnectRequest to create a full profile.

DeviceAuthenticationRequest should not be used in conjunction with RegistrationRequest as the two accounts will not be merged.

#### Parameters

Name : TypeRequiredDescription

deviceId:string
Yes

A unique device identifier. Each platform has it's own method for getting a unique id

deviceModel:string
No

The device model

deviceName:string
No

The device name

deviceOS:string
Yes

An indicator of the device platform, should be IOS, ANDROID, WP8 or W8

deviceType:string
No

The device type

displayName:string
No

An optional displayname for the player

operatingSystem:string
No

The device type

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

segments:JSON
No

An optional segment configuration for this request.

#### Errors

NameValueDescription

deviceOS
IOS|ANDROID|WP8 

The supplied deviceOS was not in the accepted range

  


## Example Request
    
    
    {
      "@class" : ".DeviceAuthenticationRequest",
      "deviceId" : "thisisalongstringusedasadeviceidentifier",
      "deviceModel" : "Desire",
      "deviceName" : "My Phone",
      "deviceOS" : "IOS",
      "deviceType" : "Android",
      "displayName" : "Gabriel",
      "operatingSystem" : "Android OS 4.1.2 / API-16, ",
      "segments" : {
        "PROFILE" : "P1"
      }
    }

## Example Response
    
    
    {
      "@class" : ".AuthenticationResponse",
      "authToken" : "524c13c7e4b0f3abf2b1ddc0",
      "displayName" : "Nick",
      "newPlayer" : false,
      "scriptData" : { },
      "switchSummary" : {
        "achievements" : [ "..." ],
        "displayName" : "...",
        "externalIds" : "...",
        "id" : "...",
        "online" : false,
        "scriptData" : { },
        "virtualGoods" : [ "..." ]
      },
      "userId" : "523b0628e4b0aba320077410"
    }