# Unity Tutorial: Setting up GameSparks and adding a Leaderboard

## 1: Introduction

![](https://www.youtube.com/watch?v=rN0tS-195TM)

In this tutorial you’ll learn how to set up GameSparks in Unity for the first time and how to use GameSparks to implement Facebook integration including user authentication and pulling data from Facebook. You’ll learn how to set up a leaderboard, post scores to it and how to display the leaderboard correctly in Unity using information pulled from Facebook. You’ll also learn how to register users without Facebook and how to use anonymous device authentication. In the next part, we will cover setting up your game for the first time on the GameSparks portal and Facebook Developers App page as well as importing the GameSparks and Facebook SDK’s into Unity.

## 2: Setting Up Facebook and GameSparks

![](https://www.youtube.com/watch?v=snz64n1Pa0s)

In this section you’ll set up a new game project in GameSparks and Facebook. You’ll add the Facebook and Unity SDK’s to Unity, finally setting up your game in Unity to pull user data from Facebook.

### *Setting up new GameSparks and Facebook Projects*

*1) Set up new GameSparks project*

If you have not already done so, go to [https://portal.gamesparks.ne](https://portal.gamesparks.ner)t and register.  Once registered, log in and you will be taken to the portal home page.  From here, add a new game to the GameSparks interface from the drop down menu at the top left. Fill in the name and description. For this tutorial, call the game “GameSparks Tutorial”. Save the project. The first page you will see is the Configurator overview. We will manage our API keys from here.


*2) Set up new Facebook App*

Open up <http://developer.facebook.com> to create a new App there. Go to: \_Apps_ > \_Create New App_ and fill in the title,  You can use “GameSparks Tutorial” again.

*3) Add Facebook App Keys to GameSparks Project*

Now that you’ve set up both new projects, retrieve the Facebook App ID and App Secret from the Dashboard.

![](https://lh5.googleusercontent.com/YFbYpP8eTAULrDpVnoFaQ2Frh4VGts4gfwbDghr63MnBT7FRoBczvzLsB2eiE8E4SDAzmr4Rn0MHAx7RkcViw8UYt4D-uV43HoiIdsdb-GZqqXdphvIAU-A7mt1IAqJeZQ)

Copy and paste the App ID and App Secret into the Facebook [Integrations](/developer-portal/integrations) area.

### Setting up GameSparks and Facebook SDK's in Unity

*1) Download the SDKs*

Download the GameSparks SDK for Unity and the [Facebook SDK](https://www.google.com/url?q=https%3A%2F%2Fwww.facebook.com%2Fcampaign%2Flanding.php%3Fcampaign_id%3D282184128580929%26placement%3DSDK_6.0.0%26url%3Dhttps%253A%252F%252Fdevelopers.facebook.com%252Fresources%252FFacebookSDK-140805.unitypackage&sa=D&sntz=1&usg=AFQjCNH_6tTQizQFinQAVbaJ0m_lbMMo5w) for Unity.

*2) Import the SDKs*

 You should have the two new SDKs downloaded now. Locate and import them to Unity via \_Assets_ > \_Import Package_ > \_Custom Package_.

![](https://lh5.googleusercontent.com/9CtovOSjVwSZCb3nmJpDhHXNa9q0EsqykQInD__qhXnkNJDSsQ01oIQNAf2pnk3MDwy6bA7gqWbHVXZjNnzAl8j1nACZHjn41EhYVDAAs0X0JZRuAuRQMx4_ie9ZjhNpig)

Unity will process them. You should have two new menu items in Unity now, “GameSparks” and “Facebook”. If not, click on another menu item and they should appear.

 ![](https://lh4.googleusercontent.com/XiiW_js5_Z6nJQn56G3cZENpXZItWnbwuH73jV9dlujADL_IcTV3LNAdb5MN0MDmJR9zfp9BZemMmIMz4nQJ1EzhgB6Kfcten_3bXbNFyDyNTSkBAf0rmsI4g0WChJ52aw)

 *3) Add Gamesparks and Facebook App IDs*

  Enter the Facebook App ID you retrieved earlier in \_Facebook_ > \_Edit Settings_. Then enter the Gamesparks API Key and Secret Key through \_Gamesparks_ > \_Edit Settings_ which you can find on the game overview panel in the Gamesparks portal. Make sure you save the scene after entering the keys. You’re all set up, now you just need to test everything to make sure it works.

### Testing the Gamesparks API and Facebook integration

*1) Open Gamesparks TestUI*

 In the \_GameSparks_ > \_Edit Settings_ tab in Unity, open the GameSparks test harness by hitting “test configuration”

![](https://lh4.googleusercontent.com/coFiuC7MOkf1A2VMa6_i71pwmLZz4qv7VIJMdPorxOjPisHPq_1GFozulEJ9xWFoe8labltIzKBqagqwXVhpu1uwj_HiOBuou8ZNZ1so2PuBiZM6B63PGxaPgzVdUGUmEw)

You will be prompted to save the scene and then the test harness will load. You should see the message that GameSparks is available; Unity is now connected with the GameSparks service.

* 2) Send a request to the Gamesparks service* To make sure its all working correctly, send an authenticate device request by hitting \_deviceAuthenticationRequest_ in the test harness, if GameSparks returns a UserID then everything is running properly.

![](https://lh4.googleusercontent.com/Iy9ZJ84lugvt0lRr1Uo26yS4XxevdG9eToPJG8fVS2gczp50UTq0aB3K4Jm0Nsi2_Ou1rmrhT_4eQKOdrZbR37lJaJf2NtOGu3XacSvvD6z5llvCrVXV0rBewCwXVHnEmg)

*3) Test Facebook Connection*

 To test the Facebook connection, you need to retrieve an Access Token from the Facebook Developer page. On the developer page navigate to \_Tools_ >\ _Access Tokens_. If you have just created the app, you will need to grant it permissions. Hit “grant permission” and you will be presented with a new _UserToken_. Copy and paste this into the Access Token field in the Unity Test Harness and then hit _facebookConnectRequest_

