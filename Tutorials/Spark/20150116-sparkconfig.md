title: SparkConfig
link: https://docs.gamesparks.net/documentation/cloud-code-api/misc-cloud-code-api/sparkconfig
author: GameSparks
description: 
post_id: 5707
created: 2015/01/16 11:16:38
created_gmt: 2015/01/16 11:16:38
comment_status: open
post_name: sparkconfig
status: publish
post_type: post

<!--Contains configuration information for the game -->

# SparkConfig

[toc] 

Contains configuration information for the game

* * *

### getStage

**signature** getStage()

**returns** string

**validity** All Scripts

Returns the stage (preview or live) the game is running on

* * *

### getApiKey

**signature** getApiKey()

**returns** string

**validity** All Scripts

Returns the apiKey of the game

* * *

### getVirtualGoods

**signature** getVirtualGoods()

**returns** JSON

**validity** All Scripts

Returns a list of the Virtual Goods configured against the game

* * *

### getVirtualGood

**signature** getVirtualGood(string shortCode)

**returns** [SparkVirtualGood](../Misc/SparkVirtualGood)

**validity** All Scripts

Returns the virtual good with the supplied short code

* * *

### getAchievements

**signature** getAchievements()

**returns** JSON

**validity** All Scripts

Returns a list of the Achievements configured against the game

* * *

### getAchievement

**signature** getAchievement(string shortCode)

**returns** [SparkAchievement](../Misc/SparkAchievement)

**validity** All Scripts

Returns the achievement with the supplied short code

* * *

### getSegments

**signature** getSegments()

**returns** JSON

**validity** All Scripts

Returns a list of the Segments configured against the game

* * *

### getSegment

**signature** getSegment(string shortCode)

**returns** [SparkSegmentType](../Misc/SparkSegmentType)

**validity** All Scripts

Returns the segment with the supplied short code

* * *

### getTeams

**signature** getTeams()

**returns** JSON

**validity** All Scripts

Returns a list of the Teams configured against the game

* * *

### getTeam

**signature** getTeam(string shortCode)

**returns** [SparkTeamType](../Misc/SparkTeamType)

**validity** All Scripts

Returns the team with the supplied short code

* * *

### getChallenges

**signature** getChallenges()

**returns** JSON

**validity** All Scripts

Returns a list of the Challenges configured against the game

* * *

### getChallenge

**signature** getChallenge(string shortCode)

**returns** [SparkChallengeType](../Misc/SparkChallengeType)

**validity** All Scripts

Returns the challenge with the supplied short code

* * *

### getDownloadable

**signature** getDownloadable(string shortCode)

**returns** [SparkDownloadable](../Misc/SparkDownloadable)

**validity** All Scripts

Returns the downloadable with the supplied short code

* * *

### getDownloadables

**signature** getDownloadables()

**returns** [SparkDownloadable](../Misc/SparkDownloadable)[]

**validity** All Scripts

Returns a list of all the downloadables configured for this game