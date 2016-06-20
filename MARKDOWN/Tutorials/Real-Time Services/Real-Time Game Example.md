---
src: /Tutorials/Real-Time Services/Real-Time Game Example.md
---

# Real-Time Multiplayer Game Example

In the previous tutorial, we looked at how to set up a simple chat-system so that players found through the match-making process can communicate with each other. It included a simple introduction to how packets are sent and received using our real-time services.

In this final tutorial, we follow the previous one and use the real-time services to create a simple multiplayer game based on Atari’s Tank! (1974).

## Introduction

The tutorial splits into several parts:
* To begin with we will be creating a scene and setting up all of our game-objects such as the spawn-points, tanks, shells and walls as well as our HUD.
* Then we'll be set up the scripts we need to control the game and instantiating our players into the level. This will constitute our scene setup.
* From there we will be handling all the events and collisions in-game, as well as sending updates about each tank to all other players.

## Scene Setup

In order to follow this tutorial you will need the game-assets available in here.
The assets used in this tutorial are open-source and the original files are available here, thanks to the creator for providing these assets.
Once you have those assets downloaded you can add the Textures folder to the Assets folder of your project. The important texture for this the once called ‘tankSprites’. You will need to set this texture to the multiple sprite-mode and then split the sprite-sheet yourself using the automatic-splice option. I have also set the pixel per unit size to 150 for this tutorial, but you may leave it at 100 if you like.
Once you have the tank-sprites ready we can move onto the main-game scene.
We will be focusing on four parts for setting up the scene…
1.	The Game Heads-Up-Display (HUD)
2.	The borders and obstacles
3.	Player Spawn-Points
4.	Player Tanks
5.	Shells



## The Game HUD

Our game's head-up display (HUD) is going to contain two pieces of information. We will have a text-field for each player’s name and below that we will have another text-field for the number of enemies each player has destroyed.
The HUD will therefore look something like below…

The setup involved the following steps…
1.	Add a new UI Panel to the ‘Main Canvas’ object in the scene hierarchy. This panel should cover the screen from left to right, but only come down a few pixels (used a height of 50 pixels).
2.	For each player add a new empty GameObject and name the object. Space these objects equidistant from each other along the HUD bar.
3.	To each player’s empty GameObject, add two UI Text objects and name them ‘player_name’ and ‘player_score’. There isn’t much else I’ve done to these text-fields except to center the text and align them to fit one above the other.

### Sorting Layers

Before we finish up with the game HUD we need to plan out our sorting layers. There will be a number of sprites in this game and each of them will need to be drawn on different layers. Most importantly, the HUD needs to be always drawn on top of everything else.
So to set the draw-order of our HUD we can select the ‘Main Canvas’ object and then click on the Sorting Layer drop-down menu.

Now select Add New Sorting Layer. We want to create three layers, Shell, Tank and HUD. And set the sorting layer of your Main Canvas to ‘HUD’.



## Borders and Obstacles

Next we will create some barriers/walls, which will surround our scene and stop tanks from being able to leave the camera boundaries. We will also add some obstacles to give the players something to navigate around.
To begin with we’ll create a new empty GameObject in our scene hierarchy and name it ‘Game Controller’. This is where all our game-elements will be kept.  Inside this game-object we need to create another empty GameObject called ‘Level Obstacles’. All objects the player’s tank cannot pass through will go here.
The obstacles we are going to create will be very simple; they will just be a sprite with a BoxCollider2D component attached. I’ve also added the pixel_White sprite to the object. This will allow you to add whatever colour you wish to the sprite.

After we have the level borders setup we can add some obstacles to the middle of the scene…

Now we have barriers we can start putting in our spawn-points.

## Player Spawn Points

The player spawn-points are going to be very simple. They are just an empty GameObject with a name for each player.
All we need from these objects is the position and rotation when each player is created at the start of the game. For this level I’m going to place each spawn-point behind each obstacle so that other players cannot immediately kill each other when they spawn. I’ve also added icons to each of these items so that the game-object standout a little more in the scene.

Before we finish off with these spawn-points we need a way of giving them each an index which will later relate to which player gets spawned from which point. This is really important in making sure each player is spawned from the same place for all instances of the game.
So we will add a new C# script to each spawn point, and all we need for that script is one public integer.
using UnityEngine;
using System.Collections;

