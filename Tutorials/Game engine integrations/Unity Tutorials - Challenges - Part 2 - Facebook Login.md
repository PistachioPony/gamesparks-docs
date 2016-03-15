# Unity Tutorials - Challenges - Part 2: Facebook Login

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 2 of a 6 part tutorial, it's recommended that you look at the previous section before continuing. In this section we will be logging our users into GameSparks via Facebook. It’s best practice with GameSparks to log your users in as soon as the game launches so new data can be pulled and the client updated quickly with any changes that might have occurred on the GameSparks end, such as updating leaderboards, changing daily challenges etc.

* * *

##

## Configuring the Unity project to communicate with GameSparks and Facebook

Set up your game in GameSparks Portal and the Facebook Developer page, if you need a reminder on how to do this check out the [Unity Leaderboard Tutorial Part 2. ](/tutorials/unity-tutorial-configuring-gamesparks-for-facebook-authentication)Retrieve the Facebook App Id and App Secret from [developers.facebook.com](http://developers.facebook.com) and add them to your game in the [GameSparks Portal](http://portal.gamesparks.net), in the edit game window on the Configurator:   ![](https://lh5.googleusercontent.com/YFbYpP8eTAULrDpVnoFaQ2Frh4VGts4gfwbDghr63MnBT7FRoBczvzLsB2eiE8E4SDAzmr4Rn0MHAx7RkcViw8UYt4D-uV43HoiIdsdb-GZqqXdphvIAU-A7mt1IAqJeZQ)   ![integrations](https://docs.gamesparks.net/wp-content/uploads/2014/10/integrations-1024x471.png) Open up Unity and add in the Facebook and GameSparks API information to the SDK’s. If you need a reminder on how to set up the GameSparks and Facebook SDK’s in Unity check out [Unity Leaderboard Tutorial Part 2](https://docs.gamesparks.net/tutorials/unity-tutorial-configuring-gamesparks-for-facebook-authentication). Add the App ID and App Name to the Facebook SDK (Facebook>Settings) ![](https://lh4.googleusercontent.com/nKJn77-vKfMGjiksygaPklLPSveScyiWBan1pLe8KF2of6Ltjok5QcRnNIUfjaAwwOAHIRnSbxJ3tOz7k2HSezRbNRPz3zwGfp0BnblH9riL9qEJ-yCuOHVW3hkaQa4g0Q) Then add the GameSparks API Key and API Secret (GameSparks>Edit Settings) which you can find in the [Game Overview](http://portal.gamesparks.net) in the Configurator ![apiKeys](https://docs.gamesparks.net/wp-content/uploads/2014/10/apiKeys.png) ![](https://lh6.googleusercontent.com/XUgKByrRBg1A_MwrNhd37n0dK6s7yFzuzGKWldR1HICrZhqqav8Fm86JCLrwVAUvDgFA6k9kbd_1S4o45-rTqY-ZU_me88pxmikFzJRP6YnCtrajhUe9iElEMlykIJmFKw) Next, add the GameSparks script into the Unity scene. We use an empty Game Object called API Manager. Find the GameSparks Unity script in the GameSparks folder and add it to the API Manager Game Object. ![](https://lh5.googleusercontent.com/XhdkTvVmSpvsgTZ87AljFtyuaMN3GjHl8NV9glXuA7C9Xnbrj1ZJm6vNIrtvazIWmsA6tXtzrGIUHkY5BfUM_xK0Nc_WCknjqFwmZdR5vGMe3SxleHiVKvgeTToAOnP1zA) Now our game is fully configured and ready to communicate with GameSparks and Facebook. We will now write the script that will manage the client login to GameSparks via Facebook.

* * *

###

## Writing our Login script

We've provided the code below, read through it to get an idea how we implemented the Facebook login. We create a new C# script and write the following:


    using UnityEngine;
    using System.Collections;
    using Facebook;
    using GameSparks.Api.Requests;

    public class LoginManager : MonoBehaviour
    {

    	// Use this for initialization
    	void Start ()
    	{
    		//When the scene is ready we initialise Facebook
    		CallFBInit();
    	}

    	private void CallFBInit()
    	{
    		//When done initialising, call OnInitComplete
    		FB.Init(OnInitComplete, OnHideUnity);
    	}


    	private void OnInitComplete()
    	{
    		//Print to the debug log that we are initialised and check if we are logged in
    		Debug.Log("FB.Init completed: Is user logged in? " + FB.IsLoggedIn);
    		//Call FB.Login
    		CallFBLogin();
    	}

    	private void OnHideUnity(bool isGameShown)
    	{
    		Debug.Log("Is game showing? " + isGameShown);
    	}

    	private void CallFBLogin()
    	{
    		//We first tell Facebook what permissions we want and then tell it todo GameSparksLogin when done
    		FB.Login("email,user_friends", GameSparksLogin);
    	}

    	//FB.Login returns an FBResult, which is just information about our session
    	private void GameSparksLogin(FBResult fbResult)
    	{
    		//Check if we are logged in to Facebook
    		if (FB.IsLoggedIn)
    		{
    			//If so, we can use that acces token to log in to Facebook
    			new FacebookConnectRequest().SetAccessToken(FB.AccessToken).Send((response) =>
    				{
    					//If our response has errors we can check what went wrong
    					if (response.HasErrors)
    					{
    						Debug.Log("Something failed when connecting with Facebook " + response.Errors);
    					}
    					else
    					{
    						//Otherwise we are successfully logged in!
    						Debug.Log("Gamesparks Facebook Login Successful");
    						//Since we successfully logged in, we can get our account information.
    						UserManager.instance.UpdateInformation();
    					}
    				});
    		}
    	}
    }


  Now attach the LoginManager script onto the API Manager Game Object. Now when the game starts the user will be prompted with a Facebook login which will connect them to the GameSparks service. You can get yourself and access token and try it out. In the next part we will create the User Manager which will store the user account information so we can compare it against other users when the challenges come in. Don't forget to check the [developer forum](https://support.gamesparks.net/support/discussions) if you have any questions, or with the GameSparks team at [info@gamesparks.com](mailto:info@gamesparks.com)
