title: SparkChallengeType
link: https://docs.gamesparks.net/documentation/cloud-code-api/misc-cloud-code-api/sparkchallengetype
author: GameSparks
description: 
post_id: 6165
created: 2015/03/17 17:48:13
created_gmt: 2015/03/17 17:48:13
comment_status: open
post_name: sparkchallengetype
status: publish
post_type: post

<!--Contains configuration information for the challenges -->

# SparkChallengeType

[toc] 

Contains configuration information for the challenges

The methods in this class respect the segments of the current player when being executed

* * *

### getShortCode

**signature** getShortCode()

**returns** string

**validity** All Scripts

Returns the Short Code of the challenge

* * *

### getName

**signature** getName()

**returns** string

**validity** All Scripts

Returns the Name of the challenge

* * *

### getDescription

**signature** getDescription()

**returns** string

**validity** All Scripts

Returns the Description of the challenge

* * *

### isTurnBased

**signature** isTurnBased()

**returns** boolean

**validity** All Scripts

Returns the true if the challenge is turn based, false otherwise

* * *

### getAttemptConsumers

**signature** getAttemptConsumers()

**returns** string

**validity** All Scripts

Returns the Attempt Consumers of the challenge

* * *

### isGlobal

**signature** isGlobal()

**returns** boolean

**validity** All Scripts

Returns the true if the challenge is global, false otherwise