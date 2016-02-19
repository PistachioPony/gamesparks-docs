title: SparkMultiplayer
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkmultiplayer
author: GameSparks
description: 
post_id: 8067
created: 2015/06/10 14:46:40
created_gmt: 2015/06/10 14:46:40
comment_status: closed
post_name: sparkmultiplayer
status: publish
post_type: post

<!--Provides access to the platform's multiplayer capabilities. -->

# SparkMultiplayer

[toc] 

Provides access to the platform's multiplayer capabilities.

e.g.
    
    
    var multiplayer = Spark.getMultiplayer();

* * *

### createMatch

**signature** createMatch([SparkPlayer](../Spark/SparkPlayer)[] players)

**returns** string

**validity** All Scripts

Create a match between the given players.

**params**

players - An array of players to include in the match

**returns**

The matchId if a match was successfully created, or null

**example**
    
    
    var matchId = Spark.getMultiplayer().createMatch(player1, player2);

* * *

### createMatchById

**signature** createMatchById(string[] playerIds)

**returns** string

**validity** All Scripts

Create a match between the players for the given playerIds.

**params**

playerIds - An array of playerIds to include in the match

**returns**

The matchId if a match was successfully created, or null

**example**
    
    
    var matchId = Spark.getMultiplayer().createMatchById(playerId1, playerId2);

* * *

### createMatchWithMatchId

**signature** createMatchWithMatchId(string matchId, [SparkPlayer](../Spark/SparkPlayer)[] players)

**returns** string

**validity** All Scripts

Create a match between the given players, using the given matchId.

**params**

matchId - The matchId to use when creating this match

players - An array of players to include in the match

**returns**

The matchId if a match was successfully created, or null

**example**
    
    
    var matchId = Spark.getMultiplayer().createMatchWithMatchId("myId", player1, player2);

* * *

### createMatchByIdWithMatchId

**signature** createMatchByIdWithMatchId(string matchId, string[] playerIds)

**returns** string

**validity** All Scripts

Create a match between the players for the given playerIds, using the given matchId.

**params**

matchId - The matchId to use when creating this match

playerIds - An array of playerIds to include in the match

**returns**

The matchId if a match was successfully created, or null

**example**
    
    
    var matchId = Spark.getMultiplayer().createMatchById("myId", playerId1, playerId2);

* * *

### loadMatch

**signature** loadMatch(string matchId)

**returns** [SparkMatch](../Spark/SparkMatch)

**validity** All Scripts

Load the match with the given matchId

**params**

matchId - The id of the match to load

**returns**

The match if a match was found with the given id

**example**
    
    
    var matchId = Spark.getMultiplayer().loadMatch(matchId);