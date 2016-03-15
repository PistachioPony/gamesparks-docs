# Unity Tutorial - Leaderboards - Part 2: Configuring GameSparks for Facebook Authentication

Tutorial - Leaderboards for Unity 3D

  * [1. Introduction](/uncategorized/unity-tutorial-introduction)
  * [2. Configuring GameSparks for Facebook Authentication](/uncategorized/unity-tutorial-configuring-gamesparks-for-facebook-authentication)
  * [3. Logging in to GameSparks with Facebook](/uncategorized/unity-tutorial-logging-in-to-gamesparks-with-facebook)
  * [4. Creating And Testing GameSparks Leaderboards](/uncategorized/unity-tutorial-creating-and-testing-gamesparks-leaderboards)
  * [5. Creating Leaderboard Prefabs & Posting Scores](/uncategorized/unity-tutorial-creating-leaderboard-prefabs-posting-scores)
  * [6. Getting profile pictures for Leaderboard Entries](/uncategorized/unity-tutorial-getting-profile-pictures-for-leaderboard-entries)

This is part  2 of a 6 part tutorial, it's recommended that you look at the previous section before continuing. In this section you’ll set up a new game project in GameSparks and Facebook. You’ll add the Facebook and Unity SDK’s to Unity, and finally set up your game in Unity to pull user data from Facebook.  

* * *

##

## **Setting up new GameSparks and Facebook Projects**

**1) Set up new GameSparks project** If you have not already done so, go to [https://portal.gamesparks.ne](https://portal.gamesparks.ner)t and register. Once registered log in and you will be taken to the portal home page.  From here, add a new game to GameSparks from the drop down menu at the top left. Fill in the name and description. For this tutorial, call the game “GameSparks Tutorial”. Save the project. The first page you see is the Configurator overview. We will manage our API keys from here.   **2) Set up new Facebook App** Open up <http://developer.facebook.com>. Create a new App there; go to: Apps>Create New App and fill in the title, you can use “GameSparks Tutorial” again.   **3) Add Facebook App Keys to GameSparks Project** Now that you’ve set up both new projects, retrieve the Facebook App ID and App Secret from the Dashboard. ![](https://lh5.googleusercontent.com/YFbYpP8eTAULrDpVnoFaQ2Frh4VGts4gfwbDghr63MnBT7FRoBczvzLsB2eiE8E4SDAzmr4Rn0MHAx7RkcViw8UYt4D-uV43HoiIdsdb-GZqqXdphvIAU-A7mt1IAqJeZQ)

Copy/paste them into the Facebook App ID and Facebook App Secret fields in the GameSparks Game Overview menu (Configurator>Integrations>Edit)

![integrations](/wp-content/uploads/2014/10/integrations-1024x471.png)

* * *

###

### Setting up GameSparks and Facebook SDK's in Unity

**1) Download the SDKs** Download the [GameSparks SDK](/uncategorized/unity3d-sdk-v3-new) for Unity and the [Facebook SDK](https://www.google.com/url?q=https%3A%2F%2Fwww.facebook.com%2Fcampaign%2Flanding.php%3Fcampaign_id%3D282184128580929%26placement%3DSDK_6.0.0%26url%3Dhttps%253A%252F%252Fdevelopers.facebook.com%252Fresources%252FFacebookSDK-140805.unitypackage&sa=D&sntz=1&usg=AFQjCNH_6tTQizQFinQAVbaJ0m_lbMMo5w) for Unity. **2) Import the SDKs** You should have the two new SDKs downloaded now. Locate and import them to Unity via Assets>Import Package>Custom Package. ![](https://lh5.googleusercontent.com/9CtovOSjVwSZCb3nmJpDhHXNa9q0EsqykQInD__qhXnkNJDSsQ01oIQNAf2pnk3MDwy6bA7gqWbHVXZjNnzAl8j1nACZHjn41EhYVDAAs0X0JZRuAuRQMx4_ie9ZjhNpig) Unity will process them. You should have two new menu items in Unity now, “GameSparks” and “Facebook”. If not, click on another menu item and they should appear. ![](https://lh4.googleusercontent.com/XiiW_js5_Z6nJQn56G3cZENpXZItWnbwuH73jV9dlujADL_IcTV3LNAdb5MN0MDmJR9zfp9BZemMmIMz4nQJ1EzhgB6Kfcten_3bXbNFyDyNTSkBAf0rmsI4g0WChJ52aw) **3) Add Gamesparks and Facebook App IDs** Under Facebook Settings in Unity (Facebook>Edit Settings) enter the Facebook App ID you retrieved earlier. Then enter the Gamesparks API Key and Secret Key (which you can find on the game overview panel in the Gamesparks portal) via GameSparks>Settings. Make sure you save the scene after entering the keys. You’re all set up, now you just need to test everything to make sure it works.

* * *

###

### Testing the Gamesparks API and Facebook integration

**1) Open Gamesparks TestUI** In the GameSparks > Edit Settings tab in Unity, open the GameSparks test harness by hitting “test configuration” ![](https://lh4.googleusercontent.com/coFiuC7MOkf1A2VMa6_i71pwmLZz4qv7VIJMdPorxOjPisHPq_1GFozulEJ9xWFoe8labltIzKBqagqwXVhpu1uwj_HiOBuou8ZNZ1so2PuBiZM6B63PGxaPgzVdUGUmEw) You will be prompted to save the scene and then the test harness will load. You should see the message that GameSparks is available; Unity is now connected with the GameSparks service. ![](http://i.imgur.com/pyPNtrq.png) ** 2) Send a request to the Gamesparks service** To make sure it's all working correctly send an device authentication request by hitting deviceAuthenticationRequest in the test harness. If GameSparks returns a UserID then everything is running properly. ![](https://lh4.googleusercontent.com/Iy9ZJ84lugvt0lRr1Uo26yS4XxevdG9eToPJG8fVS2gczp50UTq0aB3K4Jm0Nsi2_Ou1rmrhT_4eQKOdrZbR37lJaJf2NtOGu3XacSvvD6z5llvCrVXV0rBewCwXVHnEmg) **3) Test Facebook Connection** To test Facebook connection you need to retrieve an Access Token from the Facebook Developer page. On the developer page navigate to Tools > Access Tokens. If you have just created the app you will need to grant the app permission. Hit “grant permission” and you will be presented with a new UserToken. Copy and paste this into the Access Token field in the Unity Test Harness and then hit facebookConnectRequest  

![](https://lh4.googleusercontent.com/_pCz4hURVBjHMgHaR3cy-ZcCyxea9xwLSIW7nxvzzehbSLZqETb_sdS3wvlvGB4Hn6CJ8J3Ozuk95RqheblZLvryosjwoHZFPVREd6yzwHvYjIymoXwCyNNZBKlsk-XKWQ)

If the Facebook API has been set up in Unity and GameSparks correctly the harness should return a string containing your Facebook details, specifically your name. ![](https://lh3.googleusercontent.com/GmXMdSkwoO8E_MKWfd7efTScqufcfUFG2_-9c0jO7C2Xx6cqqXbrTAoTPbiAz2Sgove87YTOP5z0p5eB6C4AkT2dt9bTl08S3Glkc92Apgk2sMpp2LSKZzyUlFxabw4e1g) That's it for configuring GameSparks and Facebook in Unity, next we will be setting up Facebook authentication for GameSparks in Unity.
