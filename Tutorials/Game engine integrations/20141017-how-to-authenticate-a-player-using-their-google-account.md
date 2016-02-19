# How to authenticate a player using their Google+ account

[toc] Google+ authentication allows you to provide your players with a simple way to sign in with their Google+ account, and allows the GameSparks platform to then use the player's profile to drive its social features. In this exercise you'll go through setting up the necessary configuration with Google and how you can then use that to connect your players.

## Setting up an application with Google

**1.**  Head over to the **[Google Developer Console](https://console.developers.google.com)** and sign in if you already have an account.  Sign up if you don't. **2.  **Go to **[ Google Play Game Services](https://developers.google.com/games/services/)**.  Follow the relevant "_Getting Started_" section based on the application type that you are creating by navigating to [Set up Play Games Services](https://developers.google.com/games/services/console/enabling).  The most important step to understand is the "_Add your game to the Google Play Developer Console_". **TIP:**  If you've got time, it's worth a read.  There is a wealth of information hidden away in these pages). If you're targeting more than one platform (Android, IOS, Web etc...), just pick one to start with - a chunk of the setup will only need to be done once. **3.  **While setting up your application in the **Google Play Developer Console**, also add a "Web" linked application.  This will serve as our "Server" client in later steps. It's important that this be created through the [Google **Play** Developer Console](https://play.google.com/apps/publish/) (rather than the standard Google **Developer** Console), otherwise when we try to get a token later it will fail to work correctly. ![Screen Shot 2015-05-26 at 12.45.05](/wp-content/uploads/2014/10/Screen-Shot-2015-05-26-at-12.45.05.png)   **4.  **Make a note of the **OAuth Client Id**** **that is generated once the application is set up. ![Screen Shot 2015-05-26 at 15.47.05](https://docs.gamesparks.net/wp-content/uploads/2014/10/Screen-Shot-2015-05-26-at-15.47.05.png)   **5.  **After setting up the application, follow the steps from the [Google+ documentation](https://developers.google.com/+/). The relevant section is "_Enable server-side API access for your app_", located [here for Android](https://developers.google.com/+/mobile/android/sign-in#enable_server-side_api_access_for_your_app) and [here for iOS](https://developers.google.com/+/mobile/ios/sign-in#enable_server-side_api_access_for_your_app) (for a web application the relevant section is under [Server Side Flow](https://developers.google.com/+/web/signin/server-side-flow)). This will show you how you are going to get hold of the access code that we need to pass through to the server later on. Wherever the instructions talk about "_your server's client ID_", is where we need to substitute in the **OAuth Client Id** from the Web application we created within **Google Play Developer Console**. If you begin to distribute your game on more than one device, it's always this Web Application that we use as the "Server" Client ID. When requesting the token, you are required to provide the "**scopes**" of the token which determine what you can gain access to.  Currently, the only scope we require to support our social features is "https://www.googleapis.com/auth/plus.login". **6.  **Go into the [Google **Developer** Console](https://console.developers.google.com), select your project and under **APIs & auth** and click **Consent Screen**. **7.  **Fill in the **Email Address** and **Product Name** fields, click **Save**. Again, without doing this we can end up with some failures later on. ![](https://docs.gamesparks.net/wp-content/uploads/2014/10/consent.png)

## Configuring your GameSparks game

Now we've done that, here comes the easy part. **8.  **Go into the [GameSparks Developer Portal](https://portal.gamesparks.net/) for the game, and go to **Configurator** > **Integrations**. **9.  **Select the **Google** tab and click **Edit**. ![Screen Shot 2015-05-26 at 17.52.31](/wp-content/uploads/2014/10/Screen-Shot-2015-05-26-at-17.52.31.png)   While you can view the Application Client Id through the [Google **Play** Developer Console](https://play.google.com/apps/publish/), you can only access the Client Secret under the standard [Google **Developer** Console](https://console.developers.google.com), see screenshot below). ![](https://docs.gamesparks.net/wp-content/uploads/2014/10/Screen-Shot-2015-05-27-at-11.08.021.png) **10.  **Fill in the fields **Application Client Id** and **Application Client Secret** using the **Oauth Client Id** and **Secret** from your Google Web Application and click **Save**. ![](https://docs.gamesparks.net/wp-content/uploads/2015/06/Screen-Shot-2015-06-05-at-11.55.56.png)   That's all there is to it. Now we're ready to make a **GooglePlusConnectRequest**. **11.  **Get an access code using the method described in the relevant Google documentation above, then go to the [Test Harness](https://portal.gamesparks.net/testHarness.htm). **12.  **Under **Authentication**, choose the **GooglePlusConnectRequest**. You can now send the access code through as the "code" parameter, and your Google+ profile will be connected!


     { "@class": ".GooglePlusConnectRequest",
       "code": "4/kHkxY8JbQ4bDBxabWyHyrVI3oROi8LcF_Fk25DF3bWM.QpEEsFOJzU8RJvIeHux6iLahn6g8kgI",
     }

Response:


     {
     "@class": ".AuthenticationResponse",
     "authToken": "1c9314ad-6309-40aa-9ef6-03544047c78a",
     "displayName": "David Clark",
     "requestId": "1413552906008",
     "scriptData": null,
     "userId": "5418461b1c26e32e438653d4"
     }

  That's it!  You are now authenticated with Google! As a basic setup of the Google authentication, these are the only steps you will need. However, if you are interested in knowing other alternative ways on how to authenticate your Players with Google, then read on...

## Authenticating via the Redirect URI

If you have a local web server available, it can be used to authenticate your game and Client ID to generate an access code using a **redirect** **URI.  **The resulting POST message will contain the access code to authenticate your Google Plus account with the GameSparks platform. **13.  **On your local web server, you will need to create a HTML page that will contain the Google Sign in button.  The HTML page should contain the following pre-requisites:
