# How to access Leaderboards via Cloud Code

Imagine the scenarios where you want to determine the position of given player within a Leaderboard or that you want to get the player id of whoever is at a given position. You can implement these two features using the Cloud Code [SparkRequests API](/documentation/cloud-code-api/sparkrequests-api), the API allows requests to be sent either as the current player or as any other player within your game.

To find the rank of a given player use a [LeaderboardDataRequest](https://docs.gamesparks.net/documentation/request-api/leaderboards-request-api/leaderboarddatarequest) which will return the data associated with the player:

```    
    var request = new SparkRequests.LeaderboardDataRequest();
    request.entryCount = 1;
    request.leaderboardShortCode = "leaderboardSC";

    var response = request.Send();
```

Now you'll have GameSparks response stored in your response variable as a JSON object.