![](https://lh4.googleusercontent.com/_pCz4hURVBjHMgHaR3cy-ZcCyxea9xwLSIW7nxvzzehbSLZqETb_sdS3wvlvGB4Hn6CJ8J3Ozuk95RqheblZLvryosjwoHZFPVREd6yzwHvYjIymoXwCyNNZBKlsk-XKWQ)

If the Facebook API has been set up in Unity and GameSparks correctly, the harness should return a string containing your Facebook details, specifically your name.

![](https://lh3.googleusercontent.com/GmXMdSkwoO8E_MKWfd7efTScqufcfUFG2_-9c0jO7C2Xx6cqqXbrTAoTPbiAz2Sgove87YTOP5z0p5eB6C4AkT2dt9bTl08S3Glkc92Apgk2sMpp2LSKZzyUlFxabw4e1g)

# 3: Silently Logging in to GameSparks with Facebook

In this section, you’ll be setting up Unity to use Facebook as a log in for GameSparks when your game starts. We’ve provided the code below necessary for the exercise.

*1) Logging into GameSparks with Facebook*

To get the most out of GameSparks, it’s best to log users in silently as soon as the game starts. This way GameSparks is accessed for data (such as updated leaderboards, daily quests, p2p challenges etc.) immediately. We have a script below that initialises and logs into Facebook. Read through the comments to make sure you understand how it works before adding it to your game.

<pre class="lang:c# decode:true">using UnityEngine;
using System.Collections;
using Facebook;
using GameSparks.Api.Requests;

public class APIManager : MonoBehaviour {

        // Use this for initialization
        void Awake () {
                //If facebook is not Initialized
                if (!FB.IsInitialized)
                {
                        //Call FB.Init and once that's complete we'll call
                        //Facebook Login
                        FB.Init(FacebookLogin);
                }
                //Otherwise if we already initialized call Facebook Login
                else
                {
                        FacebookLogin();
                }
        }

        public void FacebookLogin()
        {
                //If we aren't logged in
                if (!FB.IsLoggedIn)
                {
                        //Call FB.Login, tell it to call GameSparksLogin
                        //when done
                        FB.Login("", GameSparksLogin);
                }
        }

        //GameSparksLogin takes FBResult from FB.Login but we don't use it
        //for anything
        public void GameSparksLogin(FBResult result)
        {
                //It never hurts to double check it you are logged into Facebook                
                //before trying to log into GameSparks with Facebook
                if (FB.IsLoggedIn)
                {
                        //This is the standard FacebookConnectRequest. This will                        
                        //log into GameSparks with your Facebook Profile.
                        new FacebookConnectRequest().SetAccessToken(FB.AccessToken).Send((response) =>
                                                                                         {
                                if (response.HasErrors)
                                {
                                        Debug.Log("Something failed with connecting with Facebook");
                                }
                                else
                                {
                                        //Here you can display some information                                                                              //to the user that they are logged in...
                                }
                        });
                }
        }
}</pre>

**2) Add Script to Hierarchy** Create a new Empty Game Object in Unity (GameObject>CreateEmpty) and add the script above as a new C# Script component. Also add the GameSparksUnity.cs script found in Assets>GameSparks to the object. This script needs to be added to your game so that GameSparks will work. ![](https://lh6.googleusercontent.com/w-CwcoILxfvx2bCopph_aalRyqFDcASdYaQ-t7D_TeoA-MI2k3IUzMIomTFDmCYBtE54nmN8KQ8U15HAna4hNSc8eTw4xMpKH7KtNStKvxWQznYN00YIc6dVFxAYMfjkrw) If this object is in the opening scene of your game, say, the Main Menu scene then Facebook will log the client into GameSparks on start-up. Call the object “API Manager”. ![](https://lh5.googleusercontent.com/C8LD4rN2wdqJe-z0nTQDPgdeM7-cjX8nHSrksMzaXWG5D4fC4U2AEHOR99GLUegmAkVvk6DwFp0RObk-V5yuwjG05Meq76rj4Rg_8z9q_BUIdTG5kCQs2jOsuxKCzagw4Q) **3)Testing it out** When you click Play in the Unity editor you will be able to see the Facebook initialization running in the background. The access token request will pop up. ![](https://lh5.googleusercontent.com/dLWTz3bqybxP9KjRBEaLGhXyvR1KqcIU7ON5qTJ_Giq8kxocW3kZgK-lu3WhG65eRArxNXQsK3zFApLS_ejLXCAeDzb0ApWgFCixELluOcn2gdfpQXoYVDSRAc3dO8TooA) Paste your access token retrieved in the last exercise from the developers.facebook.com page and click Login. The Unity Console will  get a message from GameSparks, if you see your name after “displayName” you’ve successfully logged into Facebook. ![](https://lh6.googleusercontent.com/Pe5719oytz97qmOSMR75YhbRAz4XvD2yuHnKpEjkYIkLp_rTwxspXfGfU259XtKcgRMqerKeLqTevXU_k8qRx242Ax-HrBrCj34u9Xm9gI2YYUm8kUJawsqlCs9AypfXyQ) In the next section we will be setting up our leaderboard in the GameSparks portal, creating our Post Score Events and looking at the GameSparks Test Harness.

# 4\. Creating and Testing our Events and Leaderboards

<iframe width="854" height="510" src="//www.youtube.com/embed/u9W4eWYYjz0" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

