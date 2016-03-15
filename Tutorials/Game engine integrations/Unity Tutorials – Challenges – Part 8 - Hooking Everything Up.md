# Unity Tutorials – Challenges – Part 8: Hooking Everything Up

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 8 of an 8 part tutorial, it's recommended that you look at the previous section before continuing. In this final section we will edit the Running Game entry and Challenge Manager scripts we wrote earlier to take the game board from Cloud Code and pass it to a new instance of Tic Tac Toe. We will also add the log challenge event to the ticTacToe script and make sure that it works.

* * *

##

## Editing RunningGame

Open up the RunningGame Script. The edits we need to make are shown below. In the StartGame function we set up before, add in the following. This function will manage whose turn it is to play and it will toggle the visibility of the game board.


    public void StartGame()
            {
                    //Clear any previous instances of Tic Tac Toe
                    ticTacToe.instance.ClearInstance();

                    //Pass the gameBoard we got from Cloud Code to the Tic Tac Toe instance
                    ticTacToe.instance.gameBoard = gameBoard;

                    //Update the Tic Tac Toe game instance's challenge Id to the current one
                    ticTacToe.instance.challengeInstanceId = challengeId;

                    //If we initiated the challenge, we get to be player 1
                    if (challengerId == UserManager.instance.userId)
                    {
                            ticTacToe.instance.isPlayerOne = true;
                    }
                    //Otherwise we're player 2
                    else
                    {
                            ticTacToe.instance.isPlayerOne = false;
                    }

                    //If the user Id of the next player is equal to ours then it's out turn
                    if (turnStatus == UserManager.instance.userId)
                    {
                            ticTacToe.instance.currentPlayerTurn = true;
                    }
                    //Otherwise it's not
                    else
                    {
                            ticTacToe.instance.currentPlayerTurn = false;
                    }

                    //We've passed enough information for the Tic Tac Toe instance to construct the board
                    ticTacToe.instance.GetBoard();

                    //Tween the alpha of the Challenges screen so we can see the game board
                    GUIManager.instance.challengeAlpha.Toggle();
                    GUIManager.instance.challengesPos.Toggle();

                    //We've done everything we can do with the Running Game Entry, so we can remove it from the scene.
                    canDestroy = true;
            }

* * *

 

##

## Editing ChallengeManager

Now open up the ChallengeManager script. We need to add the following lines to our GetRunningChallenge function now that it’s complete. From line 96, just above runningGames.Add(go);, add in the following lines:


    					go.GetComponent<RunningGame>().challengerId = challenge.Challenger.Id;

    					//We've saved the gameBoard in the cloud in ScriptData, we saved it as a String List and we need to convert it to a Unity Array
    					go.GetComponent<RunningGame>().gameBoard = challenge.ScriptData.GetStringList("gameBoard").ToArray();

Now when we get our running challenges we are going to get the challengerId and gameBoard array.

* * *

 

##

## Editing the Tic Tac Toe script

The final bit of editing we have to do is in the Tic Tac Toe game script. In set pieces we have to write our log Challenge event now that the challenge has been created in GameSparks. Around line 83 within the Set Piece function add the following code:


    //We use LogChallengeEventRequest with the challenge Instance Id of this particular game.
                            new LogChallengeEventRequest().SetChallengeInstanceId(challengeInstanceId)
                                    .SetEventKey("takeTurn") //The event we are calling is "takeTurn", we set this up on the GameSparks Portal
                                    .SetEventAttribute("pos", pos) //takeTurn has an attribute for position called "pos", we supply it with the pos we placed our icon at
                                    .SetEventAttribute("playerIcon", playerIcon) //takeTurn also has an attribute called "playerIcon, we set to our X or O
                                    .Send((response) =>
                                    {
                                            if (response.HasErrors)
                                            {

                                            }
                                            else
                                            {
                                                    // If our ChallengeEventRequest was successful we inform the player
                                                    sent.PlayForward();
                                            }
                                    });

* * *

 

##

## Testing

One final bit of testing to make sure everything is working. Log in two of our Facebook test users as we did in part 6, one into the game via Unity and another test user through the GameSparks Test Harness. Once you have both test users logged in open up the friend list in Unity and send a Challenge request to the online test user we logged in via the Test Harness. Then, from the GameSparks Test Harness accept the Challenge request. Now when we go back to Unity and hit the VS button we will see an ongoing challenge panel with “Your Turn”. ![](https://lh4.googleusercontent.com/bHuzhL20kwMVcxLJic3DZ4qPMeqIDT2k-7uemqRuOCkOH7L1RP-i5mHjJyy-vTwvUp6JqWSeLk3MVwISmpywCPbSGlJEyQOHSiUL0t0UVHVD2bFlQw9rLnxDOOMfrVDKGg) Take the turn, select the center square. A “Turn Sent!” message will pop up which means our Challenge response is positive. ![](https://lh6.googleusercontent.com/EA5mstFO6q-FwNApcnGHaEuhNzHYJdF_TrmT3gsX-B-gOk8ikeVzJncHc6ciNay2YrIniWB-sRPrQ4vLmXBW9AFyyR7hxWy-VmmVQGS98-HLeD-6cgJhF_3kFPYV-nx_OA)
