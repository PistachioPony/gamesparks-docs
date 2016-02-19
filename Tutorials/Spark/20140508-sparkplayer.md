title: SparkPlayer
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkplayer
author: gabriel.page
description: 
post_id: 2398
created: 2014/05/08 10:56:35
created_gmt: 2014/05/08 10:56:35
comment_status: closed
post_name: sparkplayer
status: publish
post_type: post

<!--Provides access to a player details -->

# SparkPlayer

[toc] 

Provides access to a player details

e.g.
    
    
    var player = Spark.getPlayer();

or
    
    
    var player = Spark.loadPlayer(myplayerid);

* * *

### getDisplayName

**signature** getDisplayName()

**returns** string

Gets the display name of the player.

This may be null for a player who has only used device authentication. Other authentication mechanisms will return a value.

**example**
    
    
    var userName = Spark.getPlayer().getDisplayName();

* * *

### getUserName

**signature** getUserName()

**returns** string

Gets the username name of the player.

For a player who has only used device authentication this value will be generated from the device id.

**example**
    
    
    var userName = Spark.getPlayer().getDisplayName();

* * *

### getPlayerId

**signature** getPlayerId()

**returns** string

Gets the GameSparks ID of the player

**example**
    
    
    var userName = Spark.getPlayer().getPlayerId();

* * *

### credit1

**signature** credit1(number quantity)

**returns** void

Credits the currency1 balance of the player with the amount specified.

**params**

quantity - the amount to credit

**example**
    
    
    Spark.getPlayer().credit1(20);

* * *

### debit1

**signature** debit1(number quantity)

**returns** boolean

Debits the currency1 balance of the player with the amount specified.

**params**

quantity - the amount to debit

**returns**

true if the debit was successful, false if the current balance was not sufficient

**example**
    
    
    Spark.getPlayer().debit1(5);

* * *

**signature** credit2(number quantity)

**returns** void

Credits the currency2 balance of the player with the amount specified.

**params**

quantity - the amount to credit

**example**
    
    
    Spark.getPlayer().credit2(20);

* * *

**signature** debit2(number quantity)

**returns** boolean

Debits the currency2 balance of the player with the amount specified.

Returns true if the debit was successful, false if the current balance was not sufficient.

**params**

quantity - the amount to debit

**example**
    
    
    Spark.getPlayer().debit2(5);

* * *

**signature** credit3(number quantity)

**returns** void

Credits the currency3 balance of the player with the amount specified.

**params**

quantity - the amount to credit

**example**
    
    
    Spark.getPlayer().credit3(20);

* * *

**signature** debit3(number quantity)

**returns** boolean

Debits the currency3 balance of the player with the amount specified.

Returns true if the debit was successful, false if the current balance was not sufficient.

**params**

quantity - the amount to debit

**example**
    
    
    Spark.getPlayer().debit3(5);

* * *

**signature** credit4(number quantity)

**returns** void

Credits the currency4 balance of the player with the amount specified.

**params**

quantity - the amount to credit

**example**
    
    
    Spark.getPlayer().credit4(20);

* * *

**signature** credit5(number quantity)

**returns** void

Credits the currency5 balance of the player with the amount specified.

**params**

quantity - the amount to credit

**example**
    
    
    Spark.getPlayer().credit5(20);

* * *

**signature** credit6(number quantity)

**returns** void

Credits the currency6 balance of the player with the amount specified.

**params**

quantity - the amount to credit

**example**
    
    
    Spark.getPlayer().credit6(20);

* * *

**signature** debit4(number quantity)

**returns** boolean

Debits the currency4 balance of the player with the amount specified.

Returns true if the debit was successful, false if the current balance was not sufficient.

**params**

quantity - the amount to debit

**example**
    
    
    Spark.getPlayer().debit4(5);

* * *

**signature** debit5(number quantity)

**returns** boolean

Debits the currency5 balance of the player with the amount specified.

Returns true if the debit was successful, false if the current balance was not sufficient.

**params**

quantity - the amount to debit

**example**
    
    
    Spark.getPlayer().debit5(5);

* * *

**signature** debit6(number quantity)

**returns** boolean

Debits the currency6 balance of the player with the amount specified.

Returns true if the debit was successful, false if the current balance was not sufficient.

**params**

quantity - the amount to debit

**example**
    
    
    Spark.getPlayer().debit6(5);

* * *

### getBalance1

**signature** getBalance1()

**returns** number

Gets the currency1 balance of the player.

**example**
    
    
    var bal = Spark.getPlayer().getBalance1();

* * *

**signature** getBalance2()

**returns** number

Gets the currency2 balance of the player.

**example**
    
    
    var bal = Spark.getPlayer().getBalance2();

* * *

**signature** getBalance3()

**returns** number

Gets the currency3 balance of the player.

**example**
    
    
    var bal = Spark.getPlayer().getBalance3();

* * *

**signature** getBalance4()

**returns** number

Gets the currency4 balance of the player.

**example**
    
    
    var bal = Spark.getPlayer().getBalance4();

* * *

**signature** getBalance5()

**returns** number

Gets the currency5 balance of the player.

**example**
    
    
    var bal = Spark.getPlayer().getBalance5();

* * *

**signature** getBalance6()

**returns** number

Gets the currency6 balance of the player.

**example**
    
    
    var bal = Spark.getPlayer().getBalance6();

* * *

### addVGood

**signature** addVGood(string shortCode, number quantity)

**returns** boolean