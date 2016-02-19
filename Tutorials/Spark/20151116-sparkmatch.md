title: SparkMatch
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkmatch
author: GameSparks
description: 
post_id: 9649
created: 2015/11/16 15:07:50
created_gmt: 2015/11/16 15:07:50
comment_status: closed
post_name: sparkmatch
status: publish
post_type: post

<!--Provides access to a match's details. -->

# SparkMatch

[toc] 

Provides access to a match's details.

e.g.
    
    
    var match = Spark.getMultiplayer().loadMatch(matchId);

* * *

### getId

**signature** getId()

**returns** string

**validity** All Scripts

**returns**

The id of this match

**example**
    
    
    var matchId = match.getId()

* * *

### getParticipants

**signature** getParticipants()

**returns** [SparkParticipant](../Spark/SparkParticipant)[]

**validity** All Scripts

**returns**

An array containing all of the participants of this match

**example**
    
    
    var participant = match.getParticipants()

* * *

### getServer

**signature** getServer()

**returns** [SparkRealtimeServer](../Spark/SparkRealtimeServer)

**validity** All Scripts

**returns**

The details of the realtime server on which this match will take place.

**example**
    
    
    var server = match.getServer()

* * *

### addPlayers

**signature** addPlayers([SparkPlayer](../Spark/SparkPlayer)[] players)

**returns** void

**validity** All Scripts

Add the given players to this match.

**example**
    
    
    match.addPlayers(playersToAdd)

* * *

### addPlayersById

**signature** addPlayersById(string[] playerIds)

**returns** void

**validity** All Scripts

Add the players with the given playerIds to this match.

**example**
    
    
    match.addPlayersById(playerIdsToAdd)

* * *

### removePlayers

**signature** removePlayers([SparkPlayer](../Spark/SparkPlayer)[] players)

**returns** void

**validity** All Scripts

Remove the given players from this match.

**example**
    
    
    match.removePlayers(playersToRemove)

* * *

### removePlayersById

**signature** removePlayersById(string[] playerIds)

**returns** void

**validity** All Scripts

Remove the players with the given playerIds from this match.

**example**
    
    
    match.removePlayersById(playerIdsToRemove)

* * *

### enableRealtime

**signature** enableRealtime()

**returns** void

**validity** All Scripts

If this match is not already realtime enabled, this method will enabled realtime.

**example**
    
    
    match.enableRealtime();

* * *

### isRealtimeEnabled

**signature** isRealtimeEnabled()

**returns** boolean

**validity** All Scripts

Whether this match has realtime servers enabled.

**example**
    
    
    var isEnabledForRealtime = match.isRealtimeEnabled();