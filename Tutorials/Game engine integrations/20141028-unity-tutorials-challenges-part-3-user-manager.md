# Unity Tutorials – Challenges – Part 3: User Manager

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 3 of an 8 part tutorial, it's recommended that you look at the previous section before continuing. Now we will write our UserManager, which will display our Username and Profile Picture at the top when in game. We will also use the User Manager to store account information, which we will use again when writing the code for our challenges.

* * *

##

## Write the UserManager Script

First, create a new C# Script and name it UserManager. We’ve provided the code we used below, you can use it yourself. Read through the comments to understand the script functions.


    using UnityEngine;
    using System.Collections;
    using GameSparks.Api.Requests;

    public class UserManager : MonoBehaviour
    {

    	public static UserManager instance;

    	//These are the account details we want to pull in
    	public string userName;
    	public string userId;
    	private string facebookId;

    	public UILabel userNameLabel;
    	public UITexture profilePicture;

    	// Use this for initialization
    	void Start()
    	{
    		instance = this;
    	}

    	public void UpdateInformation()
    	{
    		//We send an AccountDetailsRequest
    		new AccountDetailsRequest().Send((response) =>
    		{
    			//We pass the details we want from our response to the function which will update our information
    			UpdateGUI(response.DisplayName, response.UserId, response.ExternalIds.GetString("FB").ToString());
    		});
    	}

    	public void UpdateGUI(string name, string uid, string fbId)
    	{
    		userName = name;
    		userNameLabel.text = userName;
    		userId = uid;
    		facebookId = fbId;
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
    }

Once you've written the code, it’s time to attach it to the GUI.

* * *

 

## Setting up the GUI

Add the UserManager Script to the scene by adding it as a component to the API Manager Game Object. You’ll see that we have an empty UILabel and an empty UITexture. This is where we will display the player name and image. ![](https://lh3.googleusercontent.com/ocJEiB-RRyhDSyiHRkt7_dARw2FjLVks3C7I93W32ZXkKlQeUCMpPP7v84OWTocFHhWcvFQnkWqbJ-1gBXp8Q8l3SAXrLTKyheuRJymrGR-TBmZLq0NvMBEHA9KYYxQmog) In the hierarchy view, navigate to where we store the assets that display the user name and user profile picture. It’s found under UI Root>Header>ProfilePicCover and there you will see two game objects called Username and ProfilePic. ![](https://lh5.googleusercontent.com/Mc-nHiY36B7_KkRrNssaKtn3a1Fp7WPH4M8q12wRtSY-kk2YJ8gbJdK3aZvhgBU9UmShyy71Z3ITxblyBJKzFapbzVX8sfDLlRITrSG7p_sjTjr5Gtl4NWI33hXNWad5-A) Drag “UserName” from the hierarchy into the empty “User Name(UILabel)” field in the API Manager Object. Then drag “ProfilePic” from the Hierarchy into the empty “Profile Pic (UITexture)” field in the API Manager Object. ![](https://lh5.googleusercontent.com/shX9L9uKOTZGkNAI7nvPxpckmv0xeYPlQ-pmoPErRyLvlojeJVHdZBTxCJ7C2chxOEoNakWWpiMAcIiHauC4IfbbRJIbIRKu_FSV0Jqw40dDuhhFEb0w5AiqT67-zRZOVg) Now when we log our Facebook User Name and Profile Picture will be pulled in and displayed along the header at the top of our game scene. ![](https://lh6.googleusercontent.com/70rx6ieBL1sg8qqoNWKIVcDxZ02C3zt_4SqKA-iBNnrYe-SVFnS0vbJfBfjGGtUdWh7NEOmjlstxzCvGQSqlN4dW2m_xGx-A-MseqUqoNzplpmh8WXcTIj_9Nv4Un6olHg) We have now successfully pulled and displayed our Facebook profile picture and user name in game. In the next part we will pull in our Facebook friends and display them in game so that we can send some Challenge Requests. Don't forget to check the [developer forum](https://support.gamesparks.net/support/discussions) if you have any questions, or with the GameSparks team at [info@gamesparks.com](mailto:info@gamesparks.com)