public class SpawnPoint : MonoBehaviour {
    public int playerPeerId;
}

We then need to set the peer-ID of each player we wish to spawn at each point.





Note

You could skip adding the script if you like and just name each spawn-point ‘1’,’2’,’3’, etc. after each player’s peerId and use that as the spawn-id instead.


## Player Tanks

Now we will setup our player-tank objects. First we will create a new Sprite and add one of the tank-sprites to the object.

### Tank Sorting Layer

We will now need to set the sorting layer of the tank to ‘Tank’ so that the tank is always drawn underneath the HUD.

### Tank Box Collider

The next thing to do is to add a BoxCollider2D component to the tank and set it up to be just around the body of the tank.

### Tank Rigidbody

And the last thing we need on this sprite is a Rigidbody2D. The rigidbody is going to allow our tanks to detect collisions. We aren’t going to use any force on our tanks, but they do also need to be stopped by our obstacles.
 And for this rigidbody we will set the gravity scale to zero, but we don’t need to change any other attributes right now.

### Shell Spawn-Point

We are going to add an empty GameObject to our tank now. The purpose of this game-object is to give the shells we fire a spawning position instead of spawning them from the tank’s center. So we will put this empty GameObject at the barrel of the tank’s gun so there is some distance from the tank.


### Tank.cs Class

We also need to give this tank its own class so create a new C# script called Tank.cs and add it to the tank.

### Tank Prefabs

Our tank object is now all setup. The only thing left to do is to create four prefabs for each colour of tank and for each prefab add the correct sprite. Then rename your tank-prefabs to match the colours.

The tank object is now setup and ready. We will move onto the Shell object.

## Tank Shells

These are the objects that are being fired by the tanks. You can call them shells or bullets or whatever you prefer, the important thing is that these objects are a simple sprite with a small box-collider and a rigidbody.
And we want these objects to bounce of the walls as they do in Atari’s TANK! In order to achieve this behavior we will create a physics-material and apply this to the rigidbody.

### Shell Sprite

To begin with create a new Sprite and name it ‘Shell’. For this game-example I used one of the assets that your project will already comes with for the shell-texture. I used the ‘UISprite’ texture. This texture suits the look of our shell without needing to bring in additional assets, but feel free to change the sprite if you wish.
Play around with the shell size compared to the tank’s gun until it looks right.

### Shell Layer and Tag

If you remember when we setup the tank, we gave it a sorting layer. Now we will do the same for this shell. We will also need to tag this shell, ‘Shell’. We will use the tags to detect collisions between the tank and shells.

### Box-Colloder and Rigidbody

Next we will need a BoxCollider2D component and a Rigidbody2D component. Again, as with the tank, the rigidbody will have a gravity-scale of zero, but other than that you don’t need to change any attributes.

### Bouncy Material

In order to give the shell the ability to bounce off walls we will need to create a new physics material.
To do this right-click in the project tab and select Create -> Physics2D Material.
I’ve called this material Shell_PhysMat. Select this material and set the Friction to 0 and the Bounciness to 1.
And finally, add this material to the material field of the shell’s box-collider.

### The Shell.cs Script

We also need to add a script to the shell object so that we can control it. I have called this script ‘Shell.cs’.

### The Shell Prefab

The last thing we need to do is create a prefab from this shell so that we can have a reference to it we will use later for creating new shells.

## Setting Up the Game Controller

The game-controller script is the most important part of this game-scene. In this script we will setup our level and load all the player tanks to the right positions and give them the right attributes.
It will also receive all the packet information from the GameSparksManager.cs and send it on to update the opponent’s shells and tanks. It is responsible for making sure all the opponent information is in sync with the instance of the game you are running.
To begin with we will go through setting up the GameController.cs class, and then later we will re-visit this class so we can get our tanks spawned into the scene.
The first things you need to do is create a new script called GameController.cs and add it to the ‘Game Controller’ object in your scene’s hierarchy.

### GameController Singleton

For this example we are going to create a singleton for our GameController.cs script. This is going to be very simple example where we just setup a getter for the singleton and return it in a static method.

Note

If you are averse to using singletons then feel free to restructure this class. However, a reference to the game-controller will be needed by the tank class to reward points, and by the GameSparksManager class to be able to send the right packets to the game-controller.


### Object Lists

