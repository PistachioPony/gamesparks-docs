# Unity Tutorial - Leaderboards - Part 3: Logging in to GameSparks with Facebook

Tutorial - Leaderboards for Unity 3D

  * [1. Introduction](/uncategorized/unity-tutorial-introduction)
  * [2. Configuring GameSparks for Facebook Authentication](/uncategorized/unity-tutorial-configuring-gamesparks-for-facebook-authentication)
  * [3. Logging in to GameSparks with Facebook](/uncategorized/unity-tutorial-logging-in-to-gamesparks-with-facebook)
  * [4. Creating And Testing GameSparks Leaderboards](/uncategorized/unity-tutorial-creating-and-testing-gamesparks-leaderboards)
  * [5. Creating Leaderboard Prefabs & Posting Scores](/uncategorized/unity-tutorial-creating-leaderboard-prefabs-posting-scores)
  * [6. Getting profile pictures for Leaderboard Entries](/uncategorized/unity-tutorial-getting-profile-pictures-for-leaderboard-entries)

This is part  3 of a 6 part tutorial, it's recommended that you look at the previous section before continuing. In this section, you’ll be setting up Unity to use Facebook as a log in for GameSparks when your game starts. We’ve provided the code below necessary for the exercise.   **1) Logging into GameSparks with Facebook** To get the most out of GameSparks, it’s best to log users in silently as soon as the game starts. This way GameSparks is accessed for data (such as updated leaderboards, daily quests, p2p challenges etc.) immediately. We have a script below that initialises and logs into Facebook. Read through the comments to make sure you understand how it works before adding it to your game.



    using UnityEngine;
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

    }


  **2) Add Script to Hierarchy** Create a new Empty Game Object in Unity (GameObject>CreateEmpty) and add the script above as a new C# Script component. Also add the GameSparksUnity.cs script found in Assets>GameSparks to the object. This script needs to be added to your game so that GameSparks will work. ![](https://lh6.googleusercontent.com/w-CwcoILxfvx2bCopph_aalRyqFDcASdYaQ-t7D_TeoA-MI2k3IUzMIomTFDmCYBtE54nmN8KQ8U15HAna4hNSc8eTw4xMpKH7KtNStKvxWQznYN00YIc6dVFxAYMfjkrw) If this object is in the opening scene of your game, say, the Main Menu scene then Facebook will log the client into GameSparks on start-up. Call the object “API Manager”. ![](https://lh5.googleusercontent.com/C8LD4rN2wdqJe-z0nTQDPgdeM7-cjX8nHSrksMzaXWG5D4fC4U2AEHOR99GLUegmAkVvk6DwFp0RObk-V5yuwjG05Meq76rj4Rg_8z9q_BUIdTG5kCQs2jOsuxKCzagw4Q) **3)Testing it out** When you click Play in the Unity editor you will be able to see the Facebook initialization running in the background. The access token request will pop up. ![](https://lh5.googleusercontent.com/dLWTz3bqybxP9KjRBEaLGhXyvR1KqcIU7ON5qTJ_Giq8kxocW3kZgK-lu3WhG65eRArxNXQsK3zFApLS_ejLXCAeDzb0ApWgFCixELluOcn2gdfpQXoYVDSRAc3dO8TooA)   Paste your access token retrieved in the last exercise from the developers.facebook.com page and click Login. The Unity Console will  get a message from GameSparks, if you see your name after “displayName” you’ve successfully logged into Facebook. ![](https://lh6.googleusercontent.com/Pe5719oytz97qmOSMR75YhbRAz4XvD2yuHnKpEjkYIkLp_rTwxspXfGfU259XtKcgRMqerKeLqTevXU_k8qRx242Ax-HrBrCj34u9Xm9gI2YYUm8kUJawsqlCs9AypfXyQ) In the next section we will be setting up our leaderboard in the GameSparks portal, creating our Post Score Events and looking at the GameSparks Test Harness. Don't forget to check the [developer forum](https://support.gamesparks.net/support/discussions) if you have any questions, or with the GameSparks team at [info@gamesparks.com](mailto:info@gamesparks.com)
