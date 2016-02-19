title: SparkProperties
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkproperties
author: GameSparks
description: 
post_id: 8385
created: 2015/08/10 08:51:33
created_gmt: 2015/08/10 08:51:33
comment_status: closed
post_name: sparkproperties
status: publish
post_type: post

<!--Provides access to the properties for the current game. -->

# SparkProperties

[toc] 

Provides access to the properties for the current game.
    
    
    var properties = Spark.getProperties();

* * *

### getProperty

**signature** getProperty(string propertyShortCode)

**returns** JSON

Returns the property with the given shortCode, as JSON

**example**
    
    
    var property = Spark.getProperties().getProperty(propertyShortCode);

* * *

### getPropertySet

**signature** getPropertySet(string propertySetShortCode)

**returns** JSON

Returns the property set with the given shortCode, as JSON

**example**
    
    
    var propertySet = Spark.getProperties().getPropertySet(propertySetShortCode);