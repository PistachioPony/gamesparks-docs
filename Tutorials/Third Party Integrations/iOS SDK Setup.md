---
src: Tutorials/Third Party Integrations/iOS SDK Setup.md
---

# iOS SDK Setup

# GameSparks Objective-C SDK

Welcome the GameSparks SDK for Objective C. This is an non blocking SDK, all the work is done in the background and only the blocks you supply are executed on the main thread.

All API calls are strongly typed, with GSAPI.h/m being auto generated when the server API changes, full details of the API can be found at [http://docs.gamesparks.net](http://docs.gamesparks.net/)

## Installation

  1. Via cocoapodsTo install the SDK, simply add the following line to your Podfile:

```
        pod 'GameSparks', :git => 'https://bitbucket.org/gamesparks/gamesparks-ios-sdk.git' :tag => "0.2.3"
```

  2. Copy the source to your project

## Usage

  1. Import GSAPI.h & GS.h

```
        #import <GS.h>
    #import <GSAPI.h>
```

  2. Create a instance of GS, providing the apiKey and secret from the portal along with whether you want to connect to the live or preview servers. We recommend you keep a static reference to this object.

```
        GS* gs = [[GS alloc] initWithApiKey:@"YOU_KEY" andApiSecret:@"YOUR_SECRET" andPreviewMode:true];
```

  3. Register a listener for availability events

```
        [gs setAvailabilityListener:^ (BOOL available) {
        //Your code here
    }];
```

  4. Register a listener for authentication events

```
        [gs setAuthenticatedListener:^(NSString* playerId) {
        //Your code here
    }];
```

  5. Register listeners for asyncronous messages

```
        GSMessageListener* listener = [[GSMessageListener alloc] init];

    [listener onScriptMessage:^(ScriptMessage* message) {
        //Your code here
    }];

    [gs setMessageListener:listener];
```

  6. Connect the SDK

```
        [gs connect];
```

  7. Start sending requests, and processing responses.

```
        DeviceAuthenticationRequest* dar = [[DeviceAuthenticationRequest alloc] init];
    [dar setDeviceId:@"deviceId"];
    [dar setDeviceOS:@"IOS"];
    [dar setCallback:^ (AuthenticationResponse* response) {
        //Your code here    
    }];
    [gs send:dar];
```
