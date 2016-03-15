# Creating a search function to find user-generated levels

## Introduction

This tutorial will demonstrate two ways in which you can create a system used to search uploaded data, for example user-generated levels.  

## Using a collection

### MetaData/Runtime collection

For our example we are going to create a runtime collection and insert a few records for testing.
![](/wp-content/uploads/2016/01/bandicam-2016-01-28-12-53-00-534-300x157.jpg)![](https://docs.gamesparks.net/wp-content/uploads/2016/01/bandicam-2016-01-28-12-57-14-164-300x157.jpg)
 

### Test Downloadble

We will also create an equal number of downloadables for testing. The Shortcode for these downloadables will be correspondent to the Shortcode in the database record.
![](/wp-content/uploads/2016/01/bandicam-2016-01-28-15-48-22-636-300x157.jpg)

### Search event

We made an event which takes 4 different strings to search for levels. Those strings are the name of the map, author of the map, rating of the map and the difficult which can be used separately or in conjunction with each other to find results relevant to the search.
![](/wp-content/uploads/2016/01/bandicam-2016-01-28-12-51-29-395-300x157.jpg)


    //Create a JSON to save search criteria
    search = {};

    //If any search criteria is passed in then we will construct the JSON to include it
    if(Spark.getData().NAME){
        search.Name = Spark.getData().NAME;
    }
    if(Spark.getData().AUTHOR){
        search.Author = Spark.getData().AUTHOR;
    }
    if(Spark.getData().RATING){
        search.Rating = Spark.getData().RATING;
    }
    if(Spark.getData().DIFF){
        search.Difficulty = Spark.getData().DIFF;
    }

    //Creating a reference to the collection
    var levelCollection = Spark.runtimeCollection("levelCollection");

    //Creating a temp Cursor which contains the records
    var tempCursor = levelCollection.find(search, {_id : 0});

    //Create an Array to save the results from the cursor
    var searchResults = []

    //While loop will keep iterating the cursor until length and insert objects into our array
    while (tempCursor.hasNext()){
        searchResults.push(tempCursor.next());
    }

    //Output the search for our players to be used in the frontend
    Spark.setScriptData("searchResult", searchResults);

### Using search results

The results will be passed to the frontend as an array of objects. The array can be iterated through and data can be extracted from it and listed to the player. A GetUploaded request will have to be made once the player chooses the level they wish to download. The request will take a Shortcode that refers to the downloadble, this Shortcode will be found in the array of objects that we passed in, for our example it would be the value of "DLShortcode". For more information about the GetUploaded request, click [here](https://api.gamesparks.net/?csharpsdk#getuploadedrequest).
 

## Using a partitioned leaderboard

  Partitioning a leaderboard is a powerful feature that augments a leaderboard with more functionality and allows it to be used for purposes other than just to print entries. This tutorial will show you how to setup a partitioned leaderboard for the purpose of looking up a user generated level.    

### Event

The attributes for our event will be:

  * Name - Level name which can be used for reference.
  * Rating - Which can be used to rank the entries.
  * Difficulty - The difficulty set the level belongs under, this will be used for the partition.
  * ShortCode - will be used to get the downloadable.
 
![](/wp-content/uploads/2016/02/bandicam-2016-02-02-10-53-48-461-300x159.jpg)
 

### Leaderboard

The running totals for our leaderboard will be:

  * Rating - Which we'll use to rank our entries set .
  * Difficulty - Used as an example of a partition. We'll need to choose 'Partition' as the group.
  * Name - Name of the level used for reference.
  * ShortCode - easily accessible by users when searching for entries.
![](/wp-content/uploads/2016/02/bandicam-2016-02-02-10-55-18-795-300x159.jpg)
 

### Managing and reviewing the leaderboard per partition

In the manage section you can review your leaderboard. You can limit this review to per partition, so you only retrieve entries from the partition value that you wish to see. This is also the way your players retrieve these entries based on partition through the leaderboard requests. More about paritions, [here](/howtos/leaderboards-howtos/how-to-partition-leaderboards).
![](/wp-content/uploads/2016/02/bandicam-2016-02-02-10-56-11-349-300x159.jpg)
 

### Searching for level

Because these entries are leaderboard entries players can use the native GameSparks leaderboard requests to retrieve them. Players can specifically return levels associated with them, ones that are similar to them or all entries with or without format. You can choose what entries come back to your user based on their search criteria through cloud code or the frontend. Once players find the level they wish to download, they can do so through the ShortCode that links to downloadable.
