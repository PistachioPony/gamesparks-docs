title: PushRegistrationResponse
link: https://docs.gamesparks.net/documentation/response-api/misc-response-api/pushregistrationresponse
author: GameSparks
description: 
post_id: 4336
created: 2014/08/04 15:33:43
created_gmt: 2014/08/04 15:33:43
comment_status: open
post_name: pushregistrationresponse
status: publish
post_type: post

<!--A response to a push registration request  -->

# PushRegistrationResponse

A response to a push registration request 

#### Parameters

Name : TypeDescription

registrationId:string

An identifier for the successful registration. Clients should store this value to be used in the event the player no longer wants to receive push notifications to this device.

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
      "@class" : ".PushRegistrationResponse",
      "registrationId" : "1234567890ABCD",
      "scriptData" : { }
    }