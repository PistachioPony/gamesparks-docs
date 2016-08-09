---
nav_sort: 5
src: /Tutorials/Social Authentication and Player Profile/Using Bulk Operations for Global Messages.md
---

# Using Bulk Operations to Send Global Messages to your Players

The GameSparks platform allows you to perform bulk operations. We’ll use bulk operations to send every player on our platform a message.

There are two ways to do this, first through the request itself and the second through Cloud code.

## Through the request from Test Harness:


```

{
 "@class": ".ScheduleBulkJobAdminRequest",
 "playerQuery": {},
 "scheduledTime": "2016-03-29T10:16Z",
 "script": "Spark.sendMessageById({\"Message\": \"Good day!\"}, [Spark.getPlayer().getPlayerId()]);"
}

```

The three simple fields that need setting are:

    playerQuery – Takes a query that acts on the player collection. This can be anything relevant to the player document found in the player collection.
    scheduledTime – The time when this bulk job should take place.
    script – The Cloud code that will execute on every player.

By entering no query we include all players to this bulk job.

Due to the request taking the script in as a string, Cloud code with quotes will cause problems in the compiler and hence it will not run. For this example we use an escape character ‘\’ before a quotation to allow us to carry on.

Optionally you can execute a module by referring to its shortCode, like so:


```

{
 "@class": ".ScheduleBulkJobAdminRequest",
 "moduleShortCode": "messageModule",
 "playerQuery": {},
 "scheduledTime": "2016-03-29T10:32Z"
}

```

Once the request is executed, every player we have is sent a message.

## Through Cloud code

You can send a bulk job request in Cloud code in two ways:

Building it via request builder

```

var bulkJobRequest = new SparkRequests.ScheduleBulkJobAdminRequest();

//If using module
bulkJobRequest.moduleShortCode = "messageModule";

//If using script
bulkJobRequest.script = "Spark.sendMessageById({\"Message\": \"Good day!\"}, [Spark.getPlayer().getPlayerId()]);";

bulkJobRequest.scheduledTime = "2016-03-29T10:32Z";

bulkJobRequest.playerQuery = {};

bulkJobRequest.Send();


```

Sending it via Spark.sendRequest

```

Spark.sendRequest({"@class": ".ScheduleBulkJobAdminRequest",
 "playerQuery": {},
 "scheduledTime": "2016-03-29T10:16Z",
 "script": "Spark.sendMessageById({\"Message\": \"Good day!\"}, [Spark.getPlayer().getPlayerId()]);"});


```
