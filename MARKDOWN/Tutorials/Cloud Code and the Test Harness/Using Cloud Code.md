---
nav_sort: 1
src: /Tutorials/Cloud Code and the Test Harness/Using Cloud Code.md
---

# How to create and use Cloud Code

In this tutorial, you can follow an example and learn how to create and work with Cloud Code:
* We use the Configurator to create an Event that will then trigger a simple piece of Cloud Code.
* The Event will contain three attributes - a String, a Number and a JSON field.
* The Cloud Code (a piece of JavaScript) will manipulate these values and echo them back in the Event response.
* We'll then use the Test Harness to try out the Cloud Code script and the Event.

## Create an Event

*1.* Go to *Configurator > Events* and click the ![](/img/fa/plus.png) icon:

![](img/CreateCloud/1.png)

The *Create Event* dialog appears:

*2.* Now fill in the Event’s details and click the *Save* button:

![](img/CreateCloud/12.png)

The *Create Event* dialog closes and the Event is listed on the Events page.

*3.* Click *Edit* ![](/img/fa/edit.png) icon. The *Edit Event* dialog appears:

*4.* Next, click the ![](/img/fa/plus.png) icon to add an Event Attribute.

![](img/CreateCloud/13.png)

*5.* Now fill in the Event Attribute details:
* The Name field is self explanatory.
* The Short Code will be used as the key for the value that you post into the GameSparks platform from your game code.
* Set the Data Type to "String".
* For Default Calc choose the option ‘Used in Script".

![](img/CreateCloud/14.png)

*6.* Click the Save.

*7.* Repeat this step to create another two attributes for this event, one with "Number" for its Data Type, the other with "JSON" for its Data Type.

![](img/CreateCloud/15.png)

*8.* Click Save. Your *Events* page should now look something like this.

![](img/CreateCloud/16.png)

## Create a Cloud Code Script

In this section we will create a Cloud Code script linked to the Event that we have just created. Go to Configurator/Cloud Code, find Events in the Bindings section, and select Cloud Code Event. This is the Event we have just created and we will now bind cloud code to it.

![](img/CreateCloud/7.png)

Copy and paste the following JavaScript code into the editor section.

  ```  
    var eventAttr1 = Spark.getData().CC_ATTR
    var eventAttr2 = Spark.getData().CC_ATTR_2
    var eventAttr3 = Spark.getData().CC_ATTR_3
    Spark.setScriptData("eventAttr1", eventAttr1.toUpperCase());
    Spark.setScriptData("eventAttr2", eventAttr2 * 10);
    eventAttr3.won = true
    Spark.setScriptData("eventAttr3", eventAttr3);
```

Click Save at the bottom right hand corner. Your page should now look like this.

![](img/CreateCloud/8.png)

The first three lines of the script use the *Spark.getData* function to access the attribute values of the incoming Event. Notice how these attributes match the values we gave the Event Attribute short codes in the previous section. The remaining lines use the *Spark.setScriptData* function to add three new fields to the response that is delivered to the calling client. The first line takes the first attribute and converts it to uppercase, the second multiplies the second attribute value by 10 and the final two lines add a new property to an incoming JSON object and assign that to the response. You're now ready to test the code via the Test Harness.

## Testing the Cloud

Code script and Event with the Test Harness

In this section we will use the Test Harness to register a test player with the preview version of the game, authorise this player and post an event that will trigger our Cloud Code script. We will see the JSON requests and responses containing the data inserted by the script.

### Register test players

Go to Test Harness/Authentication and select RegistrationRequest. Then change the userName and displayName as shown below.

![](img/CreateCloud/9.png)

To send this JSON request to the GameSparks platform press the Play icon.

![](img/CreateCloud/10.png)

The Inspector shows the request (in green text) that was sent sent to the GameSparks platofrm via the WebSocket and the response (in blue text).

![](img/CreateCloud/11.png)

## Log Event

Go to Test Harness/LogEvent section, and select the CC_EVT event that we created above. Set each of attribute values in the JSON request as below. Note that the key names are the short codes of the Event Attributes that we created at the start of the exercise. The first attribute must be a String, the second a Number and the third attribute must be a JSON object. Click the Play icon to send the request to the GameSparks platform.

![](img/CreateCloud/12.jpg)

The response is displayed in the Inspector in blue text. The scriptData property contains the fields that we added from within our Cloud Code script. The keys are eventAttr1, eventAttr2 and eventAttr3.
