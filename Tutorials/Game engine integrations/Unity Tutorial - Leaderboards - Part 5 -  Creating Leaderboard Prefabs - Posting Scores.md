# Unity Tutorial - Leaderboards - Part 5: Creating Leaderboard Prefabs & Posting Scores

Tutorial - Leaderboards for Unity 3D

  * [1. Introduction](/uncategorized/unity-tutorial-introduction)
  * [2. Configuring GameSparks for Facebook Authentication](/uncategorized/unity-tutorial-configuring-gamesparks-for-facebook-authentication)
  * [3. Logging in to GameSparks with Facebook](/uncategorized/unity-tutorial-logging-in-to-gamesparks-with-facebook)
  * [4. Creating And Testing GameSparks Leaderboards](/uncategorized/unity-tutorial-creating-and-testing-gamesparks-leaderboards)
  * [5. Creating Leaderboard Prefabs & Posting Scores](/uncategorized/unity-tutorial-creating-leaderboard-prefabs-posting-scores)
  * [6. Getting profile pictures for Leaderboard Entries](/uncategorized/unity-tutorial-getting-profile-pictures-for-leaderboard-entries)

This is part  5 of a 6 part tutorial, it's recommended that you look at the previous section before continuing. This tutorial will cover creating our leaderboard entry prefab, our in game leaderboard displayed to the player and writing code to post scores and to retrieve leaderboards from Gamesparks. You might find it helpful to dowload our sample game Tappy Bird and see what we did to implement our in-game leaderboards. To follow the steps and emulate what we did there is also a version of the game for download that does not have any GameSparks features implemented.

* * *

 

### Creating the Leaderboard Header

First thing you’ll need to do is set up a new NGUI Panel to contain the Leaderboard and a Header to show the player what page they are looking at. **1) Creating the Leaderboard Parent** As a child of the UI Root create a new Panel through NGUI>Create>Panel. This parent will contain all the elements of our Leaderboard. **2) Set Leaderboard Header** As a child of the new Leaderboard parent you just created, add a new 2D sprite to contain the Leaderboard Header (NGUI>Create>Unity 2D Sprite). Select button-1 as the sprite and resize it to about 320 x 30. Set Material to “Sprites - Default”. Drag it to the top of your Scene as it’s going to be the title of the leaderboard that displays over the results. Name the new object "Leaderboard Header". ![](https://lh3.googleusercontent.com/kaqxOravUo8XeUPOWDmlG5fDnTbLQa1dSmBoHDqGhAayA5IdwxicWLnPZDnnwBpLbZKs-JaIgqcRKsSrzHuQNt5WgCdZNtju6pUd8MOveaRDlYWwCdZHlZy_gSRE1jA92Q) **3) Set Leaderboard Header Label** In the hierarchy, as a child of the Leaderboard Header add a new Label (NGUI>Create> Label). This is will be the text displayed in the header panel. Set the new label up in the inspector as follows:

  * In the “Text” field type “High Score Leaderboard.”
  * Uncheck “Gradient.”
  * Change the “Effect” menu to “Outline”
![](https://lh4.googleusercontent.com/Wk14iNdjYOFp1sr0VDiLcaMmSrJ1Pch1WDd30ylHGj0smbo9gnR3qxXZ6e3D9IoXcLQpyB_fJT8vq7yOrNHvRI-KhNZEhXntATpRhjIBpc6hOQA0_XQqLBiqwo1oRZjc1w) It should look something like this: ![](http://i.imgur.com/KBAYfu0.png) **4) Create NGUI Grid**

As a child of the overall Leaderboard parent Create an NGUI Grid (NGUI>Create>Grid) This will automatically arrange any entry added to the Leaderboard. Set the Grid arrangement to “Vertical” and the cel height to “40”, on account of our header. This gives each entry some space as it’s auto arranged.

  * Arrangement: vertical
  * Set cell size height: 40
  * Move the grid up so it’s positioned just below the Leaderboard Header

###

* * *

### Create a Leaderboard Entry Prefab

This is a prefab that can be recalled whenever we want to add a new leaderboard entry. It will contain a Unity 2D sprite and three labels that will hold the strings for User Name, User Score and User Rank. Whenever an entry is added to the Leaderboard the information on this Prefab will be updated and a new entry added to the grid. **1) Create a new Unity 2D Sprite** As a child of Grid create a Unity 2D Sprite (NGUI>Create>Unity 2D Sprite). Rename this sprite “Leaderboard Entry” in the Hierarchy.  Set the sprite to “Button - 2”, Material to “Sprites - Default”. Snap it and Resize it to be roughly the same size as the Leaderboard Header: 312 x 28. Make sure it’s positioned correctly, slightly below the Leaderboard Header. ![](https://lh6.googleusercontent.com/elo80fwWSUfv7ftmLrW6wbYFVkX3FjtSxrpWggTE6hx-J7KL_uL1eTXJ4ZGK5rYGlbVET323Jo6ntHGmeWLB2a1NzVw8k7UxhFKQZxnUxfo65iQSnx9u61QvRxwaP00ubA) **2) Set a User Rank Label** As a child of Leaderboard Entry add a label(NGUI>Create>Label). Rename the Label to User Rank. Set it up in the inspector as  follows

  * Enter Text as 1 (Any text entries we add here are just for testing, these test entries will be overridden by our scripts in the future)
  * Turn off  the gradient on the text
  * Give the text an outline
  * Position on left of the Leaderboard Entry Sprite.
**2) Set a Username Label** As child of Leaderboard Entry add a second Label (NGUI>Create>Label). Rename the Label to “User Name”.

  * Enter “Username” in the Text field (again, this entry is just a placeholder to make sure we have configured the prefab correctly)
  * Turn off gradient on the text
  * Give the text an outine
  * Position in center of label
**4) Set a User Score Label** As a child of Leaderboard Entry add a third Label. Rename this label User Score. In the inspector, set it up as follows:

  * Enter 5000 in the text field
  * Turn off gradient on the text
  * Give the text an outline
  * Position to right of leaderboard
**5) Save Leaderboard Entry as a Prefab** Hit apply and drag the Leaderboard Entry Parent from the Hierarchy into your Prefabs folder to save a prefab. We now have a Leaderboard Header set up, and a Leaderboard Entry prefab with entries for Player Rank, Username and Score that can be called and filled with information pulled from GamesSparks.The scene preview should now look something like this: ![](https://lh5.googleusercontent.com/uqyx7GfWg2ltZ4dRSTIGc-YpwdakXNXedpJjeKSmigqGHdnCpOfK2osvrN5zZrombXPb6U43JSvPLit9z8y52HcReosGJdQMY9gwhvDLLTaAwhiJY4B0VPK4LKsWP4LMUQ) Next we will write scripts to allow our Leaderboard to function that will pull information from GameSparks, add it to the Leaderboard Entry panel and update and display the Leaderboard whenever it’s requested. **1) Leaderboard Entry**
