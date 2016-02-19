title: SparkScheduler
link: https://docs.gamesparks.net/documentation/cloud-code-api/utils-cloud-code-api/sparkscheduler
author: gabriel.page
description: 
post_id: 2401
created: 2014/05/08 11:10:20
created_gmt: 2014/05/08 11:10:20
comment_status: closed
post_name: sparkscheduler
status: publish
post_type: post

<!--Utility to schedule execution of a module in the future -->

# SparkScheduler

[toc] 

Utility to schedule execution of a module in the future

**validity** All Scripts

**example**
    
    
    var theScheduler = Spark.getScheduler();

* * *

### inSeconds

**signature** inSeconds(string shortCode, number delaySeconds, JSON data)

**returns** boolean

Schedules the execution of the supplied module. The scheduled script will run in the context of the current player

**params**

shortCode - The shortCode of the module to execute

delaySeconds - How long to wait until executing the module

data - The data to pass to the module. This will be available as Spark.getData() when the module is running

**example**
    
    
    theScheduler.inSeconds("SHORT_CODE", 15, {"myData" : myData});

* * *

**signature** inSeconds(string shortCode, number delaySeconds, JSON data, string key)

**returns** boolean

Schedules the execution of the supplied module

**params**

shortCode - The shortCode of the module to execute

delaySeconds - How long to wait until executing the module

data - The data to pass to the module. This will be available as Spark.getData() when the module is running

key - The id of the scheduled item. If schedule already exists for the given key it's details will be updated

**example**
    
    
    theScheduler.inSeconds("SHORT_CODE", 15, {"myData" : myData}, "logTimeout-" + Spark.getPlayer().getPlayerId());

* * *

### cancel

**signature** cancel(string key)

**returns** void

Cancels the execution of a previously scheduled module.

**params**

key - The id of the scheduled item to cancel.