After the singleton, all class remembers we need to setup the game-controller are actually arrays of either game-objects or text-fields for our HUD so I will go through them one-by-one.

public GameObject[] tankPefabs
We’ll load each tank-prefab into the script through the editor. This will then be used to assign colours to each player.

private Tank[] playerTanksList
Each time we create a new tank for the player and set it up, we will add it to this list. Later we will use this list to update tank positions and rotations and make sure each player has been assigned the right points. We will also create a getter for this list so we can access it from other classes.

public Text[] playerKillsHUDList, playerNamesHudList
These represent the player_score and player_names text-fields in the HUD panel. We will add these manually through the editor to make sure that the order of players in the HUD appears the same for each player.

private static Shell[] shellPool = new Shell[13]	This is the object pool for all the shells our players can instantiate from. Instead of creating new shell we will replace objects in this pool thereby reducing overheads for instantiation and garbage collection.
For this example I’ve decided on 13 shells in the pool. This is calculated from the fire rate of 1 shell per second, and each shell has a lifetime of two seconds. So each player can have a total of 2 shells in the scene at any time, with a slight possibility of an extra shell (if the fire-rate overlaps). So with 4 players there can be a total 12 shells in the scene at any time (plus one extra for safety).






Once you have built the script, head back into Unity and link all of these arrays with the correct objects in the scene hierarchy.


### Handling Packets

After the initial setup (which we will get to layer) the GameController.cs class handles all the different kinds of packets relating to game-data that are received.
We need to setup our GameSparksManager to pass these packets on, but before we do that, we need to create these methods.
public void UpdateOpponentTanks(RTPacket_packet)

This will handle data coming from packets sent only by opponent tanks. It will update the position and rotation of the tank.

public void InstantiateOpponentShells(RTPacket_packet)
When a player fires a shell, they will send off a packet to all players telling them they should instantiate a shell with their ID. This method will create that shell and assign values of the owner to the new shell.

public void UpdateOpponentShells(RTPacket_packet)
This method will handle updating that information for opponent shells.

public void RegisterOpponentCollision(RTPacket_packet)
When your tank is hit by an enemy shell, you will need to broadcast a message to all other players to tell them to reset your tank, clear the shell that hit you and update the score of the opponent who’s shell hit you.

public void OnOpponentDisconnected(int _peerId)
When a player disconnects we will disable their colliders and turn the sprite black. This will convey to other players that they have dropped out._


### Hooking Up these Methods to GamesSparksManager.cs

So the next thing we need to do is pass on all the packets to these methods. We are going to do this in our GameSparksManager.cs class, and specifically in the OnPacketReceived() method where we had our chat manager setup.
In this method we are going to add 4 more cases for the op-code of the packet, each passing back the packet corresponding to that op-code (see code below).
It is important that you match the op-code with the correct method as in the code below as not all of these packets will contain the same information.


### Setting Up the Tank Object

Before we can setup the game-scene we have to make a detour to the Tank.cs class. Here we are going to create an empty method, which we will finish setting up the GameController.cs class in the next section.
To setup the tank we will need three attributes, which will be stored by each player’s tank…
1.	The Spawn-position of the tank
2.	Whether or not this tank is the player or not
3.	A reference to the player’s score text-field




For the moment we will not do anything in this method until we are sure that we are passing the right values in.

### GameController.cs Start() Method

I am going to setup the scene in the Start() method of the GameController.cs class.
Our setup will have the following steps…
1.	Create our shell-pool by instantiating the shell-prefab.
2.	Getting a reference to all the spawners in our scene.
3.	Create a new tank object from the prefab.
4.	Pass in the correct variables to setup the tank.
5.	Add the new tank to its place in the tank-list array.
6.	Set the corresponding player-name in the HUD to be the player we just created.
7.	Clean up any unused players in the HUD by setting the names and scores to be empty strings.

### Instantiating the Shell Pool

Instantiating the shell-pool is simple. We just iterate through the number of objects in the pool and create a new shell-prefab each time. We then set the parent of the shell to be an empty GameObject (just to make our scene appear neater) and immediately disable the object so the shell’s script cannot run (remember our shells will have a lifetime of 2 seconds, so we don’t want the timer to start until they have been fired).
Before creating any code create an empty GameObject in your ‘Game Controller’ object called ‘Shell Pool’.



### Get Spawners

