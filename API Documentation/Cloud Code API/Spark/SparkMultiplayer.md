# SparkMultiplayer

Provides access to the platform's multiplayer capabilities.

e.g.

<pre rel="highlighter" code-brush="js" contenteditable="false">var multiplayer = Spark.getMultiplayer();</pre>


## createMatch
_signature_ createMatch(<a href="../Spark/SparkPlayer">SparkPlayer</a>[] players)</p>
_returns_ string</p>
<b>validity</b> All Scripts
Create a match between the given players.
<b>params</b>
players - An array of players to include in the match
<b>returns</b>
The matchId if a match was successfully created, or null
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var matchId = Spark.getMultiplayer().createMatch(player1, player2);</pre>

## createMatchById
_signature_ createMatchById(string[] playerIds)</p>
_returns_ string</p>
<b>validity</b> All Scripts
Create a match between the players for the given playerIds.
<b>params</b>
playerIds - An array of playerIds to include in the match
<b>returns</b>
The matchId if a match was successfully created, or null
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var matchId = Spark.getMultiplayer().createMatchById(playerId1, playerId2);</pre>

## createMatchWithMatchId
_signature_ createMatchWithMatchId(string matchId, <a href="../Spark/SparkPlayer">SparkPlayer</a>[] players)</p>
_returns_ string</p>
<b>validity</b> All Scripts
Create a match between the given players, using the given matchId.
<b>params</b>
matchId - The matchId to use when creating this match
players - An array of players to include in the match
<b>returns</b>
The matchId if a match was successfully created, or null
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var matchId = Spark.getMultiplayer().createMatchWithMatchId("myId", player1, player2);</pre>

## createMatchByIdWithMatchId
_signature_ createMatchByIdWithMatchId(string matchId, string[] playerIds)</p>
_returns_ string</p>
<b>validity</b> All Scripts
Create a match between the players for the given playerIds, using the given matchId.
<b>params</b>
matchId - The matchId to use when creating this match
playerIds - An array of playerIds to include in the match
<b>returns</b>
The matchId if a match was successfully created, or null
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var matchId = Spark.getMultiplayer().createMatchById("myId", playerId1, playerId2);</pre>

## loadMatch
_signature_ loadMatch(string matchId)</p>
_returns_ <a href="../Spark/SparkMatch">SparkMatch</a></p>
<b>validity</b> All Scripts
Load the match with the given matchId
<b>params</b>
matchId - The id of the match to load
<b>returns</b>
The match if a match was found with the given id
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var matchId = Spark.getMultiplayer().loadMatch(matchId);</pre>

