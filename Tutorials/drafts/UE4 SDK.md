# UE4 SDK

# Welcome to the GameSparks SDK for Unreal Engine 4.

We're pleased to announce the release of the SDK, with full blueprint support for all GameSparks API calls.

## Getting Started

  * Download the SDK <https://bitbucket.org/gamesparks/gamesparks-cpp-unreal>
  * Copy the GameSparks folder directly into your projects "Plugins" folder
It's as simple as that. The SDK is now configured to be used in your project.

## Using the SDK.

We recommend adding the SDK configuration to your GameMode blueprint. This allows you to configure your API Key and Secret in a single place that can be re-used for all levels. To do this in your game mode blueprint:

  * "Add Component" -> "GameSparks"
  * Attach "GameSparks Connect" to "Event Begin Play" and enter your API Key, API Secret and whether you want to use the live or preview servers;
  * Attach "GameSparks Disconnect" to "Event End Play". This will ensure the SDK is disconnected once your play session stops.
Once you have done this you should end up with a game mode blueprint similar to this : ![Screen Shot 2015-07-29 at 15.45.44](/wp-content/uploads/2015/07/Screen-Shot-2015-07-29-at-15.45.44-1024x582.png)   Using the GameSparks API in your own blueprints.

### Attaching to Events.

The GameSparks component provides Events you can bind to in your blueprints. On Game Sparks Available - This is triggered when the SDK changes from available and unavailable (and vice versa). We generally wait until the SDK is available before sending requests. A boolean variable is sent with the event to indicate whether the SDK is available or not. On GameSparks Debug Log - You can attach to this event to show the debug logging the SDK generates. This is generally only useful for development. We generally wait until we get the available event for the SDK before we do anything. To add this event to your blueprint, click the GameSparks component in the components area, then in the details area the event is available to be added to the blueprint. In this simple example, we are attaching a branch to the event and printing a different string depending on the availability state. ![Screen Shot 2015-07-29 at 16.09.55](/wp-content/uploads/2015/07/Screen-Shot-2015-07-29-at-16.09.55.png)  

### Sending Requests and Getting responses.

The request / response mechanism in the UE4 SDK is asynchronous, the pattern is to invoke the send function for a request setting the various values in the node, then binding to the response event, at which point you can read the response data. We generally right click on the blueprint grid, then type the name of the request we want to send (the request types available to the SDK are all listed [here](/documentation/gamesparks-service-request-api). All responses types are USTRUCTS so you can break the struct in the blueprint to get the data you want out of them. Each response attribute has both a getter, and a "has" boolean that you want use to determine if the attribute is set. In this example we have dome a simple AuthenticationRequest with a username and password. Once the response is received the displayName of the authenticated player is printed.

### Listening for Asynchronous Messages

The GameSparks platform supports messages being pushed to a player without them having made a request, these might be chat messages, or anything else you want to send from the platform. The SDK supports listening to all the different message types (The list of available message types are [here](/documentation/gamesparks-message-api)) within your blueprint. All the message events are found in the "GSMessageListenersComponent" which needs to be added to your blueprint. To listen to ScriptMessage (this is the one you will be sending from your cloud code).

  * Select the GSMessageListeners in the components area, and you'll see all the events you can attach to in the details panel.
  * Click the + symbol next to "On Script Message"
  * Break the Message to access the message attributes
  This example shows a Print String attached to the ScriptMessage event that prints the "MessageId" attribute of the message. ![Screen Shot 2015-07-29 at 16.36.53](/wp-content/uploads/2015/07/Screen-Shot-2015-07-29-at-16.36.53.png)

### Custom JSON Structures

All parts of the API support user extensions through the "scriptData" attribute on the requests / responses / messages. A node type "Game Sparks Script Data" exists that allows you to build or read these custom JSON structures directly through blueprints. To create some custom JSON, first call the "Create Game Sparks Script Data" function, this will spawn the object in the blueprint ready for you to start adding data to it. When adding an attribute to the object you need to provide the name as a String, then the Value as an object. The different types that can be attached (and the supporting methods) are : [su_table]

 Data Type Write Method Read Method

String
Set String
Get String

Number
Set Number
Get Number

Boolean
Set Boolean
Get Boolean

Object
Set Object
Get Object

String Array
Set String
Get String

Number Array
Set Number
Get Number

Boolean Array
Set Boolean
Get Boolean

Object Array
Set GSData Array
Get GSData Array
[/su_table] The ability to nest Script Data within Script Data gives you the ability to read and write complex JSON structures, the following example gives you a taste, but with these nodes there are few limits to what you do. ![Screen Shot 2015-07-29 at 16.52.07](/wp-content/uploads/2015/07/Screen-Shot-2015-07-29-at-16.52.07-1024x445.png)