Now we will get all the spawners in the using the FindObjectsOfType() method. This will get any objects which have the Spawner.cs class attached. Since we may not always have 4 spawners in our scene it is important to let the game collect this data using the existing API calls if possible rather than setting the spawners through the editor.

### Set Up each of the Player Tanks

This section itself is going to have several steps, so we will go through these steps now…
1.	Initialize the playerTanksList array with the number of players there are in the session.
2.	We will then start to loop through the player list.
3.	Inside the player-list loop we will start to loop through the spawner-list.
4.	We will check that the player’s peerId corresponds to the spawner you have set for that player.
5.	Instantiate a new tank GameObject using the prefab at the same index as the current player in the loop (this will be the same for every user so all the coloured tanks will correspond to the same players in each instance of the game).
6.	Set the name of the tank to be the player’s peerId. We will use this to find matching tanks from received packet data later on using the packet’s SenderId.
7.	Check to see if the player in the loop is the current player (i.e. the peerId of this player matches the peerId of the player we are at in the loop). Using this info we can setup the tank as a player or opponent.
8.	Add the newly created tank to the corresponding reference in the playerTankList.
9.	Set the display name of the player to the text-field in the HUD.


So this code uses the indexes of the player list to set the correct HUD components. This is because we know that the order of the player-list for everyone running the game is the same, so using that as a constant we know that each tank will have the right colour, and each player’s HUD will be correct in each instance.

### Clearing HUD Elements for Players not in the Session

This game-example is setup for 4 players, but if there are not 4 players connected we want to clear the HUD elements for the missing players. To do this we just loop through the HUD elements starting at the index corresponding to the number of players in the scene and setting each element to be an empty string.

Note

You could skip this step by having the HUD appear clear when the level starts, though this would make it harder to setup the HUD in the first place. The choice is yours.

### Testing

Once you have all the setup code in place, and all your prefabs and object-arrays are linked through the editor, we can test out the code. If everything is setup correctly you will see 4 tanks of different colours appear at the spawn-points for each of your game instances. You should also see that the position of each colour of tank is the same for each game.


## Tank.cs Setup

The next thing we are going to focus on is the tank class.
We want to be able to move the tank as well as broadcast that movement. We want to be able to fire shell, and we want to be able to detect collisions and broadcast those collisions to our opponents.
Those are the basics we want the tank class to do but there are a number of others we should think about just to make this a more complete game.

Player’s Firing Rate
We don’t want the player to fire every time they press a button. Firstly this makes the game very hectic and unbalanced but it will also cause a bottleneck of packets arriving with shell updates which will slow the game down.

Reset Players Position On Collision
When a player gets hit we want to reset their position back to the original spawn-point. These is so that opponents cannot camp out in one spot and continually attack the player.

Temporary Invincibility For Reset Players
There is a caveat to the previous point, which is that an opponent can camp at the player’s spawn-points and just keep hitting them. They will re-spawn in the same position, so as long as the opponent is aimed at that point they can continue to kill the player tank. So to combat this we will add a 4 second invincibility to the player.

Update Player Score
We also want to be able to update a player’s score when they kill an opponent’ tank.



### Tank Class Variables

Each of the points we just discussed will require variables in our tank class. We will group these variables to the specific functions they are used for.

#### Spawning and Movement

For this we need a reference to the spawn-position as well as float for speed and rotation of the tank. We also need a bool to tell if this tank is the player’s tank. You will remember in the GameController.cs setup we passed this bool into the SetupTank() method.

#### Firing Shells

For this we are going to need a bool to tell us whether or not we can fire, as well as a float for the fire-rate. We will also need a reference to that shell-spawn game-object we added to tank, and finally we will need a public Color variable.
The colour variable is going to be used to apply player colours to the shells so opponents can tell the difference between their own shells and their opponent’s. We will set this on each prefab from the editor.

#### Player Invincibility

For this we only need two things: a bool, which will tell when we are invincible, and will also dictate to opponent if their version of our tank can be hit.

I have set the invincibility to 4 seconds because my tanks move pretty slowly but feel free to set it to whatever value you wish.

### Player Score

And finally we need an integer for the player score and we need a reference to the player score in the HUD and this will be a Text object.

All together these variables are as follows…




### SetupTank() method

Setting up the tank is pretty straightforward. We just need to assign those few values we passed in earlier.


### Tank Movement

