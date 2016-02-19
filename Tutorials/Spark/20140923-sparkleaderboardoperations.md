title: SparkLeaderboardOperations
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkleaderboardoperations
author: GameSparks
description: 
post_id: 4751
created: 2014/09/23 15:26:10
created_gmt: 2014/09/23 15:26:10
comment_status: open
post_name: sparkleaderboardoperations
status: publish
post_type: post

<!--A comparison operation on the owners (players in a player-based leaderboard, teams in a team-based leaderboard) of entries within leaderboards. -->

# SparkLeaderboardOperations

[toc] 

A comparison operation on the owners (players in a player-based leaderboard, teams in a team-based leaderboard) of entries within leaderboards.
    
    
    var operation = Spark.getLeaderboards().union(lb1, lb2);

* * *

### union

**signature** union([SparkLeaderboard](../Spark/SparkLeaderboard) rhs)

**returns** [SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations)

**validity** All Scripts

Performs a union on the set of owners returned as result of evaluating this operation and the owners of entries within the given leaderboard.

Returns a new SparkLeaderboardOperations object to allow further operations to be chained before evaluation.

To obtain the result of the operation call evaluate() on the SparkLeaderboardOperations returned.

**params**

rhs - the the right-hand side of the operation.

**example**
    
    
    var inAny = operation.union(rhs).evaluate();

* * *

**signature** union([SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations) rhs)

**returns** [SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations)

**validity** All Scripts

Performs a union on the set of owners returned as result of evaluating this operation and the set of owners returned as result of evaluating the given operation.

Returns a new SparkLeaderboardOperations object to allow further operations to be chained before evaluation.

To obtain the result of the operation call evaluate() on the SparkLeaderboardOperations returned.

**params**

rhs - the the right-hand side of the operation.

**example**
    
    
    var inAny = operation.union(rhs).evaluate();

* * *

### intersection

**signature** intersection([SparkLeaderboard](../Spark/SparkLeaderboard) rhs)

**returns** [SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations)

**validity** All Scripts

Performs an intersection on the set of owners returned as result of evaluating this operation and the owners of entries within the given leaderboard.

Returns a new SparkLeaderboardOperations object to allow further operations to be chained before evaluation.

To obtain the result of the operation call evaluate() on the SparkLeaderboardOperations returned.

**params**

rhs - the the right-hand side of the operation.

**example**
    
    
    var inBoth = operation.intersection(rhs).evaluate();

* * *

**signature** intersection([SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations) rhs)

**returns** [SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations)

**validity** All Scripts

Performs an intersection on the set of owners returned as result of evaluating this operation and the set of owners returned as result of evaluating the given operation.

Returns a new SparkLeaderboardOperations object to allow further operations to be chained before evaluation.

To obtain the result of the operation call evaluate() on the SparkLeaderboardOperations returned.

**params**

rhs - the the right-hand side of the operation.

**example**
    
    
    var inBoth = operation.intersection(rhs).evaluate();

* * *

### difference

**signature** difference([SparkLeaderboard](../Spark/SparkLeaderboard) rhs)

**returns** [SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations)

**validity** All Scripts

Performs a difference on the set of owners returned as result of evaluating this operation and the owners of entries within the given leaderboard.

Returns a new SparkLeaderboardOperations object to allow further operations to be chained before evaluation.

To obtain the result of the operation call evaluate() on the SparkLeaderboardOperations returned.

**params**

rhs - the the right-hand side of the operation.

**example**
    
    
    var onlyInFirst = operation.difference(rhs).evaluate();

* * *

**signature** difference([SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations) rhs)

**returns** [SparkLeaderboardOperations](../Spark/SparkLeaderboardOperations)

**validity** All Scripts

Performs a difference on the set of owners returned as result of evaluating this operation and the set of owners returned as result of evaluating the given operation.

Returns a new SparkLeaderboardOperations object to allow further operations to be chained before evaluation.

To obtain the result of the operation call evaluate() on the SparkLeaderboardOperations returned.

**params**

rhs - the the right-hand side of the operation.

**example**
    
    
    var onlyInFirst = operation.difference(rhs).evaluate();

* * *

### evaluate

**signature** evaluate()

**returns** string[]

**validity** All Scripts

Returns an array of ids representing the result set of evaluating this operation.

**example**
    
    
    var results = operation.evaluate();