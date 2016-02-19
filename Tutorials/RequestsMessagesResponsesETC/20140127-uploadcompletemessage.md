title: UploadCompleteMessage
link: https://docs.gamesparks.net/documentation/message-api/misc-message-api/uploadcompletemessage
author: gabriel.page
description: 
post_id: 1532
created: 2014/01/27 11:14:56
created_gmt: 2014/01/27 11:14:56
comment_status: closed
post_name: uploadcompletemessage
status: publish
post_type: post

<!--A message indicating that the asynchronous upload task trigger by the player is now complete. -->

# UploadCompleteMessage

A message indicating that the asynchronous upload task trigger by the player is now complete.

## Fields

Name : TypeDescription

@class:String
.UploadCompleteMessage

messageId:string

A unique identifier for this message.

notification:boolean

Flag indicating whether this message could be sent as a push notification or not.

scriptData:ScriptData

ScriptData is arbitrary data that can be stored in a message by a Cloud Code script.

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Name:TypeDescription

myKey:string
An arbitrary data key

myValue:JSON
An arbitrary data value.

subTitle:string

A textual title for the message.

summary:string

A textual summary describing the message's purpose.

title:string

A textual title for the message.

uploadData:UploadData

The upload data (if supplied as part of GetUploadUrlRequest) of UploadData objects

### UploadData

This object represents the result of uploading a file to the GameSparks platform.

Name:TypeDescription

fileName:string
The filename of the file that was uploaded.

playerId:string
The unique player id of the player that uploaded the file.

uploadId:string

The id of the upload

  


## Example Message
    
    
    {
      "@class" : ".UploadCompleteMessage",
      "messageId" : "52e05b81e4b03e0985bc80a4",
      "notification" : false,
      "scriptData" : { },
      "subTitle" : "A message sub title",
      "summary" : "A message summary",
      "title" : "A message title",
      "uploadData" : {
        "fileName" : "my-file.txt",
        "playerId" : "52933b2fe4b0cb288bca09a3"
      },
      "uploadId" : "..."
    }