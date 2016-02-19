# Unity Tutorials – Challenges – Part 5: Challenge, GameInvite and Challenge Manager

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 5 of an 8 part tutorial, it's recommended that you look at the previous section before continuing. In this section we will be creating our challenge on the [GameSparks Portal](http://portal.gamesparks.net), writing our GameInvite script and starting our ChallengeManager.

* * *

##

## Creating a Challenge in the GameSparks Portal

To start with we’re going to create a challenge in the [GameSparks Portal](http://portal.gamesparks.net) that we will reference with our code. Open the GameSparks Portal, click the Challenges tab and create a new challenge by pressing the Plus button in the top corner. Call the challenge Tic Tac Toe, give it a short code of "ticTacToe" and a description. Switch “Turn Based” to On and set Leaderboard to scripted outcome. ![](https://lh3.googleusercontent.com/pYOwpA96sUHNv2fUPH4H09yv3fkck6x1ruOH9Pf4WMtE_K4I1nqJTb1Gz2RGkDjOFp9xtEwOrypzAP-kdqtfYvbbH6yPk2vuHS3uHaBXAcDfDSw4yDobKFPqKASkmBfbgw) Now that the challenge has been created we can write the scripts in Unity that will use it.

* * *

##

## Write the GameInvite script

In Unity, open up the GameInvite prefab so that we know what we’re coding for. You can find it in Assets>Resource>Prefabs>GameInvite. Drag it into the scene and you'll see this: ![](https://lh5.googleusercontent.com/eZdSLgvANe_D7_8yex4-EFHGgj25eRufAwibZxFGurThs8keJp1KWegpXNxSsK41QYTPW4CB9hJM_cOfcut6t0oqzs56zxW809DyCSrCpFWQREx4-gBtLxJIiuOFJdKRng) The areas that we will need to fill is the name of the person who challenged us, a text field that tells us when the challenge expires, a picture of the person who has challenges us and two buttons, one for accepting and one for declining the challenge. Create a script in the Scripts folder and call it GameInvite. As before feel free to use the code provided, just make sure that any short codes we use to reference GameSparks in our example are changed to whatever short code you assign in your GameSparks Portal.


    using UnityEngine;
    using System.Collections;
    using GameSparks.Api.Requests;

    public class GameInvite : MonoBehaviour
    {
            //ChallengeId is the important variable here, we use to reference the specific challenge we are playing
            public string inviteName, inviteExpiry, challengeId, facebookId;


            //We use canDestroy to let the Tween Alpha know it's safe to remove the gameObject OnFinish animating
            public bool canDestroy = false;

            public UILabel inviteNameLabel, inviteExpiryLabel;
            public UITexture profilePicture;

            // Use this for initialization
            void Start ()
            {
                    inviteNameLabel.text = inviteName + "has invited you to play";
                    inviteExpiryLabel.text = "Expires on " + inviteExpiry;
            }

            //This in the function we call OnClick
            public void AcceptChallenge()
            {
                    //We set the Challenge Instance Id and Message of AcceptChallengeRequest
                    new AcceptChallengeRequest().SetChallengeInstanceId(challengeId)
                            .SetMessage("You're goin down!")
                            .Send((response) =>
                            {
                                    if (response.HasErrors)
                                    {
                                            Debug.Log(response.Errors);
                                    }
                                    else
                                    {
                                            //Since this challenge is no longer an invite, we need to update our running games
                                            ChallengeManager.instance.GetRunningChallenges();

                                            //Once we accept the challenge we can go ahead and remove the gameObject from the scene
                                            canDestroy = true;
                                    }
                            });
            }

            public void DeclineChallenge()
            {
                    //We set the Challenge Instance Id and Message of DeclineChallengeRequest
                    new DeclineChallengeRequest().SetChallengeInstanceId(challengeId)
                            .Send((response) =>
                            {
                                    if (response.HasErrors)
                                    {
                                            Debug.Log(response.Errors);
                                    }
                                    else
                                    {
                                            //Once we decline the challenge we can go ahead and remove the gameObject from the scene
                                            canDestroy = true;
                                    }
                            });
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

            //When our tween is finished and we've accepted or declined the invite, we no longer need it
            public void DestroyAfterTween()
            {
            //remove game invite from the list of invites
            }
    }

You will only be able to write some sections of this code after completing this part and writing the next script, namely the DestroyAfterTween function which references the Challenge Manager that we have yet to write. For the time being you can add a comment within the variable in place of the code as a reminder to come back and complete it later.

* * *

##

## Adding the GameInvite script to the GameInvite prefab
