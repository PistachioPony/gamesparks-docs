title: PushRegistrationRequest
link: https://docs.gamesparks.net/documentation/request-api/misc-request-api/pushregistrationrequest
author: gabriel.page
description: 
post_id: 2244
created: 2014/05/08 11:10:22
created_gmt: 2014/05/08 11:10:22
comment_status: closed
post_name: pushregistrationrequest
status: publish
post_type: post

<!--Registers the current device for push notifications. Currently GameSparks supports iOS, GCM & Microsoft Push notifications. -->

# PushRegistrationRequest

Registers the current device for push notifications. Currently GameSparks supports iOS, GCM & Microsoft Push notifications.

Supply the device type, and the push notification identifier for the device.

#### Parameters

Name : TypeRequiredDescription

deviceOS:string
Yes

The type of id, valid values are ios, android, wp8, w8, kindle or viber

pushId:string
Yes

The push notification identifier for the device

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

#### Errors

NameValueDescription

deviceOS
IOS|ANDROID|WP8|W8|KINDLE

deviceOS is not a valid value

  


## Example Request
    
    
    {
      "@class" : ".PushRegistrationRequest",
      "deviceOS" : "ANDROID",
      "pushId" : "1234"
    }

## Example Response
    
    
    {
      "@class" : ".PushRegistrationResponse",
      "registrationId" : "1234567890ABCD",
      "scriptData" : { }
    }