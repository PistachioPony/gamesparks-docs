title: SparkMessage
link: https://docs.gamesparks.net/documentation/cloud-code-api/utils-cloud-code-api/sparkmessage
author: GameSparks
description: 
post_id: 8071
created: 2015/06/10 14:46:39
created_gmt: 2015/06/10 14:46:39
comment_status: closed
post_name: sparkmessage
status: publish
post_type: post

<!--Provides the ability to send a ScriptMessage and provide the configuration in code rather than from within the portal  -->

# SparkMessage

[toc] 

Provides the ability to send a ScriptMessage and provide the configuration in code rather than from within the portal 

* * *

### setSendViaSocket

**signature** setSendViaSocket(boolean value)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the Send Via Socket option.

* * *

### setSendAsPush

**signature** setSendAsPush(boolean value)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the Send As Push option.

* * *

### setSupressPushOnSocketSend

**signature** setSupressPushOnSocketSend(boolean value)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the Send As Push option.

* * *

### setIncludeInPushCount

**signature** setIncludeInPushCount(boolean value)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the Include In Push Count option.

* * *

### setExpireAfterHours

**signature** setExpireAfterHours(number hours)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the Time To Live (Hours) option.

* * *

### setDeviceTypes

**signature** setDeviceTypes(string[] deviceTypes)

**returns** [SparkMessage](../Utils/SparkMessage)

Limits the message delivery to only the device types supplied.

* * *

### setMessageData

**signature** setMessageData(JSON data)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the data to send.

* * *

### setPlayerIds

**signature** setPlayerIds(string[] playerIds)

**returns** [SparkMessage](../Utils/SparkMessage)

Sets the playerId to send the message to.

* * *

### send

**signature** send()

**returns** void

Sends the message.