So now that our tank is setup its time we started having it actually do something. Our movement is going to be very simple and we are going to take advantage of Unity’s input-axis controls so we don’t have to code result for each button-press.
For input-axis we can get a simulated joy-stick reading for WASD or the arrow keys, along with analog axis from a game-pad or controller. Using the vertical axis for forward/back movement and the horizontal for rotation.
This of course will only occur for our player tank, so all this code will go inside an if-statement to check if this tank is the player tank. And all of this will go in the Update() method.


We also want to send our tank’s position an rotation, and we will do this the way we did for the chat-messages in the last tutorial only instead of sending strings we are sending a Vector2 for our position and a float for our rotation.
We are going to send this data as UNRELIABLE_SEQUENCED. If you remember from the last tutorial, this will send the packet using the UDP protocol, which is faster than TCP though more unreliable. Furthermore, these UDP packets will be sequenced so that if a packet arrives out or order it will drop the old packet for the newer.
This is important for sending positions, as we don’t want an older position to be updated over a more recent one.



Note

I am sending the z-angle of the Euler-angles of my tank’s transform. Since this is a 2D object, I don’t need to worry about Quaternions, but I also don’t need to worry about my Vector3 Euler-angles either. My tank can only rotate on one axis, so I only send one float.

Wherever possible try to consider attributes that will be empty or zero and try not to send them. This will keep the packet small and prevent bottlenecks.

There is something I should point out at this time because it is optional for you and how you want you game to work.
When a shell hits our tank, it will give our player tank some force, and hence move it a little. This will mean we need to broadcast that change in position too, and since this cant happen without the player touching the controls we need to have a check to see if the position have changed.


### Controlling the Rigidbody

We are almost finished with our tank-movement code but there is one last thing to do. Our tank’s rigidbody will allow us to detect collisions with the shells, and stop us driving over obstacles. However, it will also pick up velocity from the shells and from enemy tanks. We don’t want this behavior, as it will send our tank out of control.
So instead, at the end of the update we will cancel all velocity our rigidbody has acquired. This will allow us to still keep the benefits of the rigidbody but we will be in complete control over our movement.


### Testing Tank Movement

So now we should be able move our player tank. But before we do that we also want to check that our opponents received our movement updates. You can test this very simply by adding a Debug.Log() to the UpdateOpponentTanks() method of your GameController.cs class. This log will just print out the whole packet to a string.




We can now build the game and test it out. You will be able to move your tank around the scene. While controlling the opponent, you will notice the logs being printed to your editor console.

Tip

If you want to check the packets being received by opponents you can also do this with a Debug.Log(). With your game set to be a development build, you can print Debug.LogError() to a small console that will appear your game.

### Updating Tank Positions

Now we know that our opponents are receiving our tank-data, we need to get them to update our tank in their versions of the game.
We know we have the position and rotation in the packet, but we also have another piece of info, which can be really useful to us: the SenderId.
The SenderID corresponds to the peerId of the player who sent the packet, and we used the peerId to setup our scene in the GameController.cs class. This means that we can check the tank with the same name as the SenderID and update only that tank. This is another handy tip to make sure your players are synced correctly, and also to keep you packets a little smaller.
The following code will go in the UpdateOpponentTanks() method of your GameController.cs class…


### Testing Opponent Movement

This is all we need to now test the movement of our opponents are being updated.



## The Shell.cs Class

Before we start programming our tanks to start firing shells, we need some to add some details to the Shell.cs script so that we can get some details from it during instantiation and we so that can set the lifetime of the shell so that it will disappear after a set amount of time.
Firstly, our variables are going to be two doubles, for the lifetime of the shell, and the countdown-timer. I’ve set the lifetime to 2 seconds, but you can set this to whatever you like. We are also going to assign ownership to the shell so we can identify who fired it. So we will have an int for this, and a method to check that int.


And next we will create an countdown-timer which will countdown the lifetime and once the time is out we will disable the game-object and reset the timer.



## Firing Shells

Firing shells in this example is actually somewhat complicated. Because we are using an object-pool instead of just instantiating a new shell when we fire, we must grab an inactive object, reset all its attributes and assign it’s position, rotation, etc., and then activate it again.
On top of that we have to implement a firing rate which we do using a Coroutine. To begin with we will create an IEnumerator method which we will call from the Update() method when the space-bar is pressed. We will put this inside the if-statement where we check the player.

