title: ChangeUserDetailsRequest
link: https://docs.gamesparks.net/documentation/request-api/player-request-api/changeuserdetailsrequest
author: gabriel.page
description: 
post_id: 2246
created: 2014/05/08 11:10:21
created_gmt: 2014/05/08 11:10:21
comment_status: closed
post_name: changeuserdetailsrequest
status: publish
post_type: post

<!--Change the display name of the currently signed in Player. -->

# ChangeUserDetailsRequest

Change the display name of the currently signed in Player.

#### Parameters

Name : TypeRequiredDescription

displayName:string
No

The new display name to set in the player data.

language:string
No

The new language code to set in the player data.

newPassword:string
No

The new password to set in the player data.

oldPassword:string
No

The player's existing password. If supplied it will be checked against the password stored in the player data. This allows you re-authenticate the player making the change.

requestId:string
No

The SDK adds a requestId to all requests, this is used to match responses from the websocket

userName:string
No

The new userName with which this player will sign in. If the player currently authenticates using device authentication this will upgrade their account and require them to use username and password authentication from now on.

#### Errors

NameValueDescription

DETAILS
UNRECOGNISED

The oldPassword did not match the one stored against the player.

USERNAME
TAKEN

The userName supplied is already in use.

  


## Example Request
    
    
    {
      "@class" : ".ChangeUserDetailsRequest",
      "displayName" : "Gabs",
      "language" : "en",
      "newPassword" : "p4cm4n",
      "oldPassword" : "sp4ce1nv4d3r",
      "userName" : "username2"
    }

## Example Response
    
    
    {
      "@class" : ".ChangeUserDetailsResponse",
      "scriptData" : { }
    }