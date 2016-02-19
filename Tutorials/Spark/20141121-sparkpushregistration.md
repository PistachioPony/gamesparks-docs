title: SparkPushRegistration
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkpushregistration
author: GameSparks
description: 
post_id: 5600
created: 2014/11/21 15:29:47
created_gmt: 2014/11/21 15:29:47
comment_status: closed
post_name: sparkpushregistration
status: publish
post_type: post

<!--The registration of a device to receive push notifications. -->

# SparkPushRegistration

[toc] 

The registration of a device to receive push notifications.

e.g.
    
    
    var player = Spark.getPlayer().getPushRegistrations();

* * *

### getId

**signature** getId()

**returns** string

Gets the id of this registration. This is the registrationId returned from the PushRegistrationResponse.

**example**
    
    
    pushRegistration.getId();

* * *

### getPushId

**signature** getPushId()

**returns** string

Returns the id that uniquely identifies the device to the 3rd party push service.

**example**
    
    
    pushRegistration.getPushId();

* * *

### getDeviceOS

**signature** getDeviceOS()

**returns** string

Returns the OS type for the device to which this registration belongs.

**example**
    
    
    pushRegistration.getDeviceOS();