The exercises in this section take place exclusively in the GameSparks portal. You will set up a Leaderboard and create an event to post scores to that leaderboard. Then you’ll use the GameSparks Test Harness to make sure everything works.

### <a name="h.tkvj8visvqgt"></a>Setting Up a new Event and Leaderboard

** 1) Create a Post Score Event** Open up portal.gamesparks.net and navigate to Configurator>Overview. To create a new event, click on the small plus icon. This will open the Create Event dialogue. ![](https://lh6.googleusercontent.com/dZtZGcX6SjXqM9PcZQ-H-3AUP9hPGZ4y4Q8HtILzqGoEs9KB2tVa8O7_xD1PFz0G5DbNLrDuJ9LSLr3IjYQelziISLgGax2mCIvYQxAKXxJHpbJrBGUy8Cvqf7N3bXB-gA) **2) Enter Event details** Fill in the details of the event. For this exercise name the event “Post Score” and fill in the description as “it posts the score”. Fill in the short code as “postScore”. The short code is the reference we will use in our Unity scripts to post scores to GameSparks. In practice these fields can contain whatever you like. The name and description are human readable and the Short Code is code readable and will call or register the event. ![](https://lh5.googleusercontent.com/Jn_eQtpS7934b2344ZvntKBja_hYNlY-sWXjJ3QEr8ZWWp07F-sCzpxoLZYCf-fIOIutNV2TUOWljubxzFdNWTLsIR6AGYtydF10pu5obfR7AuOVVFY6dg9uBUDCm5VOow) Next is to add the event’s attributes. Press the plus icon in the Create Event dialogue. This is what information will be returned and stored in GameSparks when the event is triggered in game. This event should return the highest score the player achieved so set the Data Type to “Number” and the Default Calc to “Maximum”. The name should be a new name for the attribute, in this case call it “Score”. The short code will be “score”. Hit save to save the event. ![](https://lh5.googleusercontent.com/bwfMghNQ1z53bCX39V9c_TyxqVruYCp1qO2T63-emtdqefZHHkgRuP46qgBxv1T0DSt4l2YzaRfo7zqTQ1mVZZhkA2cEdUez-2GS-cOGDcg4HE5QRn4fbOiv8pvZaYJazg) **3) Create a Leaderboard** Open up the Leaderboard menu by navigating to Configurator>Leaderboards. Here you can create and manage you leaderboards. Click the plus icon to bring up the Create Leaderboard dialogue. For this exercise fill in the name as “High Score Leaderboard”, the description as “it’s a leaderboard” and the short code as “highScoreLeaderboard”. The Update schedule can be set to reset the leaderboard daily, weekly or monthly if you want to create time-limited leaderboards. This leaderboard will be a continuous global ranking of the top scores, so leave the Update Schedule  as “Real-time”.The High Score and Social notifications can be left on on for the time being. These will send a push notification to your player if someone beats their highscore. Press the plus icon to add fields to this leaderboard. The event and event attribute you set earlier is already filled in, if not make sure that Running Total is set to you “Post Score” event and that the Summary is set to “Score”. Leave the filter type at * and the value blank. Sort Order should be set to “Desc”. ![](https://lh4.googleusercontent.com/D6wLRqJmBBaVcEjL4kEQw97yuC4WUOwPpFDxRnnRJAId0hEhGcbqHmITibwsDgy0k-A-Q8VOCGS_cVNOAIgh0CAlzhymWt8KtUcYq5OGYZfqxsU2iI93zY8coGNAAaLdzQ) <span style="color: #000000;">And that’s it. You have successfully set up a basic score leaderboard. Next thing to do is use the GameSparks Test Harness to make sure it’s working properly.</span>

### Testing in the GameSparks Test harness

**1) Authenticating** The GameSparks test harness lets you test all the GameSparks functionality you have set up before writing a line of code in your game. To test your new Leaderboard and Event on the Test Harness you first have to Authenticate as a user to send events. Open up the Test Harness in the Gamesparks Portal. Since this project is using Facebook to authenticate its users we will authenticate with FacebookConnectRequest. Click FacebookConnectRequest under the Authentication tab in the Requests window. ![](https://lh5.googleusercontent.com/PIbURkPMEdNQD7aY8C3yusoourcmA4yCGnpn9RK_H855rqhWJv6R0OMBq59B3q8Ptexg-YKZeQpp2PydboI20la2BsuFA3DGVFjxND2sE12DASO3CuQJ80xsj6X27sLNVA) <span style="color: #000000;">Retrieve your access token from the </span><span style="color: #000000;">developer.facebook.app page (Tools>Access Token) and copy this. Return to the GameSparks Test Harness and paste the Access Token in the JSON window under the “accessToken” field highlighted above. It should look like this</span> ![](https://lh4.googleusercontent.com/uc1EEjcpY5QML6SdGN11jRDLX36xuyv4bvBiDmnUKrPpvS3MW-7ILgQ7LOnMCFIzGr1IzoP8vaehb9PcM1f9WS-P6032kNfJ9CYqJ6-j1fwilbRxjRZibNIQxaPQXKM_AA) <span style="color: #000000;">Click the send button highlighted above. In the inspector on the right you can see the request you sent in green text and the response in blue text. You should see your name returned and an Authentication Token filled in automatically.</span> ![](https://lh4.googleusercontent.com/MYtlFb0eFHZRO1xjP0LoqY0trndcTEXxxWr0TxVI6NIjhpBTPZ70xtAsjnbaxJ3IPTcp80amY0GdZXCcLq-tsNvf0fxobYpoHcs7urkIGjo0O9siFg2vZN3lG-vZ46tJhw)

**2) Log an Event in the Test Harness**

