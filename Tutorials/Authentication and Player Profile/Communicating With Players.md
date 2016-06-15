---
nav_sort: 3
src: /Tutorials/Authentication and Player Profile/Communicating With Players.md
---

# Communicating with Players

## Introduction

You will need to be able to communicate to your players for various reasons. Maybe you want to display a daily message, inform a player of a certain promotion or send a player a token for them to retrieve their password with. GameSparks allows you to send messages to your players with incredible ease, flexibility and customisation using messages both socket (in-game) and push notification and E-mail.  

## Messages

Messages are used to notify your players with events or information. GameSparks includes many native messages such as earning a new achievement, acquiring a new highscore or losing a position on a leaderboard that you can customise or create new ones. Messages can be sent to your players through sockets, so players only receive them once they're authenticated and in-game which would be intercepted and outputted to the player using message listeners. Messages can also be sent to your players through push-notifications.You can update any of the native GameSparks native messages to suit your game and segment the messages depending on the player and display different message entirely. You can also format your message depending on OS and include or omit players with a specific OS.


![](img/PlayerCom/1.jpg)
 

## Cloud Code

Cloud code is a great way to dynamically change strings/images/values within your game in real time to communicate with your players. For example, you can have a message of the day or news column in your main menu which is updated by the game's dev team constantly. You can also use this type of communication for version checking to ensure that online and multiplayer features are only activated if the player has the latest build. Another example of this use would be using Clode code to supply players with the IP address to join a server.

```
    //Sets the IP Address for the player to retrieve
    Spark.setScriptData("serverIPAddress", "127.0.0.1");
    //Sets message of the day to view in-game, updates realtime
    Spark.setScriptData("dayMessage", "Smile! One day until the weekend!");
    //Sets buildVersion to control who gets to access to multiplayer
    Spark.setScriptData("buildVersion", "1.7");
```

 

## E-mail/SendGrid

GameSparks comes integrated with SendGrid which gives you the ability to send E-mails to your players but make sure to save E-mails against your player for reference. For an example of how to use SendGrid for a password retention process, click [here](/Tutorials/Cloud Code and the Test Harness/Password Change.md). For more information about SendGrid, click [here](/API Documentation/Cloud Code API/Comms/SendGrid.md).
