# How to store custom data against a Player

Generally, you will want to be able to store custom data against your players, so you can consume the data from either cloud code or from your game client.

There are 2 options available for storing data.  This article will describe the options and explain the pro's and cons of each.

## Attaching Data to the Player object in Cloud Code

Data attached to the Player object is stored in memory on the GameSparks platform, you can use this method of storing global data against a player and you can be sure that subsequent requests for this data will be as fast as possible. The player object is always cached in memory whilst the player has an open socket.

This data set is best used for data that is shared or stored for the lifetime of the player. You have the ability through the [SparkPlayer](/documentation/cloud-code-api/spark-cloud-code-api/sparkplayer) object to set (this can either add or overwrite), get and remove data stored against a key.

The [SparkPlayer](https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkplayer) object has 2 separate data sets that differ in their accessibility.

ScriptData values are stored against the player, and are available via API calls that return details about a player. This leads to the data being accessible to both the players device (via [AccountDetailsRequest](https://docs.gamesparks.net/documentation/request-api/player-request-api/accountdetailsrequest)), and any of the player friends devices (via [ListGameFriendsRequest](https://docs.gamesparks.net/documentation/request-api/player-request-api/listgamefriendsrequest)). You should limit the amount of data you put into ScriptData - although the platform does not limit how much data you can put in, as the data set grows so do the responses that use this data, potentially making the request / response process slower. The script data can be used to store information against a player that you want to show on a device.

PrivateData values are only ever available through cloud code, they will never be transmitted to a device.

## Using MongoDB to store custom data

For more complex scenarios, or where you want responses to only include a subset of the data you have stored, we recommend creating a mongo collection to store this data. You can store all options in a single document, and use the partial update operations (Described [here](/howtos/cloud-data/partial-updates))
