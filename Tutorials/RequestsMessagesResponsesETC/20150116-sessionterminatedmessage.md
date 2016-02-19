title: SessionTerminatedMessage
link: https://docs.gamesparks.net/documentation/message-api/misc-message-api/sessionterminatedmessage
author: GameSparks
description: 
post_id: 5656
created: 2015/01/16 11:16:38
created_gmt: 2015/01/16 11:16:38
comment_status: open
post_name: sessionterminatedmessage
status: publish
post_type: post

<!--A message sent to sockets when disconnectOthers() has been called. -->

# SessionTerminatedMessage

A message sent to sockets when disconnectOthers() has been called.

## Fields

Name : TypeDescription

@class:String
.SessionTerminatedMessage

authToken:string

Used to automatically re-authenticate a client during socket connect.

  


## Example Message
    
    
    {
      "@class" : ".SessionTerminatedMessage",
      "authToken" : "32898e1f-68d7-48e6-b075-b3e9ee0bb7e5"
    }