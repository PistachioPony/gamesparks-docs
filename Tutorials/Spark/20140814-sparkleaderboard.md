title: SparkLeaderboard
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkleaderboard
author: GameSparks
description: 
post_id: 4579
created: 2014/08/14 10:26:39
created_gmt: 2014/08/14 10:26:39
comment_status: closed
post_name: sparkleaderboard
status: publish
post_type: post

<!--Provides access to the entries of a leaderboard. -->

# SparkLeaderboard

[toc] 

Provides access to the entries of a leaderboard.

e.g.
    
    
    var leaderboard = Spark.getLeaderboards().getLeaderboard(shortCode);

* * *

### getDescription

**signature** getDescription()

**returns** string

Returns the description of this leaderboard.

**example**
    
    
    var desc = Spark.getLeaderboards().getLeaderboard(shortCode).getDescription();

* * *

### getName

**signature** getName()

**returns** string

Returns the name of this leaderboard.

**example**
    
    
    var shortCode = Spark.getLeaderboards().getLeaderboard(shortCode).getName();

* * *

### getShortCode

**signature** getShortCode()

**returns** string

Returns the shortCode of this leaderboard.

**example**
    
    
    var shortCode = Spark.getLeaderboards().getLeaderboard(shortCode).getShortCode();

* * *

### getEntryCount

**signature** getEntryCount()

**returns** number

Returns the total number of entries in this leaderboard.

**example**
    
    
    var count = Spark.getLeaderboards().getLeaderboard(shortCode).getEntryCount();

* * *

### getEntryCountForIdentifier

**signature** getEntryCountForIdentifier(string identifier)

**returns** number

Returns the total number of entries in this leaderboard for the specified identifier.

The later can be the userId of a player or the id of a team.

**example**
    
    
    var count = Spark.getLeaderboards().getLeaderboard(shortCode).getEntryCountForIdentifier("myPlayerId");

* * *

### getEntries

**signature** getEntries()

**returns** [SparkLeaderboardCursor](../Spark/SparkLeaderboardCursor)

Returns a cursor over all the entries in this leaderboard.

**example**
    
    
    var cursor = Spark.getLeaderboards().getLeaderboard(shortCode).getEntries();

* * *

**signature** getEntries(number count, number offset)

**returns** [SparkLeaderboardCursor](../Spark/SparkLeaderboardCursor)

Returns a cursor over **count** entries in this leaderboard, starting at **offset**.

**params**

count - the number of entries over which to obtain a cursor.

offset - the number of entries to skip before the start of the cursor.

**example**
    
    
    var cursor = Spark.getLeaderboards().getLeaderboard(shortCode).getEntries(mycount, myoffset);

* * *

### isPartitioned

**signature** isPartitioned()

**returns** boolean

Returns true if this leaderboard has or can have partitions.

**example**
    
    
    var isPartitioned = Spark.getLeaderboards().getLeaderboard(shortCode).isPartitioned();

* * *

### isPartition

**signature** isPartition()

**returns** boolean

Returns true if this leaderboard is a single partition of a parent leaderboard.

**example**
    
    
    var isPartitioned = Spark.getLeaderboards().getLeaderboard(shortCode).isPartition();

* * *

### getPartitions

**signature** getPartitions()

**returns** [SparkLeaderboardPartition](../Spark/SparkLeaderboardPartition)[]

Returns an array containing the partitions of this leaderboard if it is partitioned, otherwise an empty array is returned.

**example**
    
    
    var partitions = Spark.getLeaderboards().getLeaderboard(shortCode).getPartitions();

* * *

### drop

**signature** drop()

**returns** void

Deletes the underlying data for this leaderboard, making it like new.

**example**
    
    
    Spark.getLeaderboards().getLeaderboard(shortCode).drop();

* * *

**signature** drop(boolean deleteRunningTotalData)

**returns** void

See #drop. Additionally deletes the underlying running total data, resetting any record of players' scores.

**example**
    
    
    leaderboard.drop(true);

* * *

### getEntriesForItentifier

**signature** getEntriesForItentifier(string identifier, JSON customIdFilter)

**returns** SparkLeaderboardEntry[]

Returns the array of leaderboard entries that correspond to the supplied identifier and customIdFilter

If the customIdFilter is null, the method returns all the entries in the leaderboard for the suplied identifier

**example**
    
    
    leaderboard.getEntriesForItentifier(myPlayerId, {});

* * *

### getEntriesFromPlayer

**signature** getEntriesFromPlayer(string playerId, number count)

**returns** [SparkLeaderboardCursor](../Spark/SparkLeaderboardCursor)

Returns a cursor over the leaderboard entries starting from the highest score of the supplied playerId

**example**
    
    
    leaderboard.getEntriesFromPlayer(myPlayerId, 50);

* * *

### getEntriesFromPlayerForCustomId

**signature** getEntriesFromPlayerForCustomId(string playerId, number count, JSON customIdFilter)

**returns** [SparkLeaderboardCursor](../Spark/SparkLeaderboardCursor)

Returns a cursor over the leaderboard entries starting from the highest score of the supplied playerId and customIdFilter

If the customId filter is not an object with valid ID fields, it will return an empty cursor

**example**
    
    
    leaderboard.getEntriesFromPlayerForCustomId(myPlayerId, 50, {carType:"raceCar"});

* * *

### getIdFields

**signature** getIdFields()

**returns** string[]

Returns the list of custom ID fields that are defined on the leaderboard

**example**
    
    
    leaderboard.getIdFields();

* * *

### getScoreFields

**signature** getScoreFields()

**returns** string[]

Returns the list of fields that are defined on the leaderboard

**example**
    
    
    leaderboard.getScoreFields();

* * *

### deleteAllEntries

**signature** deleteAllEntries(string identifier, boolean deleteRunningTotals)

**returns** string[]

Deletes all entries from the leaderboard that correspond to this identifier. If your leaderboard has custom IDs set up, 

it will delete the entries for all the custom IDs

This method only works for realtime leaderboards

If deleteRunningTotals is true, all running total data for these entries will also be deleted

deleting running totals may affect other leaderbaords using the same running totals

**example**
    
    
    leaderboard.deleteEntry(myPlayerId, true);

* * *

### deleteEntriesForCustomId

**signature** deleteEntriesForCustomId(string identifier, boolean deleteRunningTotals, JSON customIdFilter)

**returns** string[]