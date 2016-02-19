# Using server-authority to identify and respond to client hacking

Introduction Sometimes due to a glitch, unfair advantage or tempering with game logic a player might achieve a score that is well beyond realistic. Scores like these make their way into leaderboards with ease and often it's hard to keep track of them. Cloud code offers you many ways in which you can tackle this. This tutorial will show you an example of how to report anomalies to your devs.  

###Event cloud code

We'll take into account the average score of the first few entries of our leaderboard and double that, if the new score is higher than that we'll flag it as suspected cheating for further investigation. We'll place all of our logic in the event used to upload the score to the leaderboard.

```    
    //Obtain the score
    var score = Spark.getData().SCORE;

    //Make an instance of LeaderboardData request to pull the entries needed
    var request = new SparkRequests.LeaderboardDataRequest();

    //We'll consider the first 7 values of the leaderboard for our average
    var entryCounts = 7;

    //We'll choose the leaderboard we wish to access
    request.leaderboardShortCode = "High_Score_Leaderboard";

    //Pass in the entry count
    request.entryCount = entryCounts;

    //Send request and save response
    response = request.Send();

    //Reference Data
    var entries = response.data;

    //Declare sumScore
    var sumScore = 0;

    //Foreach function
    entries.forEach(processEntry);

    //Add the score of each entry to the average
    function processEntry(entry){

        sumScore += entry.SCORE;
    }

    //The rule to compare to
    var flagScore = (sumScore / entryCounts) * 2;

    //If score goes beyond that score, report it to our devs using the logs
    if (score > flagScore){
        var msg = "Player " + Spark.getPlayer().getUserName() + " is suspected of cheating with a score of" + score;

        Spark.getLog().warn(msg);
    }
  ```  

###Leaderboard

How our leaderboard looks. If a player scores 525+ we'll get a notification to investigate. Players might not be cheating once investigated which means the anti cheating method must improve.

![](/wp-content/uploads/2016/02/bandicam-2016-02-02-17-33-48-881-300x100.jpg)

###The report

How to know a new report has been submitted:

  * Top bar on your configuration screen you have two daily logs summary, one for preview and one for live. If you have issues the bar will be ready and it will ask for the developer's attention and if not the bar will be green and will inform you that there are no issues. Once the bar is clicked you will see a summary of all the type of logs generated for that day.
  How to review it:
  * Head over to the NoSQL tab.
  * Access the script.log runtime collection from the collections menu.
  * Limit the 'levels' search to "WARN" and hit find or the Enter key.

Once done correctly you will be able to review all your 'WARN' logs where we output the suspected cheaters to. In the log you can see the message you've posted, from which event it was fired and the ID of the player associated with it.


![](/wp-content/uploads/2016/02/bandicam-2016-02-03-10-09-06-323-300x159.jpg)

![](https://docs.gamesparks.net/wp-content/uploads/2016/02/bandicam-2016-02-03-09-22-50-332-300x159.jpg)

![](https://docs.gamesparks.net/wp-content/uploads/2016/02/bandicam-2016-02-03-09-27-39-802-300x159.jpg)
