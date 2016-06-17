---
src: /Tutorials/Realtime Services/Implementing Realtime Chat Services.md
---

# Implementing Realtime Chat Services


In the last tutorial we looked at how we can setup real-time sessions as well as the matchmaking request used to find players for your real-time sessions. In this tutorial we will start some real-time programming to implement a peer-to-peer chat system. This will be done as an introduction to sending/receiving real-time packets before we get onto multiplayer network programming in the next tutorial.

## INTRODUCTION

So for this tutorial we will be focusing on building a very simple chat system. The chat dialogue will be toggled using a button in our game-scene and from there you will have the option to send messages to everyone, or to a selected player.

## CHAT MANAGER LAYOUT

We are going to keep this chat manager simple in this tutorial, but where possible we will point out where this chat manager can be expanded upon and how to do so.
The layout of this chat manager will be simple. It will have 3 windows we will be focusing on…
•	The Chat Window Toggle Button: For turning the chat window on and off.
•	The Chat-Log Panel: This is where all the chat history will be displayed.
•	The Message-Input Panel: This is where the user will be able to create the messages they want to send, as well choose who they want to send messages too.
We will be creating these element using the out-of-the-box Unity UI elements.

### THE CHAT TOGGLE BUTTON

We will start with the simplest of these panels; in your main-game scene, please create a new Canvas UI element. In my example I called this ‘Main Canvas’.
We will create an empty GameObject for all the chat-windows and call it ‘Chat Manager’. I then created a new Panel and named that ‘ToggleChatPanel’, and added a button to that panel.
I’m positioning this panel at the button in the bottom corner of the screen so that it will interfere with gameplay as little as possible.

Note

For the toggle-button and the chat-windows we will be creating separate objects in this canvas. This is because in the next tutorial we will be using the same canvas to draw the scores HUD for each player.

### THE CHAT LOG WINDOW

The chat log window is going to very simple for this example. We are going to create a panel, and a text-field. All chat-logs are going to be put into a queue, so that the text-field cannot contain more text then the size of the panel.
To begin with we will create another new empty GameObject called ‘Chat Window’, which will be where our chat window panel and text-field will go. I have docked this panel to the right-hand-side of the screen above the toggle-button, but I have left room for the message-window at the bottom. Don’t worry about the size of the space; you can adjust your windows later.


Note
Another way of doing this could be with a ScrollView object and a text-field in the content area with a content-fitter element. This would allow you to scroll through your chat-history and fit more chat-logs in the window. However, to keep this example brief I have chosen not to use a scrolling chat window.

### THE MESSAGE-INPUT WINDOW

There are three elements that are going to make up the message-input panel…
Input-Field
This will be where the user types out the message. I am putting a character limit of 75 on this field so that a decent amount of messages can be displayed here without the text-field cutting text off from view. You can play around with font sizes and character limit of you like. I am using the default font size.

Send Button
We will add an OnClick-listener to this button, which will check which player is selected and then send the message to them.

Dropdown Selector
We will use a drop-down selector so that we can choose what player to send the messages to.


These elements are laid out as in the image below…

The drop-down menu object will automatically fill in three options when it is created. For this example we only need one option right now, which I have called ‘To All’. Later, in our ChatManager.cs script we will programmatically add other players to the drop-down menu options.
THE CHATMANAGER SCRIPT
Now we will create a new class called ChatManager.cs and add this class to the Chat Manager empty game-object we created earlier.
The first thing we will do is setup the toggle-button so that we can show/hide the chat-manager window. So, in the ChatManager.cs script we will add a public variable for the button, and a public variable for the chat-window GameObject. We will also need a bool to toggle the window on and off. Once you have linked these variables to the objects in the editor we can start coding the toggle button.

In the Start() method we will disable the chat window, so that when the game loads, the chat window will automatically disappear. We will then add a OnClick listener to the chatToggleBttn variable. This will be linked to a method I called ‘ToggleChatWindow’.
This method is pretty simple. It simply toggles the isChatWindowOpen bool, checks if the bool is true, then enables the window, or disables it. This method will also change the text-element of the button, so that the button has a different message when the chat window is shown and when it is hidden.


Now that we have the toggle-button hooked up we will need a few more variables so that we can continue onto the next section and start sending and receiving messages. We are going to need the following public variables.
InputField, messageInput
We will use this to get the text the user has input that they want to send.

Dropdown, recipientOption
When we link this to the drop-down menu in the editor we will be able to add options to it, as well as check the ID of the recipient before sending the message.

Button,  sendMessageBttn
We will add a listener to this button, which will be used to decide who the message should be sent to.

Text,  chatLogOutput
As we send and receive new messages we will print them out to this text-field.

