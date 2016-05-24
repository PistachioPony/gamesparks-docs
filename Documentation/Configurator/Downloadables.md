---
nav_sort: 13
---
# Downloadables

This section of the Configurator allows you to upload and manage binary data (e.g. content, such as new levels).  You just need to upload the file and assign it a short code.  Once an object has been added you can then access it from within Cloud Code and do whatever you want with it (e.g. distribute it to certain players under certain conditions).

**Note*: The platform also supports the upload of binary content directly from your game using the API which allows player-created content (e.g. photos,custom levels) to be uploaded and stored.**

![](img/Downloadables/1.jpg)

* __ Amend the Downloadable.
* __ Delete the Downloadable.
* __ Download the Downloadable


To create a new piece of Downloadable content click on the __ icon as highlighted above. Next fill in a meaningful short code and then select the downloadable file.

![](img/Downloadables/1.jpg)

*API Request*

The GetDownloadableRequest returns a secure, time sensitive URL to allow the game to download a piece of downloadable content stored in the GameSparks platform. An example can be found [here](/?p=2240).

*Accessing the Downloadable from Cloud Code*

Both [XML](https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/spark#downloadableXml) and [JSON](https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/spark#downloadableJson) Downloadables can be accessed via Cloud Code.
