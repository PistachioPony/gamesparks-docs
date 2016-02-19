# Unity Tutorials – Challenges – Part 7: Cloud Code

Tutorial - Challenges for Unity 3D

  * [1. Introduction](/tutorials/unity-tutorials-challenges-part-1-introduction)
  * [2\. Facebook Login](/tutorials/unity-tutorials-challenges-part-2-facebook-login)
  * [3. User Manager](/tutorials/unity-tutorials-challenges-part-3-user-manager)
  * [4. Facebook Friend Manager](/tutorials/unity-tutorials-challenges-part-4-facebook-friend-manager)
  * [5. Challenge, GameInvite and Challenge Manager ](/tutorials/unity-tutorials-challenges-part-5-challenge-gameinvite-and-challenge-manager)
  * [6\. Running Game, Challenge Manager Part 2 & Testing](/tutorials/unity-tutorials-challenges-part-6-running-game-challenge-manager-part-2-testing)
  * [7\. Cloud Code](/tutorials/unity-tutorials-challenges-part-7-cloud-code)
  * [8\. Hooking Everything Up](/tutorials/unity-tutorials-challenges-part-8-hooking-everything-up)

This is part 7 of an 8 part tutorial, it's recommended that you look at the previous section before continuing. In this section we will be writing the cloud code that lets us sync the game state to GameSparks.

* * *

##

## Creating the Events

First thing we have to set up in GameSparks is our events, select Events from the side panel and then press the plus icon in the top right to start a new event. Call it "takeTurn", enter a description and enter "takeTurn" as the short code. Then, add a two attributes, one called Position with the short code "pos" that takes "Number" as its Data Type and set the Default Calc to "used in script". The second can be called "Player Icon" with the shortcode "playerIcon" that takes a "String" as its Data Type and also has Default Calc set to "used in script". ![](https://lh3.googleusercontent.com/5gz9HIllMxI0NYimArElETpQVkVR1eXftZ3un5nh6sOyhjYvn3kTfmzf-vDbF900ZWHajn6FP4EFY7DX1gVaX1Z-MteMsXTV_svFv6PJFqU1VtgPq2-ILwqs0EtYH1riPw) Now head down to challenges and edit the challenge we created earlier. Select turn event consumer and now there is an option to select the event we just created. Select it. Now whenever we call the event "takeTurn" its going to take a turn from our challengers. ![](https://lh6.googleusercontent.com/v8RqKhuVcZ2wDeYO34pYFuaLbT2zRJglNewj8C2xvD7hkafPMWIEsLA95x-jELo-yzfztNUFb49Fy3CL8Dx_I_KR8Zj_xA6injSPmtcZ783uZJoIsPD8jdfXgsoJOiKKUg)

* * *

##

## Writing our Cloud Code

Open up Cloud Code from the side bar in the Configurator and then select Global Messages and scroll down until you can find Challenge Started Message. Challenge Started Message is called whenever a challenges is started, now when a challenges is issued. ![](https://lh3.googleusercontent.com/0wOUPRqHzUThK5O8FUSpyrOmSs9JFW4Iixq9sUXZrMppG79bursZnOU_Z9hEg7wKq4R92f9cnSGmXFfp8mawniDew9Z36JqCQkTVEQD9gbivMXZU4KiQDXgRkxpuqfZaPw) Now it’s time to write the code, a commented copy of the Challenge Started Message code is provided below:


    //Get our challenge information so we can store ScriptData to it.
    var challenge = Spark.getChallenge(Spark.data.challenge.challengeId);

    //This is our TicTacToe board.
    var gameBoard = ["","","", "","","", "","",""];

    //We save our board to this challenge instance with a key value pair.
    challenge.setScriptData("gameBoard", gameBoard);

Next we need to select Challenge Events and from there select our takeTurn event. ![](https://lh4.googleusercontent.com/1i5ld1CZAS3pXD5YujtOFOPa5cMsjBesarmThHziFHPmbmfL3P2bivFdAt1gYlku9C2UbowGxswaYrNRX3reZzaHOGQcYpL_TrjHQnX4xc-2A58ypRxtWYKQPVqv0TH07Q) The code we are going to write is below, this is how set the players positions on the boards and check who won the game:


    //Get our challenge information so we can store ScriptData to it.
    var challenge = Spark.getChallenge(Spark.data.challengeInstanceId);

    //We get the gameBoard we created in ChallengeStartedMessage
    var gameBoard = challenge.getScriptData("gameBoard");

    play();

    function play()
    {
       //We create a variable to accept the attributes we pass on to our event
       var pos = Spark.data.pos;
       var playerIcon = Spark.data.playerIcon;

       //We set the playerIcon (x or o) to a position on the gameBoard
       gameBoard[pos] = playerIcon;

       //We update our and save our gameBoard
       challenge.setScriptData("gameBoard", gameBoard);

       //Check to see if we've won
       if(checkWinner(playerIcon)){
           //If we have won, save the winner's name to ScriptData so we can easily reference
           //it when searching for "COMPLETED" games
           challenge.setScriptData("winner", Spark.player.displayName);

           //Set this challenge instance to won and which player won it.
           challenge.winChallenge(Spark.player);
       }

       //Check for a draw
       if(checkDraw())
       {
           //Save the "winner" as draw, so we can easily reference it when
           //search for "COMPLETED" games
           challenge.setScriptData("winner", "Draw");

           //En the challenge on a draw
           challenge.drawChallenge();
       }
    }

    //Check if we have three adjacent of our icon
    function checkWinner(playerIcon)
    {
      if (gameBoard[0] == playerIcon && gameBoard[1] == playerIcon && gameBoard[2] == playerIcon) return true;
                    else if (gameBoard[3] == playerIcon && gameBoard[4] == playerIcon && gameBoard[5] == playerIcon) return true;
                    else if (gameBoard[6] == playerIcon && gameBoard[7] == playerIcon && gameBoard[8] == playerIcon) return true;
                    else if (gameBoard[0] == playerIcon && gameBoard[3] == playerIcon && gameBoard[6] == playerIcon) return true;
                    else if (gameBoard[1] == playerIcon && gameBoard[4] == playerIcon && gameBoard[7] == playerIcon) return true;
                    else if (gameBoard[2] == playerIcon && gameBoard[5] == playerIcon && gameBoard[8] == playerIcon) return true;
                    else if (gameBoard[0] == playerIcon && gameBoard[4] == playerIcon && gameBoard[8] == playerIcon) return true;
                    else if (gameBoard[2] == playerIcon && gameBoard[4] == playerIcon && gameBoard[6] == playerIcon) return true;
                    else return false;
    }

    //Check if no space is empty
    function checkDraw()
    {
       for(i=0; i<8; i++)
       {
           if(gameBoard[i]=="")
           {
            return false;   
           }

       }

       return true;
    }

* * *

##

## Testing

Now we can test out our cloud code, but first we have to delete the Challenges we already sent as a test in case they interfere with anything. Select NoSQL and from the Collections drop down select challengeInstance. Click Find and then delete all the challenge instances by clicking into them and then clicking the bin icon.
