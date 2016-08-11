---
nav_sort: 5
src: /Tutorials/Third Party Integrations/Android Extra Functionality.md
---

# Android Requests and Responses Extra Functionality

GameSparks conveniently offers you the ability to augment existing calls and responses with extra functionality. In the portal, if you navigate to *Configurator > Cloud Code*, you will see tabs for Requests, Responses, User Messages, and Global Messages. Once expanded, these tabs will allow you to add Cloud Code to any request, response, or message and achieve the extra functionality you want in your game.

In this tutorial, we'll follow an example of how to do this by adding Cloud Code to the Registration request and response so that:
* The *RegistrationRequest* will be blocked if the email is not passed in.
* The *RegistrationResponse* will get the registered player's email and save it against that player's scriptData.

Lastly, we'll see how to add scriptData to requests from the SDK for Android clients.

### Registration Request

First, we'll navigate to *Configurator > Cloud Code > Requests* and open the Registration Request Cloud Code. In there we'll add:

```
if(!Spark.getData().scriptData){
    Spark.setScriptError("Error", "Need an Email")
} else{
    Spark.setScriptData("email",Spark.getData().scriptData.email );
}

```

This will ensure that if the value 'email' isn't passed in through the scriptData object, then the registration will not continue.


#### Registration Response

Second, we'll navigate to *Configurator > Cloud Code > Responses* and add this to the Cloud code:

```
if(Spark.getData().scriptData){
    var email = Spark.getData().scriptData.email;
    Spark.getPlayer().setScriptData("email", email);
}

```

After the response is received, the player will be authenticated, so calling *Spark.getPlayer()* will return the just registered player. After getting the player, we save the email value against their scriptData.

#### SDK Request

Finally, here's how we add scriptData to your requests from the SDK, similar to the way we use Attributes for Events:

```

Map scriptData = new HashMap();
        scriptData.put("email",string);

        GSAndroidPlatform.gs().getRequestBuilder().createRegistrationRequest()
                .setUserName(string)
                .setDisplayName(string)
                .setPassword(string)
                .setScriptData(scriptData)
                .send(new GSEventConsumer() {
                    @Override
                    public void onEvent(GSResponseBuilder.RegistrationResponse registrationResponse) {

                    }
                });

```
