# Unity Tutorials – Challenges – Part 6: Running Game, Challenge Manager Part 2 & Testing

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 6 of an 8 part tutorial, it's recommended that you look at the previous section before continuing. In this section we’re going to write our RunningGame entry, we will finish the ChallengeManager and we will test to make sure everything is working in the GameSparks portal and in our Unity scene.

* * *

##

## Creating the RunningGame script

This is the script that will manage the game while its running. It will check to see who we are playing against, whose turn it as and will also manage the start of our games, assigning players to be Player 1 and Player 2 and defining turn order. The script is provided below, at this point it is not complete as there are some sections of work we have to do in the [GameSparks Portal](http://portal.gamesparks.net) before we can finish it off.


    using UnityEngine;
    using System.Collections;
    using System.Collections.Generic;

    public class RunningGame : MonoBehaviour
    {

    	//We store the challengeId, next player's userId and the userId who initiated the challenge.
    	public string challengeId, turnStatus, challengerId;

    	//We create a list for playerNames and Ids
    	public List<string> playerNames = new List<string>();
    	public List<string> playerIds = new List<string>();

    	//This is the array of strings we pass our Cloud Code gameBoard to
    	public string[] gameBoard;

    	//We use canDestroy to let the Tween Alpha know it's safe to remove the gameObject OnFinish animating
    	public bool canDestroy = false;

    	public UILabel challengeLabel, statusLabel;

    	// Use this for initialization
    	void Start()
    	{
    		//We set the challenge label with the names of both players
    		challengeLabel.text = playerNames[0] + " VS " + playerNames[1];

    		//We then check if the userId of the next player is equal to ours
    		if (turnStatus == UserManager.instance.userId)
    		{
    			//If it is, then we say it's your turn
    			statusLabel.text = "Your Turn!";
    		}
    		else
    		{
    			for (int i = 0; i < playerIds.Count; i++)
    			{
    				//else find the player whose Id does match and return their name
    				if (playerIds[i] == turnStatus)
    				{
    					statusLabel.text = playerNames[i] + "'s Turn!";
    				}
    			}
    		}
    	}

    	//Start game gets called OnClick of the play button
    	public void StartGame()
    	{
    	//we will complete this function in the future
    }

    	//When our tween is finished and we've accepted or declined the invite, we no longer need it
    	public void DestroyAfterTween()
    	{
    		if (canDestroy)
    		{
    			//First remove the gameObject from it's list, so we don't end up with a null reference when we destroy it
    			ChallengeManager.instance.gameInvites.Remove(gameObject);

    			//Then destroy the gameObject, removing it from the scene.
    			Destroy(gameObject);
    		}
    	}
    }


  That’s the RunningGame script done for now, with that written we can return to our Challenge Manager and add in some more code that references the RunningGame script.

* * *

##

## Editing the ChallengeManager script

We have to edit the ChallengeManager to pull together a list of Running Challenges.  Find the empty GetRunningChallenges function we wrote in the ChallengeManager script last time and add in the following:


    public void GetRunningChallenges()
    	{
    		//Every time we call GetChallengeInvites we'll refresh the list
    		for (int i = 0; i < runningGames.Count; i++)
    		{
    			//Destroy all runningGame gameObjects currently in the scene
    			Destroy(runningGames[i]);
    		}
    		//Clear the list of friends so we don't have null reference errors
    		runningGames.Clear();

    		//We send a ListChallenge Request with the shortcode of our challenge, we set this in our GameSparks Portal
    		new ListChallengeRequest().SetShortCode("ticTacToe")
    			.SetState("RUNNING") //We want to get all games that are running
    			.SetEntryCount(50) //We want to pull in the first 50
    			.Send((response) =>
    			{
    				//For every challenge we receive
    				foreach (var challenge in response.ChallengeInstances)
    				{
    					//Create a new gameObject, add runningPrefab as a child of the running Grid GameObject
    					GameObject go = NGUITools.AddChild(runningGrid.gameObject, runningPrefab);

    					//Set our variables
    					go.GetComponent<RunningGame>().challengeId = challenge.ChallengeId;
    					go.GetComponent<RunningGame>().turnStatus = challenge.NextPlayer;

    					//For every player in the collection of players who have accepted the challenge
    					foreach (var player in challenge.Accepted)
    					{
    						//Add their names and their Ids to the list i each respective Running Game Entry
    						go.GetComponent<RunningGame>().playerNames.Add(player.Name);
    						go.GetComponent<RunningGame>().playerIds.Add(player.Id);
    					}

    					go.GetComponent<RunningGame>().challengerId = challenge.Challenger.Id;

    					//We've saved the gameBoard in the cloud in ScriptData, we saved it as a String List and we need to convert it to a Unity Array
    					go.GetComponent<RunningGame>().gameBoard = challenge.ScriptData.GetStringList("gameBoard").ToArray();

    					//Add the gameObject to the list of friends
    					runningGames.Add(go);

    					//Tell the grid to reposition everything nicely
    					runningGrid.Reposition();
    				}
    			});
    	}

* * *

##

## Adding the RunningGame script to the Running Game prefab

Open up the Running Game Prefab in Unity Resources>Prefabs>Running Game and drag it into the scene, then add the RunningGame script to it. Then fill in the empty field as we have done before, drag “GameName” to the “Challenge Label” field, drag “Game Status” to the “Status Label” field. ![](https://lh3.googleusercontent.com/XlQNaoFwH_K5xCxh-CA7FgXf1-rNqXMn1KWkR4i8uVmF_6yf1JuA_lWCwbffFELOdl5SLwVriYXicOJfjdVxu_1VDsFIxSLiDGzPQg-vx6zljXArJKtPbJkfqu2_2p8IsA)
