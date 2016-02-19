title: SparkLeaderboards
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkleaderboards
author: GameSparks
description: 
post_id: 4583
created: 2014/08/14 10:26:27
created_gmt: 2014/08/14 10:26:27
comment_status: closed
post_name: sparkleaderboards
status: publish
post_type: post

<!--Provides access to the leaderboards for the current game. -->

# SparkLeaderboards

[toc] 

Provides access to the leaderboards for the current game.
    
    
    var leaderboards = Spark.getLeaderboards();

* * *

### getLeaderboard

**signature** getLeaderboard(string shortCode)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a SparkLeaderboard object by its shortCode.

**params**

shortCode - the shortCode of the leaderboard.

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getLeaderboard(shortCode);

* * *

### getSocialLeaderboard

**signature** getSocialLeaderboard(string shortCode, string[] friendIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode, where the social group contains the current player and the players with the given playerIds.

If no playerIds are provided the player's game friends are used.

**params**

shortCode - the shortCode of the leaderboard.

friendsIds - the ids of the other players to be included in this social leaderboard.

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getSocialLeaderboard(shortCode, myplayerids);

* * *

### getInverseSocialLeaderboard

**signature** getInverseSocialLeaderboard(string shortCode, string[] friendIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode for the current player, where the social group excludes the players with the given playerIds.

If no playerIds are provided the player's game friends are used.

**params**

shortCode - the shortCode of the leaderboard.

friendsIds - the ids of the other players to be excluded from this social leaderboard.

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getInverseSocialLeaderboard(shortCode, myplayerids);

* * *

### getSocialLeaderboardAs

**signature** getSocialLeaderboardAs(string shortCode, string playerId, string[] friendIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode, where the social group contains the player with the given playerId and the players with given playerIds.

If no playerIds are provided the player's game friends are used.

**params**

shortCode - the shortCode of the leaderboard.

playerId - the playerId to load the social leaderboard for.

friendsIds - the ids of the other players to be included in this social leaderboard.

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getSocialLeaderboardAs(shortCode, myplayerid, myplayerids);

* * *

### getInverseSocialLeaderboardAs

**signature** getInverseSocialLeaderboardAs(string shortCode, string playerId, string[] friendIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode for the given player, where the social group excludes the players with the given playerIds.

If no playerIds are provided the player's game friends are used.

**params**

shortCode - the shortCode of the leaderboard.

playerId - the playerId to load the social leaderboard for.

friendsIds - the ids of the other players to be excluded from this social leaderboard.

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getInverseSocialLeaderboardAs(shortCode, myplayerid, myplayerids);

* * *

### getTeamLeaderboard

**signature** getTeamLeaderboard(string shortCode, string[] teamIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode, where the social group contains the current player and the players belonging to the teams with the given teamIds

**params**

shortCode - the shortCode of the leaderboard.

teamids - the ids of the teams to be included in this social leaderboard

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getTeamLeaderboard(shortCode, myteamids);

* * *

### getInverseTeamLeaderboard

**signature** getInverseTeamLeaderboard(string shortCode, string[] teamIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode for the current player, where the social group excludes the players belonging to the teams with the given teamIds

**params**

shortCode - the shortCode of the leaderboard.

teamids - the ids of the teams to be excluded from this social leaderboard

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getInverseTeamLeaderboard(shortCode, myteamids);

* * *

### getTeamLeaderboardAs

**signature** getTeamLeaderboardAs(string shortCode, string playerId, string[] teamIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode, where the social group contains the player for the given playerId and the players belonging to the teams with the given teamIds

**params**

shortCode - the shortCode of the leaderboard.

playerId - the playerId to load the social leaderboard for.

teamids - the ids of the teams to be included in this social leaderboard

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getTeamLeaderboard(shortCode, myplayerid, myteamids);

* * *

### getInverseTeamLeaderboardAs

**signature** getInverseTeamLeaderboardAs(string shortCode, string playerId, string[] teamIds)

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)

**validity** All Scripts

Allows a script to load a social SparkLeaderboard object by its shortCode for the given player, where the social group excludes the players belonging to the teams with the given teamIds

**params**

shortCode - the shortCode of the leaderboard.

playerId - the playerId to load the social leaderboard for.

teamids - the ids of the teams to be excluded from this social leaderboard

**example**
    
    
    var leaderboard = Spark.getLeaderboards().getInverseTeamLeaderboard(shortCode, myplayerid, myteamids);

* * *

### listLeaderboards

**signature** listLeaderboards()

**returns** [SparkLeaderboard](../Spark/SparkLeaderboard)[]

**validity** All Scripts

Gives access to all leaderboards configured for the game

**example**
    
    
    var leaderboards = Spark.getLeaderboards().listLeaderboards();

* * *

### getChallengeLeaderboard