Int,   elementsInChatLog

We’ll use this public variable to tweak the number of chat-messages that stay in the log before begin replaced by new ones.  


There is one last variable we need to create before we can start and that is the chat-log itself.
For this I am using the Queue class, as it allows new messages to be added to a collection in the order we would expect from the chat-log (i.e. last-message at the bottom) without extra programming.



The ChatManager.cs script is going to be pretty small, so this is all we need. Once you have linked these public variables to the objects in your editor we are good to go.
SETTING UP THE DROPDOWN MENU
The next step before we start sending messages is to setup the rest of the drop-down menu details.
Currently, we only have the option ‘To All’ in the drop-down menu, but we want to add an option there for each player (excluding ourselves). The code for this is simple, we just need to loop through the player/participants list we created in the GameSparksManager.cs script in the RTSessionInfo variable we created and add an option for each player in that list that isn’t us. We’ll put this code in the Start() method.


SEND-MESSAGE BUTTON LISTENER
While we are working in the Start() method lets finish up here and create a listener for the send- message button. What I am also going to do is make sure the chatLogOutput text-field is empty when the level is loaded so that any debug-text we might put there is cleared.
The Start() method now looks as follows…




We are now all-set to start sending our messages.
SENDING REAL-TIME DATA
Once you have your real-time session instance setup you are ready to start sending real-time data. There are two types of data you can send using our real-time services; structured and unstructured.
STRUCTURED DATA
Structured data is created using the RTData class. This is a class that allows you add some basic data-types to the RTData object you want to send. When using the RTData class to add these different data-types you are also required to denote a ‘key’ for each type you wish to add. This key is used to retrieve the correct data-type at each index when the packet is received.
Below is a list of the kind of data you can add using the RTData class.
Data-Type	API	Description
int	.SetInt(index, integer);	This allows you to send a 32-bit integer.
float	.SetFloat(index, float);	This allows you to send a 32-bit floating-point number with 7 digits of precision.
double	.SetDouble(index, double);	This allows you to send a 64-bit floating-point number with 16 digits of precision.
long	.SetLong(index, long);	This allows you to send a 64-bit integer.
string	.SetString(index, string);	This allows you to send a string of characters.
Vector2	.SetVector2(index, new Vector2(x, y));	This allows you to set a Unity Vector2 type which takes two floats for x and y. This can be used to send angles or 2-dimentional coordinates.
Vector3	.SetVector3(index, new Vector3(x, y, z, w));	This allows you to set a Unity Vector3 type which takes three floats for x, y, z. This can be used to send transform elements such as position, scale and Euler-rotation.
Vector4	.SetVector4(index, new Vector4(x, y, z, w));	This allows you to set a Unity Vector4 type which takes four floats for x, y, z and w. This can be used to send Quaternions or colours.
RTVector	.SetRTVector(index, new RTVector(x, y, z, w));	The RTVector class accepts floats for x, y, z and w. The difference between this type and other Vector types is that RTVector can accept any or all of these floats.
RTData	.SetData(index, RTData.Get().SetInt(index, 1));	Using the RTData class you can create nested data from without your initial RTData structure.
For all RTData we are sending we want to use the one instance of the RTData object rather than creating and new instance each time.  RTData is a disposable object too, so when using it, we wrap the instance in a ‘using’ statement to make sure is it returned to the pool.
Constructing RTData therefore looks as follows…



SENDING STRUCTURED DATA
In order to send your RTData you will need a reference to the gameSparksRTUnity object you used to configure you real-time session.
The method to send structured data is gameSparksRTUnity.SendData() and it takes the following parameters.
Parameter Name	Type	Description
opCode	uint	Each packet you send to the server has a corresponding opCode. This opCode is available when the packet is received by the other player(s). This must be a non negative integer
deliveryIntent	GameSparksRT.DeliveryIntent	There are 3 options when sending a packet to the session
RELIABLE – The packet will be queued, sent and received by the target players. The packets will be received in the order they are sent.
UNRELIABLE – The packet will be sent with no guarantees of it being received. The receivers may get the packets in a different order than they are sent
UNRELIABLE_SEQUENCED – The packet will be sent no guarantees of it being received. If it is received out of order it will be discarded
structuredData	RTData 	This is a structured dictionary indexed with integers that can contain doubles, floats, ints, longs, strings or nested RTData objects
targetPlayers	Params int[] (optional)	The peerId’s of the players you want to send to. If omitted the packet is broadcast to all others players in the session
So, leading from the previous RTData example, sending this data would look as follows…




RTData Size
The SendXXXX methods are also setup to return information about the size of the packet your are sending. They will return an int which corresponds to the size of the packet in bytes.