And in the Update() method…



You should now be able to test your firing rate in the game. If you want to tweak it you can change the fireRatePerSecond variable.

### Instantiating Shells

Where we put the debug-log for firing shells we will now call another method for instantiating shells. It’s actually not accurate to say we are instantiating shells, as the objects all already exist since we setup the scene.  Really we are just resetting them and the enabling them again.
When we want a shell, we first have to check for an inactive shell in the pool. We then claim that shell, give it a new ID and reset its position, rotation, owner, etc.  We then add force to the shell to move it. There is an important part to this method though; It is not only going to be used to fire shells, but in our FireShell() method we will send off a packet telling the other players that they should recreate the shell we are about to fire. When they receive that packet they will also use this method to recreate the shell on their side.
This method will therefore need the ID of the sender and the UID of the shell. In this example I will be using the Guid class to generate a unique id for each shell.
So the FireShell() method becomes…






#### Resetting Shells

Now we need to create the ResetShells() method in the Shell.cs class. This method is straight-forward, we just assign the variables we passed in through the InstantiateShells() method. There are two additions however, we enable the game-object, and we reset the lifetime-counter.

### Instantiating Shells for Opponents

Instantiating shells on the opponents end is actually very easy because we can use the SenderID of the packet to check which tank should instantiate the shell. We will then pass in the SenderID and the UID we sent when we created the shell to make sure the shells match.
This code goes in the InstantiateOpponentShells() method of the GameController.cs class…



### Testing

You should now be able to test your game and see the shell being instantiated. For your player you will see the shells being created, moving and bouncing off walls however we still need to write some update code for our shells to move in the opponent’s game.

## Sending Object-Details in Batches

The next thing we want to do is send off position and rotation updates for every shell that we fire. In this example each player is responsible for sending updates about their own shells, so even though we have a pool of 13 shells, we wont have to send on information about every single shell, only the ones we fired and the ones that are currently active.
We don’t want to send off a packet for each shell while we are in the loop, so instead we will create a list of RTData, and grab the details for each shell we need to update. We are also going to use a counter to check when we have a shell to send. We don’t want the packet being sent when there is nothing to send.
This process will happen in an update loop, as we want to send these positions as soon as possible to that our opponents don’t perceive lag on their end.
Predictive Movement

Lag is unfortunately unavoidable when it comes to multiplayer networking. So instead of relying on only the updates coming in from opponents, what most multiplayer games will do is to employ some kind of predictive movement or dead reckoning so that the objects in their games don’t appear to jitter if the connection is slow.

Dead reckoning is the process of using known information about the position, direction and velocity of an object to predict where it should be. The prediction is used to move the object to the predicted point while waiting for the next update to come in, at which point the position of the object is either set to the correct point, or the object is lerped towards the correct point.

In this example we are not going to employing any predictive movement, as we just want to show how the data can be used for updating game-objects. So please keep in mind that if you are experiencing lag or jitter, implementing some dead-reckoning to your physics objects is the conventional solution to this.

First we collect the information about each shell in the RTData list…

And then we check that we have enough shells to send a packet with, and we loop through the list and set our RTData from the list with the right keys.


### Receiving Shell Details

In order to get the right data out of the packet our opponent receives we will need a nested for-loop. One to go through the RTData we sent in the packet and another to find the corresponding shell in the shell-pool,


### Testing Shell Updates

This should be all you need for your shells to send and receive updates. Now, the shells that we instantiated in the last section will receive updates from their owners.

## Registering Collisions

Registering collisions is very simple using Unity3D, however when it comes to multiplayer programming it can get quite complicated. There are a few things to consider when we are talking about collisions in a networked system.
One thing to think about is who registers the collision? All players have an instance of each other’s tanks in their own game.
If a shell from player1 hits player2, should player1 register the collision and broadcast that to player2? What if the shell was a little late and in player2’s game they never saw that they got hit? The game would appear very unfair.
The solution to this is to only let each player register collisions on their own tank and only they broadcast the collision to the opponents. This is a good solution. We still have the same problem with shell being out of sync, but at least the player who gets hit will always see the shell that hit them.
So lets go through each step we are going to implement…
1.	We will setup our OnCollisionEnter2D method, which will register collisions.
2.	We will check that the object that hit us was tagged ‘Shell’.
3.	We will then check if the tank is the player, and if so, we will broadcast a packet with the tank name (my peerId), the shell name, and the shell’s owner name to all other players.
4.	An important thing to check is if our own shell hit us, we don’t need to broadcast everything, as we can’t get hit by our own shells.
So in this case we only need to send the name of the shell that hit us, so our opponents can remove it from the scene.
5.	We will check that the opponents received that packet.


