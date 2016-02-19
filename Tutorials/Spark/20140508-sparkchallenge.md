title: SparkChallenge
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkchallenge
author: gabriel.page
description: 
post_id: 2397
created: 2014/05/08 10:57:41
created_gmt: 2014/05/08 10:57:41
comment_status: closed
post_name: sparkchallenge
status: publish
post_type: post

<!--Provides access to a challenge's details. -->

# SparkChallenge

[toc] 

Provides access to a challenge's details.

e.g.
    
    
    var challenge = Spark.getChallenge(mychallengeid);

* * *

### getRunState

**signature** getRunState()

**returns** string

The run state of the object. Valid states are:

ACCEPTED - All players have accepted the challenge

WAITING - The challenge is in it's waiting state, between expiryDate and startDate

RUNNING - The challenge is running

COMPLETE - The challenge is complete

DECLINED - All players have declined the challenge

EXPIRED - The expiry time for the challenge has passed before all players have accepted

ISSUED - The challenge has been issued but is waiting for other to accept before play can begin

WITHDRAWN - The challenger has withdrawn the challenge

LAPSED - The end time of this challenge has passed before the challenge was started

**example**
    
    
    var runState = Spark.getChallenge(mychallengeid).getRunState();

* * *

### getId

**signature** getId()

**returns** string

Gets the ID of this challenge.

**example**
    
    
    var id = Spark.getChallenge(mychallengeid).getId();

* * *

### getShortCode

**signature** getShortCode()

**returns** string

Returns the shortCode of the challenge

Can be useful when block or code should only run for a particular challenge type.

**example**
    
    
    var shortCode = Spark.getChallenge(mychallengeid).getShortCode();

* * *

### winChallenge

**signature** winChallenge([SparkPlayer](../Spark/SparkPlayer) winner)

**returns** void

Complete the challenge and uses the provided SparkPlayer as the winner.

If the supplied SparkPlayer is not part of the challenge this call will be ignored (silently)

**params**

winner - the SparkPlayer to set as the winner

**example**
    
    
    Spark.getChallenge(mychallengeid).winChallenge(aPlayer);

* * *

### drawChallenge

**signature** drawChallenge()

**returns** void

Complete the challenge with no winner.

**example**
    
    
    Spark.getChallenge(mychallengeid).drawChallenge();

* * *

### startChallenge

**signature** startChallenge()

**returns** void

Starts the challenge in the current state. This method only checks that the state is ISSUED or WAITING and that there is at least 2 players in the challenge 

**example**
    
    
    Spark.getChallenge(mychallengeid).startChallenge();

* * *

### getChallengedPlayerIds

**signature** getChallengedPlayerIds()

**returns** string[]

Returns a list of Players ID's that can be used to load the player details using Spark.getPlayer(String player)

**returns**

The array of player Ids this challenge was issued to

**example**
    
    
    var players = Spark.getChallenge(mychallengeid).getChallengedPlayerIds();

* * *

### getAcceptedPlayerIds

**signature** getAcceptedPlayerIds()

**returns** string[]

Returns a list of Players ID's that can be used to load the player details using Spark.getPlayer(String player)

**returns**

The array of player Ids who have accepted this challenge

**example**
    
    
    var players = Spark.getChallenge(mychallengeid).getAcceptedPlayerIds();

* * *

### getDeclinedPlayerIds

**signature** getDeclinedPlayerIds()

**returns** string[]

Returns a list of Players ID's that can be used to load the player details using Spark.getPlayer(String player)

**returns**

The array of player Ids who have declined this challenge

**example**
    
    
    var players = Spark.getChallenge(mychallengeid).getDeclinedPlayerIds()

* * *

### getChallengerId

**signature** getChallengerId()

**returns** string

Gets the player id of whoever issued the challenge.

**example**
    
    
    var challengerId = Spark.getChallenge(mychallengeid).getChallengerId();

* * *

### consumeTurn

**signature** consumeTurn(string playerId)

**returns** boolean

**params**

Takes a turn for a player in a turn based challenge.

**params**

playerId - the id of the player who has taken their turn

**example**
    
    
    var challenge = Spark.getChallenge(mychallengeid).consumeTurn(playerId);

* * *

### removePlayer

**signature** removePlayer(string playerId)

**returns** boolean

**params**

Removes a player from this challenge.

**params**

playerId - the id of the player to remove

**example**
    
    
    var challenge = Spark.getChallenge(mychallengeid).removePlayer(playerId);

* * *

### getPrivateData

**signature** getPrivateData(string name)

**returns** JSON

Gets the value from a name value pair structure that allows custom data to be attached to this object. This data can either be complex JSON or simple values.

**params**

name - The name in the name value pair

**returns**

a JSON object

**example**
    
    
    var userName = Spark.getPlayer().getPrivateData("name");
    
    
    var userName = Spark.getChallenge().getPrivateData("name");

* * *

### setPrivateData

**signature** setPrivateData(string name, JSON value)

**returns** void

Allows arbitrary data to be added to the object being acted upon.

Sets a value into a name value pair structure that allows custom data to be attached to this object. This data can either be complex JSON or simple values.

The data is not visible to the client

**params**

name - The name in the name value pair

value - The value to set in the name value pair

**example**
    
    
    var userName = Spark.getPlayer().setPrivateData("name", "value");
    
    
    var userName = Spark.getChallenge().setPrivateData("name", "value");

* * *

### removePrivateData

**signature** removePrivateData(string name)

**returns** void

Removes a value from a name value pair structure that allows custom data to be attached to this. This data can either be complex JSON or simple values.

**params**

name - The name in the name value pair

**example**
    
    
    var userName = Spark.getPlayer().removePrivateData("name");
    
    
    var userName = Spark.getChallenge().removePrivateData("name");

* * *

### getScriptData

**signature** getScriptData(string name)

**returns** JSON