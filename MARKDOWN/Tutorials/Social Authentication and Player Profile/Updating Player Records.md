---
nav_sort: 2
src: /Tutorials/Social Authentication and Player Profile/Updating Player Records.md
---

# Updating Player Records

## Introduction

After a player has been created, you as the developer or the player may want to change details associated with the account such as password, userName, displayName etc This tutorial will demonstrate how to use the ChangeDetails request in cloud code.  

## Change Details Request


This example shows an event which takes a string input and sets it as the player's new username using the ChangeDetails request and outputs the response as scriptData.

```
//String input
//String input
Spark.getData().string

//Create an instance of the ChangeUserDetails request
var changeDetailsRequest = new SparkRequests.ChangeUserDetailsRequest();

//Set the userName. You can also change:
//Language / newPassword / oldPassword / displayName
changeDetailsRequest.userName = string;

//Send request and save response
var response = changeDetailsRequest.Send();

//Output response with scriptData
Spark.setScriptData("response", response);
```
