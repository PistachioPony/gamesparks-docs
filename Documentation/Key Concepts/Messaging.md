# Messaging

Messaging is one of the core features of the GameSparks platform. Messages are primarily used to keep your players informed about events occurring within your game, as they occur.

This diagram shows several messaging use-cases in action.

![](img/Messaging/1.png)

Messages within GameSparks are entirely cross-platform, it doesn't matter what client your players are using they will receive the messages, even if they originate from a player on a different platform.

There are two mechanisms that the GameSparks platform uses to deliver messages to a player, depending on the state of the message recipient:

1. Online Player

As well as using WebSockets for standard request/response use-cases the the GameSparks platform also uses WebSockets for delivering asynchronous messages. This means that an online player will receive any messages sent to them almost instantly. In the above diagram 'Offline Player' represents a player without an authenticated WebSocket connection. All the other players currently have authenticated WebSocket connections so receive their messages as they are sent, via the WebSocket.

2. Offline Player

The GameSparks platform allows you to set up a Game to use push notification as well where they are supported on the players' devices. The setup for these varies depending on the target device so there is some configuration for your game within the GameSparks Developer Portal required to get these to work (see [Push Notifications](/?p=2024)). In addition to the configuration, the player's devices must be registered to receive push notifications which can be done using a [PushRegistrationRequest](/?p=2244). When a message is sent to a player who does not have an authenticated WebSocket connection the GameSparks platform will send a notification to all of the player's devices that have been registered to receive a push notification.

## Message Triggers

There are various triggers that can cause a message to be sent, these fall into three categories:

1. Request message

Requests such as [SendFriendMessageRequest](/?p=2255) and [ChatOnChallengeRequest](/?p=2226) are explicit calls to the platform to send requests to the target players. The content of the message is determined by the sender of the request.

2. Event message

Certain events that occur within the platform will trigger a message to be sent to the relevant players. For example, a message will be sent to a player when they post the new high score on a leaderboard, or once a challenge they are participating in has officially started. The content of the message is determined by [message templates](..\Authentication and Player Profile\Messages.html) configured within the GameSparks Developer Portal.

3. Script message

Like the Request messages this is an explicit call to the platform to send a message to the target players, but in this case it is invoked via Cloud Code using [Spark.sendMessage](/?p=2396#sendMessage). The content of the message is an argument provided to the sendMessage method.
For the full list of message types, and when they will be sent, see [GameSparks Service – Message API](/?p=1550).

## Messages and Cloud Code

You can also tie Cloud Code scripts to the sending of messages to further customise the platform behaviour, for more information on this see [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html).
