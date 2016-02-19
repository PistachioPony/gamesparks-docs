# Unity3D SDK

[wpdm_file id=21 title="true" ]

  * Fixed potential deadlock on WP8 devices.
  * Durable queue updates to enforce processing in order.
  * xcodeproj post processing updates for new project version
  * API Updates to include all Server requests

##### V5.2

  * IL2CPP updates.
  * xcodeproj post processing modified to support append and replace.
  * API Updates to include all Server requests

##### V5.1

  * Per player durable queue, this means a request sent with durable as a player will only ever go as that player.
  * Unity 5.1.0 Support (There is currently a defect in Unity preventing WP8 builds)
  * API Updates to include all Server requests
  * Ability to have multiple GSInstance objects to aid testing

##### V5.0

  * Full Unity 5 support
  * WebGL
  * IL2CPP
  * Version number visibility within Unity.
**Using the SDK** The following steps will show in detail how to integrate the GameSparks Unity 3D SDK into a new Unity Project. **Create a new Unity project** ![New Unity Project](/wp-content/uploads/2014/09/1.create-new-project.png) **Download the new SDK** The GameSparks Unity3D SDK is provided as a standard unity package and can be downloaded here. **Import the SDK** ![2.Import Package](https://docs.gamesparks.net/wp-content/uploads/2014/09/2.Import-Package.png) Select the package you just downloaded, you will then be presented with the following screen, make sure that all items are ticked and click Import. ![3.import part 2](https://docs.gamesparks.net/wp-content/uploads/2014/09/3.import-part-2.png) You project folder should now contain Assets/GameSparks and Assets/Plugins. ![4.imported](https://docs.gamesparks.net/wp-content/uploads/2014/09/4.imported.png) **Configure the SDK** To configure the SDK for use with your game, select “GameSparks -> Edit Settings” from the menu bar. (If the GameSparks menu item is not visible click another one and it will appear, this is a nuance of menu items in unity) ![5.edit settings](https://docs.gamesparks.net/wp-content/uploads/2014/09/5.edit-settings.png) You will then be presented with an Editor pane that allows you to configure the SDK for you needs. ![6. inspector](https://docs.gamesparks.net/wp-content/uploads/2014/09/6.-inspector.png) Fill the pane with the following settings: Api Key – The “GameSparks Api Key” value from the Overview Menu in the portal Configurator Api Secret – The “GameSparks Api Secret” value from the Overview Menu in the portal Configurator ![7. GameSparksAPI](https://docs.gamesparks.net/wp-content/uploads/2014/09/7.-GameSparksAPI.png) Development Build - Select this option when you want to run the SDK against the unpublished configuration Debug Build - Select this option to get extended debugging out of the SDK (useful for support purposes) **Testing Your Configuration** Click the “Test Configuration” button in the GameSparks settings editor. This will open the test harness (you will be prompted to save your current scene). You should see JSON messages being sent and received by Unity from the service. ![7.Test Harness](https://docs.gamesparks.net/wp-content/uploads/2014/09/7.Test-Harness.png) **Authenticating against the service** On the first run, you will see the label “NOT AUTHENTICATED”, to send requests to the platform, you need to be authenticated. There are a number of requests that can authenticate you, these are: AuthenticationRequest – User to authenticate using details previously provided in a RegistrationRequest DeviceAuthenticationRequest – Uses the unique identifier for the device to create an anonymous user, the unity SDK deals with all the parameters required for this FacebookConnectRequest – Uses a facebook authentication token to register and or authenticate with the platform, this requires you to have set up an app on <https://developers.facebook.com/> RegistrationRequest – Allows a new user to be created with a username & password. The test UI contains a button to do a device authentication. Click this button and the current player will be authenticated. ![8.Auth](https://docs.gamesparks.net/wp-content/uploads/2014/09/8.Auth_.png) **Adding the SDK to your own game** To add to your own game, you need to add the GameSparksUnity class to one of your own components, a good way to do this is to create an Empty GameObject, name it GameSparks and drag the GameSparksUnity.cs script onto the GameObject. It's best to do this on the very first scene your game loads so you can begin analytics or start logging your user in as soon as possible. You only need to add it to one scene, GameSparksUnity.cs uses DontDestroyOnLoad() which ensures that the script will live throughout your game's scene changes. **Sending requests** You’ll need the following using directives:


    using GameSparks.Api.Requests; 
    using GameSparks.Api.Responses;

Each request type in the platform now has it’s own class, to send an authentication request you can use the following


    AuthenticationResponse authResponse = new AuthenticationRequest ().SetUserName ("gabriel").SetPassword ("password").Send ();  

    if (authResponse.HasErrors) { 
        //It didn't work 
    } else { 
        //It worked!!
    }

There are 3 variants of the Send method, where “OUT” is the specific response type the request will return public OUT Send ()  - Blocking send method, the thread will wait for a response   public void Send (Action<OUT> callback)  - Async send method, the provided action will be invoked when the response is received, the action should check for errors in the response using response.HasErrors   public void Send (Action<OUT> callback, int timeoutSeconds)  - As above, with user provided timeout value   public void Send (Action<OUT> successCallback, Action<OUT> errorCallback)  - Async send method, the SDK will invoke the correct action based on the HasErrors property of the reponse.   public void Send (Action<OUT> successCallback, Action<OUT> errorCallback, int timeoutSeconds)  - As above, with user provided timeout value All async methods are null safe, you can pass a null action in if you do not want to do anything on response : new DeviceAuthenticationRequest ().Send (null);  All responses from the SDK are also strongly type, so you can use your IDE’s auto complete to the the available properties. **Sending JSON**