Click the LogEvent tab in the Requests menu. You will see the Post Score event that you set up earlier in the exercise. Click it and the text in the JSON box will change. You will see a “score” key - this is the score attribute you defined earlier. Change the value of score to any numerical value, 15 for now. Send the request.

![](https://lh6.googleusercontent.com/_LRJklKupv9XYM8iTGDKQiIG3Fbstsxiue8vIVVWSB28yGGwZInziJaVRBV_TBZ9p1qKECJWu8WSDCAWmjT8-q4rxd69KK213sSJd0-syQIgeahDjJcuXVfy_eRBqqtw_Q)

You will see a message being returned in orange, this is a new high score message and is returned because you posted a new score as this particular user. In the score field it should read “15” and the userName should be your Facebook profile name. This message also gives us additional information about what time the score was posted and where. **3) Retrieving Leaderboard information** To check the details of the Leaderboard we have just sent a score to click the Leaderboards tab in the Request menu. Then select the LeaderboardDataRequest. You can delete the fields that aren’t applicable to your Leaderboard. You just need to leave class, leaderboardShortCode, entryCount and requestID. Fill in leaderboardShortCode with your short code “highScoreLeaderboard”. Send the request. ![](https://lh6.googleusercontent.com/dbD7ayQq_B-FuC5U52y9SvLTGIhFOKRbVWpZxMd13O4Pe3JqD3gCMztagaZMc1KK0i50B_c76BGzyMZUFXn0q4Wk0B2h4Bg2NCWvTL3DAAxsepBEOm1WjfKZpVgi-rz1Yg) The Leaderboard data is returned. It tells you who has posted to the leaderboard(just one person so far), the rank of the player and from where they posted. Since there is only one score logged to the leaderboard it looks a bit bare. Add some more test users to fully check if the Leaderboard is working **4) Adding test users** Register two more players with GameSparks. To register more players go back to the Authentication tab and click “RegistrationRequest”. Enter a userName and displayName, for this tutorial use testuser1 for both and hit send. You are now registered and authenticated as a new user. ![](https://lh3.googleusercontent.com/qiBCnkhCz9p-X1nauLeKtB6WAZjS5kl_WsBKfzhu8fw82Mx2ewRlHn9QhvyPsaOsYJq7n6qFBWAjlG1-e1HshYuAWhw2fyumTKuQ8gPkd-1m4S7e6Cl3ukEpMFiWs3Xc0Q) Log a new score while Authenticated as this new user with the score event under “LogEvent”. Make the score 500 so it’s higher than our first score. Repeat these steps to make a testuser2 and log a score again, this time 5. Now call the LeaderboardDataRequest again. This time there should be three entries listed in descending order with your new testuser1 on top and the original score you registered while logged with your Facebook id in the middle and testuser2 on the bottom. That’s it, your leaderboard works. In the next section will cover  writing the code to postScores and retrieve leaderboard data in Unity.

# <span id="eow-title" dir="ltr" title="GameSparks Leaderboard Tutorial - 5\. Creating Leaderboard Prefabs &amp; Writing Code to Post Our Scores">5: Creating Leaderboard Prefabs & Writing Code to Post Our Scores</span>

<iframe width="854" height="510" src="//www.youtube.com/embed/3XhK-FJrwH8" allowfullscreen="allowfullscreen" frameborder="0"></iframe>This tutorial will cover creating our leaderboard entry prefab, our in game leaderboard displayed to the player and writing code to post scores and to retrieve leaderboards from Gamesparks. You might find it helpful to dowload our sample game Tappy Bird and see what we did to implement our in-game leaderboards.

### Creating the Leaderboard Header

First thing you’ll need to do is set up a new NGUI Panel to contain the Leaderboard and a Header to show the player what page they are looking at. **1) Creating the Leaderboard Parent** As a child of the UI Root create a new Panel through NGUI>Create>Panel. This parent will contain all the elements of our Leaderboard. **2) Set Leaderboard Header** As a child of the new Leaderboard parent you just created, add a new 2D sprite to contain the Leaderboard Header (NGUI>Create>Unity 2D Sprite). Select button-1 as the sprite and resize it to about 320 x 30\. Set Material to “Sprites - Default”. Drag it to the top of your Scene as it’s going to be the Title of the leaderboard that displays over the results. Name the new ![](https://lh3.googleusercontent.com/kaqxOravUo8XeUPOWDmlG5fDnTbLQa1dSmBoHDqGhAayA5IdwxicWLnPZDnnwBpLbZKs-JaIgqcRKsSrzHuQNt5WgCdZNtju6pUd8MOveaRDlYWwCdZHlZy_gSRE1jA92Q) **3) Set Leaderboard Header Label** In the hierarchy, as a child of the Leaderboard Header add a new Label (NGUI>Create> Label). This is will be the text displayed in the header panel. Set the new label up in the inspector as follows:

*   In the “Text” field type “High Score Leaderboard.”
*   Uncheck “Gradient.”
*   Change the “Effect” menu to “Outline”

![](https://lh4.googleusercontent.com/Wk14iNdjYOFp1sr0VDiLcaMmSrJ1Pch1WDd30ylHGj0smbo9gnR3qxXZ6e3D9IoXcLQpyB_fJT8vq7yOrNHvRI-KhNZEhXntATpRhjIBpc6hOQA0_XQqLBiqwo1oRZjc1w) **4) Create NGUI Grid**

As child of the overall Leaderboard parent Create an NGUI Grid (NGUI>Create>Grid) This will automatically arrange any entry added to the Leaderboard. Set the Grid arrangement to “Vertical” and the cel height to “40”, on account of our header. This gives each entry some space as it’s auto arranged.

*   Arrangement: vertical
*   Set cell size height: 40
*   Move the grid up so it’s positioned just below the Leaderboard Header

### <a name="h.yv5382vfxjj1"></a>Create a Leaderboard Entry Prefab

This is a prefab that can be recalled whenever we want to add a new leaderboard entry. It will contain a Unity 2D sprite and three labels that will hold the strings for User Name, User Score and User Rank. Whenever an entry is added to the Leaderboard the information on this Prefab will be updated and a new entry added to the grid. **1) Create a new Unity 2D Sprite** As a child of Grid create a Unity 2D Sprite (NGUI>Create>Unity 2D Sprite). Rename this sprite “Leaderboard Entry” in the Hierarchy.  Set the sprite to “Button - 2”, Material to “Sprites - Default”. Snap it and Resize it to be roughly the same size as the Leaderboard Header: 312 x 28\. Make sure it’s correctly, slightly below the Leaderboard Header. ![](https://lh6.googleusercontent.com/elo80fwWSUfv7ftmLrW6wbYFVkX3FjtSxrpWggTE6hx-J7KL_uL1eTXJ4ZGK5rYGlbVET323Jo6ntHGmeWLB2a1NzVw8k7UxhFKQZxnUxfo65iQSnx9u61QvRxwaP00ubA) **2) Set a User Rank Label** As a child of Leaderboard Entry add a label(NGUI>Create>Label). Rename the Label to User Rank. Set it up in the inspector as  follows

*   Enter Text as 1 (Any text entries we add here are just for testing, these test entries will be overridden by our scripts in the future)
*   Turn off  the gradient on the text
*   Give the text an outline
*   Position on left of the Leaderboard Entry Sprite.

**2) Set a Username Label** As child of Leaderboard Entry add a second Label (NGUI>create>label. Rename the Label to “User Name”.

*   Enter “Username” in the Text field (again, this entry is just a placeholder to make sure we have configured the prefab correctly)
*   Turn off gradient on the text
*   Give the text an outine
*   Position in centre of label

**4) Set a User Score Label** As a child of Leaderboard Entry add a third Label. Rename this label User Score. In the inspector, set it up as follows:

*   Enter 5000 in the text field
*   Turn off gradient on the text
*   Give the text an outline
*   Position to right of leaderboard

**5) Save Leaderboard Entry as a Prefab** Hit apply and drag the Leaderboard Entry Parent from the Hierarchy into your Prefabs folder to save a prefab. <span style="color: #000000;">We now have a Leaderboard Header set up, and a Leaderboard Entry prefab with entries for Player Rank, Username and Score that can be called and filled with information pulled from GamesSparks. The scene preview should now look something like this:</span> ![](https://lh5.googleusercontent.com/uqyx7GfWg2ltZ4dRSTIGc-YpwdakXNXedpJjeKSmigqGHdnCpOfK2osvrN5zZrombXPb6U43JSvPLit9z8y52HcReosGJdQMY9gwhvDLLTaAwhiJY4B0VPK4LKsWP4LMUQ) Next we will write scripts to allow our Leaderboard to function that will pull information from GameSparks, add it to the Leaderboard Entry panel and update and display the Leaderboard whenever it’s requested. **1) Leaderboard Entry** In this script we’re adding the strings to pass info taken from Gamesparks to, such as Score, Name and Player Rank. We’re also defining the NGUI labels that have to be updated on screen. Create a new C# script and name  name it “LeaderboardEntry”. You can copy the the code below. To understand how it works read the comments in the code.

<pre class="lang:default decode:true">using UnityEngine;
using System.Collections;

public class LeaderboardEntry : MonoBehaviour {
//creating the public variables that we can pass the GameSparks information to
        public string rankString, usernameString, scoreString;

        public UILabel rank, username, score;

        // Use this for initialization. The NGUI Labels will update
       //with the information we pass to them later
void Start()
        {
                rank.text = rankString;
                username.text = usernameString;
                score.text = scoreString;
        }
}</pre>

<span class="c0" style="font-weight: bold;">2) Add this script to Leaderboard Entry NGUI as Component</span>