And that’s it. You can mix and match this setup using the RTData class to send whatever structures for your data you like.
SENDING UNSTRUCTURED DATA
When we talk about sending unstructured a data we mean that instead of using the RTData class we create a byte-array out of the data we want to send.
In this example we will be converting a string to a byte-array and sending that.
Unstructured data is actually of type ArraySegment instead of byte[], so any byte arrays will have to be converted before sending them. The reason behind this is because ArraySegment is a struct and so we will conserve memory by having it allocated on the stack.
It is advised to use the same ArraySegment variable for sending all data and have different sets of byte arrays converted to array segments before sending them.



All data, be it structured or unstructured, is send as a byte array in the end. The advantage of sending byte arrays over structured data is that there is no extra space used in the packet to give each of the elements their keys as there is when using RTData.
SENDING CHAT MESSAGES
For this tutorial we are only going to be sending two strings; the message the user entered and the time-stamp for when it was sent.
So in our SendMessage() method we will…
1.	First check to make sure there is a message to send, as we don’t want to send an empty string to players if the user hit the send-button by accident.
2.	Construct the RTData object with the message and the date.
3.	Check to see if the ‘To All’ option is set, or if there is a specific player set to be the recipient of the message.
4.	If the recipient option is set to ‘To All’, then send the data as-is.
5.	If another player is set to be the recipient then loop through the player/participant list and check the corresponding display-name. Then send the data to that player’s peer ID.
Note that we use the DeliverIntent.Reliable for this message because we want the packet to arrive in order and intact.




This is a good time to save your scene and load-up the lobby-scene again. We should test the drop-down menu is creating options for the right players and that our messages are being sent properly.
If configured correctly, you should see an option for each player except yourself in the drop-down menu. You will also see the correct message in the console for when you send to another player or to all players.

RECEIVING REAL-TIME DATA
In order to receive your RTData you will need a reference to the gameSparksRTUnity object you used to configure you real-time session.
When any packets are received the OnPacketRecieved callback will be called and the details of that packet can be processed.


The RTPacket class contains the following members…
Parameter	Type	Description
OpCode	int	The opCode set by the sending player
Sender	int	The peerId of the sender
Data	RTData	The RTData object sent
Stream	Stream	A Stream object that represents the unstructuredData sent
StreamLength	int	The number of bytes in the stream
PacketSize	int	The size of the RTData attribute of the packet in bytes.
RECEIVING STRUCTURED DATA
Any structured data in the packet received is available in the Data parameter. Consult the previous section on Sending Real-Time Data to see what kinds of data-types can be sent. I will be using the example from that section to show how data can be parsed back.





RECEIVING UNSTRUCTURED DATA
Unstructured data is accessible through the Stream parameter of the RTPacket received. In the sending unstructured data example, you can get the data back into a string using a StreamReader class.


RECEIVING CHAT MESSAGES
In order to receive the chat message we will first have to put a reference to the ChatManager.cs class in our GameSparksManager.cs script.



Now, in the OnPacketReceived() method we created when we setup the real-time session instance we will check that the op-code corresponds to the op-code we have chosen for all chat-messages (op-code 1).
We will also have to check to see if the ChatManager reference is initialized yet, and if it is not we will find the ‘Chat Manager’ object and give it that reference. We are then going to send the packet to an OnMessageReceived() method in the ChatManager.cs class.



Then, back in the ChatManager.cs class we can add that new method. We will put a Debug.Log call in this method for the moment, which will print out the message that has just been received while we are testing.

You should now be able to test messages being sent between players and see the received message being printed out in the console.

UPDATING THE CHAT LOG
The next step is to print these messages to the chat-log. We are going to create a method for this called ‘UpdateChatLog’. This method is going to take the name of the sender, the body of the message and the date. It will create a formatted string from this data so that the sender-name and body can be highlighted, and it will add this string to the queue.
We’ll check the length of the queue so that new messages are added and old ones removed, and finally we will print all of these messages to the chatLogOutput text-field.




Now we need to get this information from the OnMessageReceived() method. We can get the date and the message from the packet, but the packet does not contain the player-display name. So we are going to use the Sender parameter of the packet to check the name of the player with the same peerId as the sender.




You should now be able to test sending and receiving chat messages between players.


There is one last thing we need to do however. This chat-system does not show the player sending the data what they have just said. In order to fix this we can add a line to that start of the SendMessage() method…

This should be put below where we set the RTData for the message and date, and above where we clear the messageInput text-field.

You now have all the elements you need for this chat service to work. Test it out with as many players as you want by changing the number of players in your have through the game-portal.