Notice that when the shell hits the player it will remove it automatically by setting it to be disabled.
The next thing we need to do is make sure we are getting the right data received by our opponents so for now I am going to put in debug-logs to make sure we are getting the right info back, but just for testing we are going to remove the shells that come back so we can test out how the collisions feels in our game.
The following code goes in the RegisterOpponentCollision() method…




### Testing our Collision Code

Now that we are sending and receiving some collision info we can start testing it. When you run the game you should get the messages for when one of your own shells hits you as well as when an opponent hits you.

### Resetting Tanks and Updating Scores

Now we have collisions registering properly, its time to start making this into a game by having our tanks scoring points and resetting their positions.
The code for this is very easy; as we already have all the logic we need setup. When our tank registers a hit form a shell that is not ours (we have this already code) we reset our tank’s position. We are already broadcasting our tank’s name and the name of the owner of the shell that hit us, so on our opponent’s end we can reset the tank and update the score easily.




We then add calls to these methods after we set the name of our tank and the opponent’s. However, when we register a collision, we are not the one who deserves to get the score. So we need to find the owner of the shell and update their score instead.

### Resetting Tanks and Updating Scores Opponent-Side

We already know that our opponents are receiving the right data so all we have to do is loop through the tank-list and reset the tank that was hit and update the score of the other tank.


### Testing Updates and Scores

You should now have everything you need to test out your game. Your tanks should reset positions back to the spawn-point when hit and the score of the opponent who hit you should get updated.

## Invincibility

The last part of this tutorial will be to add invincibility to our tank when it gets reset. For this we will use the isInvincible bool.
We will then check if the bool is true in the update loop and then preform a colour-lerp on the tank’s sprite-renderer using a Sine function to flash the tank red/white over time.
We ware going to use an IEnumerator so we can set the time for the invincibility. All this method will do is set the isInvincible bool to true at the start, wait a few seconds and then set it false. It will also set the colour of the tank’s SpriteRenderer to white again to make sure the colour is right.


And the follow code goes in the Update() method, outside the if-statement that checks the player…



Then we call the SetPlayerInvincible() method from the ResetTank() method.

And finally, we need to actually make the tank invincible, and we’ll do this in the OnCollisionEnter2D method where we check if the tank is the player.

You should now be able to test your game. Your tank will begin flashing for 4 seconds when it is hit, during which time it cannot be hit again and will absorb all shells that hit it.

## Getting Around Latency Issues

There is always going to be a delay inherent in any multiplayer networking game. It is unavoidable even in the fastest systems. Our invincibility highlights a common problem that latency creates.
Lets assume the following situation…
1.	Player1 sends a message to Player2 telling them they are invincible now. At the same time Player1 starts their invincibility timer.
2.	Player2 receives the message and sets the invincibility timer of Player1’s tank in their own game. Only it took some time (say 20-40ms) for Player2 to receive that packet.
3.	Player1’s invincibility timer ends after 4 seconds.
4.	Player2’s version of Player1’s invincibility timer therefore ends 4 seconds + a delay of 20-40ms.
You can already guess the problem here. One player gets hit by a shell and is invincible, but the player who hit them sees them as normal because the timers are out of sync.
There are a few solutions to this problem; one is to use a slightly shorter invincibility time for the opponent than we use on our tank, and another more accurate way is to subtract the exact travel time of the packet from Player1 to Player2 from the invincibility time. However, we will not be dealing with lag in this tutorial so we will move on.
So, for example we would use the following change to the ResetTank() class…


## Showing Players Have Disconnected

The last thing we need to do is add something to show when a player has been disconnected or left the game. For this example we are just going to set their sprite to be totally black and to make sure they cannot be interacted with.
We will set their BoxCollider2D component to be a trigger (we could destroy the tank, thus removing it form the scene completely, but you may want to give the player the ability to come back into the game if possible).
This will go into the OnOpponentDisconnected() method of the GameController.cs class…
