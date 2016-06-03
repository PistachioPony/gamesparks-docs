---
src: Tutorials/Realtime Services/README.md
---

# Realtime Services

## Introduction

Welcome to our series of tutorials on GameSparks Real-Time services SDK. These tutorials are intended to give you an introduction to our Real-Time SDK, how it works, and to provide you with useful example on how our Real-Time might be implemented in a multiplayer game.

The Real-Time services SDK is intended to work in conjunction with our other SDKs, in the case of this series of tutorials, the Unity3D SDK.  We will not be setting up these platform SDKs, so please consult our quick-start guide on setting up the Unity3D SDK here.

## What Are RT Services?

Our real-time services provide a network communication layer which has the ability to send and receive data in real-time.

Our RT services are intended for use in multiplayer networked games where player and game-data should be sent/received as quickly as possible.

We use a PvP model for our network programming. However we use a host server to relay communications between players. This allows our services to support a higher number of players than traditional PvP models, as well has giving you the option to host games in the regions of your choice to reduce latency issues.

Our RT SDK is very lightweight, allowing the user a lot of flexibility on what and how they wish to send data. The benefit of this is not just give the developer control over what is sent and received, but it also keeps the packets as small as possible which makes transmission much more efficient.

We will be covering the following topics:

*Setting Up The Real-Time SDK*

We will integrate the RT SDK into an existing GameSparks project in Unity3D and setting up a new Real-Time match through your game’s portal.

*Matchmaking & Player Lobby*

We will use the GameSparks matchmaking services to match players of a certain skill level.

*Real-Time Chat Services*

Once we have and RT session started from the match we setup in the lobby we will start sending and receiving packets to build an RT chat service.

*Multiplayer Game Example*

To demonstrate our RT services we will be creating a very simple multiplayer game. This example will have networked objects moving around, firing projectiles, and sending and receiving information between each player to update each other’s game-objects.
Each tutorial will have an accompanying video tutorial you can follow along with, as well as downloadable examples of the finished project at the end of the tutorial.


## Setting Up the Real-Time SDK
Before we begin you will need a project with the main GameSparks SDK integrated and setup. We will not be going through this process in this tutorial, but you can find a tutorial on how to setup the main SDK here.
You will first need to download the GameSparks RT SDK package. It is available here.

>> Link to Package download

The RT SDK is separate from the main SDK, so all you will need to do is import the RT package and you are good to go. There is no additional setup required in the Unity3D editor in order for our RT services to work.

## Setting Up Real-Time Matches

In our RT services we refer to a multiplayer game-instance as an RT-Session and in order to find players for the RT session we create a match.
Matches group your players together by a skill-level you choose. In this tutorial we will not be going through the basics of matchmaking but instead we will just show how to make our normal matches work with our RT services. If you would like to learn how to setup matches you can check out our docs here.
Setting up an RT-match is the same process as for normal matches. You go to the Multiplayer tab of your game’s portal and create a new match.

![](img/1.png)

In order to setup an RT-match you need to make sure the ‘RealTime’ toggle is on. You have the option to add a  ‘RealTime Script’ to the match however in this example we will not be covering RT-scripts.
For the example game we will get to later in this series of tutorials, we are building a match for 4 players, and we don’t want the match to start until all players have joined, so i've set the min and mac number of players to 4.
All that is needed to setup an RT-match in GameSparks. In the next tutorial we will see how we can create these matches in the client and get players to connect to the match before we create an RT-session.