Drag the script onto the inspector tab of the LeaderboardEntry parent. The three variable UI labels we defined in the script need to be assigned UI elements. These are the UserName, User Rank and User Score that we set up earlier. Drag each Label into the corresponding field

![](https://lh6.googleusercontent.com/99bffkCy66XN_VnBIhoeLpuu-dGsmqXpM2XYe2H7wDVPOYhQkhRI43J_YRlx_8uqN2y18x2z-WmxRsfIxVz4MKqXemtGQqdprfOCGIxCg6WH6yczX8pqQu9WpSik9ESafA)

*   Drag username Label to username entry field
*   Drag userRank Label to Rank entry field
*   Drag userScore label to Score entry field

![](https://lh4.googleusercontent.com/JP12rfQUlWygEd9R1XyKM4ehOGRifvfiRZJxeqfFLcUby3k9H7KvJTgwnvXSrgqCFGMT3fHhXfepZKGh8WXFnp0XJZcP0OKSFSfyf7I7iZ4ZgEgKZQvaanEaTO8lc1PlEw)

Now when Leaderboard is instantiated it will pass username, userRank and userScore strings to the UI template we set up and update the values on LeaderboardEntry

Remember to hit Apply to update the LeaderboardEntry prefab.

**2) Adding a Post Score script**

First of all we want to pull in our custom GameSparks SDK. This will create functions based on the events you have created on GameSparks. To do this, navigate to  Gamesparks>Edit Settings>Get my custom SDK

 ![](https://lh5.googleusercontent.com/ZVzQIPXSjY3rMvbePvey6YNyjhlOoVxlq0BoTrBHxPafRF9zqwGPMrOuVuZohIdMbPakElU19j8ecCneKVRN1vDMz9oif06jSfx6ZbkBefj8ANMsApRwOhxTXyZDV6LkQg)

The GameSparks custom SDK will create functions based what you have set up in the GameSparks portal. For Example, we have set up a postScore as an event in GameSparks

We’re going to add our Post Score script to the Game State script. Navigate to to the Scripts folder under Assets to find it. If you are using this code to your own game and not the tutorial game, bear in mind functions such as <span class="c21">LogEventRequest_postScore() </span>and <span class="c21">Set_score(</span><span class="c20">scoreToBePassed</span><span class="c21">) </span>won’t work unless they match up perfectly with the corresponding events and attributes you set in the GameSparks portal. If you’ve been following the tutorial along thus far it should be fine, but it’s a good exercise to double check.

<pre class="lang:default decode:true">public void PostScores(string levelName, int scoreToBePassed)
        {
//The LogEventRequest_postScore() has been created by the custom SDK based on
//the events you made on the Gamesparks Portal.
//Likewise the Set_score(scoreToBePassed) Attribute has been generated by
//the attributes set in the GameSparks portal
                new GameSparks.Api.Requests.LogEventRequest_postScore().Set_score(scoreToBePassed).Send((response) =>
                {
                        if (response.HasErrors)
                        {
                                Debug.Log("Failed");
                        }
                        else
                        {
                                Debug.Log("Successful");
                        }
                });
        }</pre>

**3) Creating a Leaderboards Script** Create a new C# script in the Scripts folder. This script will generate the Leaderboards after all the GameSparks data has been pulled. It will add new entries based on that data in a grid and it will clear out the old entries whenever the Leaderboard is requested.

The script is provided below. To understand how it works read the comments that have been added. Again, make sure that any custom GameSparks function, such as LeaderboardDataRequest_highScoreLeaderboard()matches up with the short codes you’ve assigned in GameSparks.

<pre class="lang:default decode:true">using UnityEngine;
using System.Collections;
using System.Collections.Generic;
using GameSparks.Api.Requests;

//the prefab we are going to instantiate
public class Leaderboards : MonoBehaviour
{

        public GameObject leaderboardEntryPrefab;

        //NGUI grid, this will re-organise the leaderboard whenever
        //a new entry is added
        public UIGrid leaderboardGrid;

        //creates a list of GameObjects. whenever the leaderboard is called it w       //ill clear out the old enteries and pull in the new. This will also keep      //track of the enteries so they can be deleted in the future
        public List<GameObject> entries = new List<GameObject>();

        void Start()
        {
                //re-arranges all currently stored game objects that are
               //children of the leaderboard grid
                leaderboardGrid.Reposition();
        }

        public void GetLeaderboard()
        {
                //the leaderboard entries could contain old data.
               //First destroy all existing Leaderboard objects
                for (int i = 0; i < entries.Count; i++)
                {
                        Destroy(entries[i]);
                }

                //because we deleted the objects contained on the list, the list                //now contains nul references and has to be cleared so the new
                //high score objects can be added
                entries.Clear();

                //pulls in the Leaderboard information from Gamesparks,
                //identified by the short code added when setting up the
                //Leaderboard in the Gamesparks portal
                //SetEntryCount() will define how many entries you want to pull in one go
                new LeaderboardDataRequest_highScoreLeaderboard().SetEntryCount(10).Send((response) => {

                      //what we will do with the information given by GameSparks
                        foreach (var entry in response.Data)
                        {
                                //only children of the NGUI grid will be added
                                //to the grid. We make new objects with our
                                //LeaderboardEntry script and add them as
                                //children to the NGUI Leaderboard Grid
                                GameObject go = NGUITools.AddChild(leaderboardGrid.gameObject, leaderboardEntryPrefab);

                                go.GetComponent<LeaderboardEntry>().rankString = entry.Rank.ToString();
                                go.GetComponent<LeaderboardEntry>().usernameString = entry.UserName.ToString();
                          //the score string has to be added as a number value
                         //based on the short code used for the attributed
                        //to the leaderboard we are pulling from
                                go.GetComponent<LeaderboardEntry>().scoreString = entry.GetNumberValue("score").ToString();

                                //adds the gameobject to the list of entries
                                entries.Add(go);

                                //repositions the new object so it isn't stacked                                //over existing objects
                                //created by the loop
                                leaderboardGrid.Reposition();

                        }

                });

        }
}</pre>

Add the Leaderboard script to the Leaderboard Panel Game Object as a new component component by dragging the script onto the Leaderboard Panel inspector.

Drag  the prefab it needs to instantiate into the empty the Leaderboard Entry prefab field. This is the Leaderboard Entry Prefab we finished earlier, it should be in your Prefabs folder.

Add the child Grid of the Leaderboard object to the Leaderboard Grid field on the Leaderboard panel.

![](https://lh5.googleusercontent.com/nVYgpuY_NW9TDzM5Zxp1UDU795rH_qPewj8nlEam1ckcNAeQwus0tjkqUqOsH5gkyywdrWrAKJUZRTM5jP4x1GjPsfc9yu6T-dGLbug9pfC8wtNC4m34Myz2DV17OXgfXg)

And that’s the leaderboard functionality in your game all set up. Next we just need to make the leaderboards accessible by the user from the game’s Main Menu.

### Bringing Leaderboard up in-game

Now we just need to set up some UI elements to allow the user to toggle between the main menu and the Leaderboards. We also want to allow the user to call the Leaderboards themselves. To do this we will set up a button to bring up Leaderboards and toggle between Leaderboard page and Main Menu, and we’ll also set up a back button on the Leaderboard page to return to the Main Menu.

**1) Adding a Back Button on the Leaderboard page** Add a button to bring us back to the main menu from the Leaderboard page. Add new Unity 2D sprite (NGUI>Create>Unity 2D![](https://lh5.googleusercontent.com/fru_4JRjlZByYeu23vD1NKyjAL-gURr82MJyUigd_1VhS405kkJHS0TmCslfeGaJJbX_1gi9JCnb1Xa8vslYsKdrgMTsgFrmdXGGbwPMmsFdWpPGQABW824MYwAMRFTqFw) sprite) as a child of  Leaderboard. Configure the sprite as follows:

*   Assign Sprites-Default as Materials
*   Assign button 3 as the 2D sprite
*   Rename it to Back Button
*   Add a new Button Script (NGUI>Attach>Button Script) `
*   Add collider NGUI>Attach>Collider
*   Snap the sprite widget>Size>Snap
*   Position the sprite at the bottom of screen
*   Add Label NGUI>Create>Label. Configure as so it matches previous Labels we’ve made. Enter “Back” in the Text field.

** 2) Add Tween Alpha Component to Leaderboard  ** We don’t want the Leaderboard to be visible on boot. It would overlay the Main Menu.  To make the Leaderboard transparent on start select Leaderboard in the hierarchy and add a Tween Alpha to it via (Add Component >Scripts>NGUI>Tween>Tween Alpha) Configure the Tween Alpha Component in Leaderboards like so:

*   Set “From” to 0, keep “To” as 1
*   Disable it so the component doesn’t run on launch (uncheck the box beside “Tween Alpha (Script)

![](https://lh4.googleusercontent.com/D0dwE0mtlncApccq9wOMtTP_tXsOOMbh6IVt_FjJ0o6_Uy0tdMjWodl_KemBrQQY2-m-e08i4w7jfq5JZAhrpa5tSYsPvg7BsXGXefN9ZN2d-rweUlGD_4jMRWlFM8dd_w) **  4)  Set “Back” Button to Toggle between Menu and Leaderboard** Select the Back Button in Hierarchy and configure it as follows in the On-Click Panel in the Inspector for the “Back Button” object.

*   Drag Leaderboard from Hierarchy to the empty Notify field in the “On-Click” Panel
*   Set that Method to TweenAlpha/Toggle via the dropdown menu: Tween Alpha>Toggle
*   Drag Main Menu from Hierarchy to the empty Notify field in the “On-Click” Panel
*   Set that Method to TweenAlpha/Toggle too. Again, vua the dropdown menu: Tween Alpha>Toggle

![](https://lh6.googleusercontent.com/J-RQ9gn7yN9dtDP1YhieIURnEVVhkzkKIn0xKICUrhA6N0i0LA7c9gBiI3b1q8vRESTS-MfC86H48p96HBBpqyt4wRpxonOoFhPj0uHmK68CzBAJA_9vWq2D4JxbpXJVEw) <span style="color: #000000;">Lastly, make sure the Alpha Slider in the UI Panel(script) Panel in the “Leaderboard” object is set to 0.</span> ![](https://lh5.googleusercontent.com/04MdxxOE-SIiUuO7KPcegqSepHWdwgk87lhk4ROwvkvsFigWrrcCO8iZSufAUU-EG2HjzGMDgpJFjyERYlTBOp3yWnE1B-ZSf7R3hjA3V6DW9iKlz6MMLwm6FRbED4s5MQ)

Now when we click back our leaderboard will toggle between 1 and 0 and Main Menu between 0 and 1, it will look like the scenes are fading between each other.

**5) Set the “Leaderboard” Button to generate the Leaderboard and Toggle from Main Menu**

*   Set leaderboard button to toggle the leaderboards

*   Under Main Menu in hierarchy select Button - Leaderboards
*   Drag Leaderboard parent from hierarchy to empty Notify field in on-click

*   Set the Method to toggle alpha Method>Tween Alpha>Toggle

*   Drag Leaderboard parent from hierarchy to empty Notify field in on-click
*   Set the Method to get leaderboards

*   Method>leaderboards>getLeaderboards

Now when we play and click leaderboards button in-game the main menu will fade away, the Leaderboards will fade up and pull the information from GameSparks and construct a leaderboard

## 6\. Getting a Leaderboard Entrants Facebook Profile Picture

<iframe width="854" height="510" src="//www.youtube.com/embed/iFNQE412Jbo" allowfullscreen="allowfullscreen" frameborder="0"></iframe>In this section we are going to modify the Leaderboard so it pulls in the Facebook profile picture of anyone who posts a score while logged into Facebook.

### Adding a Profile Picture Field to the Leaderboard Entry Template

We already have our basic Leaderboard functionality in place, all we have to do in this exercise is edit out work to add the ability to pull images from Facebook. Start by edting the Leaderboard Entry Prefab. Set up the scene so we can see the edits we are making on the LEaderboard by dropping the Main Menu Alpha to 0 and bringing the Leaderboard Alpha back up to 1 (Remember to reset this after making your edits) **1) Editing Leaderboard Entry Prefab** Drag the Leaderboard Entry prefab from the Prefabs folder into the Hierarchy under “Grid” (So that Leaderboard Entry is a child of Grid). We need to rearrange the template that the Leaderboard Entries are added to so that it can accommodate a Facebook Profile picture

*   Set font size to 15 on all labels
*   Drag the UserName Label over to the right

Now we should have enough space to fit the Facebook profile picture on the Panel ![](https://lh5.googleusercontent.com/YX_Syd4zMd8K1Kc3QCRqSPyMbW_OmtAovcBXfD2fFY-lwZahr5Hvuj-hdOMxFEKjqMWfGqeonOBfgZFyWrgyxHvRrHN5wfnsge-WLiWhQKlPonYGJrcMMoiX_Ny1xHwtNw) **2) Adding a Profile Picture Entry to the Prefab** We need to add a new element to the Leaderboard Entry Prefab that will hold the picture we pull from Facebook and display it on the Leaderboard. As a child of the Leaderboard Entry Prefab add a new texture via NGUI>Create>Texture. Configure the new texture as follows:

*   Rename it to “User Picture”
*   Assign texture for reference purposes, use FancyIcon
*   resize to 25 x 25
*   Drag into position on Leaderboard Entry Panel between rank and userName (in the space we just created
*   Hit “Apply” to save the prefab.

That’s our Leaderboard Entry prefab set up to take a Facebook profile picture now. Your scene should look something like this: ![](https://lh6.googleusercontent.com/b2kHZjBeScU1t6sPYezIrUGlzmJnJYAJ1ol2e21tpqoToSps3Vp4xeA_T1UarG7WsBMCjPNNeJBHkCUMaHYcMBHMQzVXmqZQnvsTOIOkw9-gzze3lcLwNLmhQRY68n6AzA) Now we just need to edit some of our Leaderboard scripts so that they will pull and apply the Facebook profile pictures to the Leaderboard.

### Editing Leaderboard Scripts to pull Profile Pictures

**Edit Code** The two scripts we have to edit are the “Leaderboard Entry” script and the “Leaderboards” script. ** 1) Update Leaderboard Entry Script** We need to add a function to our Leaderboard Entry script that will add take the profile picture and add it to the Leaderboard Entry. The code is below, it’s a modified version of the Leaderboard Entry script we wrote last exercise with comments on the additions made,

<pre class="lang:default decode:true">using UnityEngine;
using System.Collections;

public class LeaderboardEntry : MonoBehaviour {

        //add a new string to refernce when adding the picture to the
        //leaderboard entry
        public string rankString, usernameString, scoreString, facebookID = "";

        public UILabel rank, username, score;

        //Create this variable so we
        //can define what textue we are updating
        public UITexture profilePic;

        // Use this for initialization
        void Start()
        {
                rank.text = rankString;
                username.text = usernameString;
                score.text = scoreString;
       // Defines when the image will be pulled
                if (facebookID != "")
                {
                        StartCoroutine(getFBPicture());
                }
        }

        //this is the function that will pull the profile picture from
        //facebook public IEnumerator getFBPicture()
        {
                var www = new WWW("http://graph.facebook.com/" + facebookID + "/picture?type=square");

                yield return www;

                //make sure the dimensions of the new texture match what we set                 //up in the Leaderboard Entry prefab
                Texture2D tempPic = new Texture2D(25, 25);

                www.LoadImageIntoTexture(tempPic);
                profilePic.mainTexture = tempPic;

        }

}</pre>

**2) Update Leaderboards Script**

We need to update the Leaderboards script to pull in the Facebook ID’s from the Leaderboard information stored on the GameSparks servers. It’s just line but we’ve added the whole script below just in case.

<pre class="lang:default decode:true">using UnityEngine;
using System.Collections;
using System.Collections.Generic;
using GameSparks.Api.Requests;

public class Leaderboards : MonoBehaviour
{

        public GameObject leaderboardEntryPrefab;

        public UIGrid leaderboardGrid;

        public List<GameObject> entries = new List<GameObject>();

        void Start()
        {
                leaderboardGrid.Reposition();
        }

        public void GetLeaderboard()
        {

                for (int i = 0; i < entries.Count; i++)
                {
                        Destroy(entries[i]);
                }

                entries.Clear();

                new LeaderboardDataRequest_highScoreLeaderboard().SetEntryCount(10).Send((response) => {

                        foreach (var entry in response.Data)
                        {

                                GameObject go = NGUITools.AddChild(leaderboardGrid.gameObject, leaderboardEntryPrefab);

                                go.GetComponent<LeaderboardEntry>().rankString = entry.Rank.ToString();
                                go.GetComponent<LeaderboardEntry>().usernameString = entry.UserName.ToString();
                                go.GetComponent<LeaderboardEntry>().scoreString = entry.GetNumberValue("score").ToString();
                                //this is the line we add to pull the facebookID from GameSparks.
                                go.GetComponent<LeaderboardEntry>().facebookID = entry.ExternalIds.GetString("FB");

                                entries.Add(go);

                                leaderboardGrid.Reposition();

                        }

                });

        }
}</pre>

Now that we’ve update the scripts, the final step is to set the Profile Picture Variable we just added to Leaderboard Entry. Drag the “User Picture” from Leaderboard Entry NGUI into the empty Profile Picture field. Make sure to hit “Apply” to save the prefab. We now have the ability to pull Facebook profile photos and add them to the Leaderboard. To test it out delete the Leaderboard Entry NGUI prefab from the Hierarchy. REset the Alpha values of Main Menu and Leaderboard so that Main Menu is at 1 and Leaderboard is at 0. Hit play in Unity and when prompted add your Facebook Access token (retrieved from developers.facebook.com/tools/accesstoken/) and open the leaderboard, it should contain your Facebook ID with profile picture ![](https://lh6.googleusercontent.com/KAxEZ5SPQ6cZiE2dQj5yKGEjG5GdcNQ7AfJhq75zoDWCdiNo3hhoUSw1-ZxQZqrkZnTc6P1WPtxcE6tRiFm1w2HNXJh6unGKLoH86W0qboDX9UMPgRnL2ETvRaLkBsdoDg) That's everything for this tutorial, be sure to check the developer forum if you have any questions, or with the GameSparks team at info@gamesparks.com
