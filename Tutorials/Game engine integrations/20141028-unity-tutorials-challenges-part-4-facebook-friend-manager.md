# Unity Tutorials – Challenges – Part 4: Facebook Friend Manager

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 4 of an 8 part tutorial, it's recommended that you look at the previous section before continuing. In this part we are going to write the code for our Facebook friend manager. This will let us see what friends we have that are playing the game and will be necessary for choosing who we want to challenge. It will also show which friends are online by displaying them in game with their profile picture and an online/offline status indicator.

* * *

##

## Write the FriendEntry Script

First we need to write a script that will be used to update the GUI elements that hold our friends profile picture, name and online status. In our Tic Tac Toe project we have a panel that we use to display this in game. You can find it in the project under Assets>Resources>Prefabs>Friend. Drag it into the scene and you'll see this: ![](https://lh4.googleusercontent.com/WFG5ZjBxb0vlNUSYo7KHAQ_gLAUOibTJy_LmkyZiUoypUIyEkud7eN-7mDyX_xk8xXTOLltJK18sLWmqFbQVl6n_HIrbDJE2mMydWVQj54ok9EijH92OkU23xflkVGLBIQ) This is our Friend prefab that we use. This is also how we will issue challenges in the future, but for now we are just focusing on making a friend list. Create a new C# script named FriendEntry in the Prefabs folder. Again, the code we use is below, read through the comments to understand how it functions. This is not the final version of this script, we will be adding to it in the future after we've done a bit more work setting up our challenges.


    using UnityEngine;
    using System.Collections;
    using System.Collections.Generic;

    public class FriendEntry : MonoBehaviour
    {

    	public string userName, id, facebookId;
    	public bool isOnline;

    	public UILabel nameLabel;
    	public UITexture profilePicture;
    	public UISprite onlineTexture;

    	// Use this for initialization
    	void Start()
    	{
    		//When the object is instantiated, update the GUI variables
    		UpdateFriend();
    	}

    	public void UpdateFriend()
    	{
    		nameLabel.text = userName;
    		onlineTexture.color = isOnline ? Color.green : Color.gray;
    		StartCoroutine(getFBPicture());
    	}

    	public IEnumerator getFBPicture()
    	{
    		//To get our facebook picture we use this address which we pass our facebookId into
    		var www = new WWW("http://graph.facebook.com/" + facebookId + "/picture?width=210&height=210");

    		yield return www;

    		Texture2D tempPic = new Texture2D(25, 25);

    		www.LoadImageIntoTexture(tempPic);
    		profilePicture.mainTexture = tempPic;
    	}

    	//This is the function we call for our UIButton OnClick
    	public void StartChallenge()
    	{
    		//CreateChallengeRequest takes a list of UserIds because you can challenge more than one user at a time
    		List<string> gsId = new List<string>();
    		//Add our friends UserId to the list
    		gsId.Add(id);

    		//Call the ChallengeUser function and pass on the list containing our friends UserId
    		ChallengeManager.instance.ChallengeUser(gsId);
    	}
    }

* * *

##

## Setting up the FriendEntry GUI

First, add the FriendEntry script to the “Friend” prefab by clicking on the “Friend” we dragged into the hierarchy, then drag the script into the inspector panel. Similar to when we created the UserManager in the last part, you will now see three empty fields that need to be linked with Game Objects for the script to update called “Name”, “Profile Picture” and “Online”. ![](https://lh6.googleusercontent.com/naCLn0RwmYjYR_sVQkbQkTGeoeaaU8wjAmm-TvEfbR0c1cjMcei8h8jOpePAcp0LgJtWT_gFS_9ZgKnXrzfwMHMjD2IurSK0oA5TeSWt7J10ZY0l8hRffkFcDGRdNacNgg) Find the necessary objects in the “Friend” prefab in the Hierarchy. Drag “Name” into the name field, “Profile Picture” into the profile picture field and “Online” into the online field. ![](https://lh3.googleusercontent.com/cXBd9WndnL8JRmRsEuQgjnvtutLZVvvsoChYX8JKScQWRs1IPOgqiq1QG7wld4wvMxZzCZVuVvnTLlxnmJgOqbLPlcT69jwz6aWNMVZ2iJ0_U2hIexBPyK4RDt-sYYuExA)![](https://lh5.googleusercontent.com/xVzq_BpJ743GXIAF91IzBV-d-kn2drxiDrKEeAvu_xi01psBH5Xv245tAivZtvjaFvk0Ov2APNYXA_cEvhtjkTdjjzYlaFm62vkFVh3P11av7IvIDCEDNaG06GyYGbP1uw) Then save the prefab by hitting apply and you can remove it from the scene.

* * *

##

## Write the FriendManager Script

Now we can start on our FriendManager script. Start off by creating a new C# script in Unity and call it FriendManager. This will pull in the friend information from Facebook and create a friend list based off those who have played the game. We’ve provided the code we used below, feel free to use it yourself. Have a read through and look at the comments to understand how it functions.


    using UnityEngine;
    using System.Collections;
    using System.Collections.Generic;
    using GameSparks.Api.Requests;

    public class FriendManager : MonoBehaviour
    {

    	public GameObject friendEntryPrefab;

    	public UIGrid friendGrid;

    	public List<GameObject> friends = new List<GameObject>();

    	public void GetFriends()
    	{
    		//Every time we call get friends we'll refresh the list
    		for (int i = 0; i < friends.Count; i++)
    		{
    			//Destroy all friend gameObjects currently in the scene
    			Destroy(friends[i]);
    		}
    		//Clear the list of friends so we don't have null reference errors
    		friends.Clear();

    		//Send a ListGameFriendsRequest, which will get all facebook friends who have played the game
    		new ListGameFriendsRequest().Send((response) =>
    		{
    			//For ever friend stored in our collection of friends
    			foreach (var friend in response.Friends)
    			{
    				//Create a new gameObject, add friendEntryPrefab as a child of the Friend Grid GameObject
    				GameObject go = NGUITools.AddChild(friendGrid.gameObject, friendEntryPrefab);

    				//Update all the gameObject's variables
    				go.GetComponent<FriendEntry>().userName = friend.DisplayName;
    				go.GetComponent<FriendEntry>().id = friend.Id;
    				go.GetComponent<FriendEntry>().isOnline = friend.Online.Value;
