---
nav_sort: 1
---
# GameSparks Realtime

We've recently enhanced our product offering by adding a new set of services for facilitating realtime multiplayer.
GameSparksRT is a low latency socket server designed specifically for realtime games where high throughput and low transmission sizes are required.

 This service is currently in trial with selected customers.  If you would like to take part in the trial please contact info@gamesparks.com and we'll add you to the waiting list.
  The current trial focuses on Unity and the RT SDK operates with near zero memory allocation.  SDKs are in the process of being built for other engines. The process to get up and running is as follows:

## Set up matchmaking rules

[See here](/Tutorials/Multiplayer/HowToMatchPlayers.md) for a document that describes the process for setting up matchmaking rules on the platform.

## Connect to the realtime servers

Using FindMatchRequest

```    
    FindMatchRequest findMatchRequest = new FindMatchRequest().SetMatchShortCode("COMBI_MCH").SetSkill(100).Send((response) => {
        if(!response.HasErrors) {
            //Configure the RealTime session Manager
            GameSparksRTUnity.Instance.Configure(
                response,                                                       //The FindMatchResponse
                (peerId) => { Debug.Log ("OnPlayerConnect=" + peerId); },       //What do do when a player connects
                (peerId) => { Debug.Log ("OnPlayerDisconnect=" + peerId); },    //What do do when a player disconnects
                (ready)  => { Debug.Log ("OnReady=" + ready); },                //What do do when the ready state of the session changes
                (packet) => { Debug.Log ("OnPacket=" + packet); }               //What do do when a packet is recieved
            );
            //Now we are all configured, lets connect to the session.
            GameSparksRTUnity.Instance.Connect();
        }
    });
```

Using MatchFoundMessage

```    
    MatchFoundMessage.Listener = ((matchFoundMessage) => {

        GameSparksRTUnity.Instance.Configure(
            matchFoundMessage, 												//The MatchFoundMessage
            (peerId) => { Debug.Log ("OnPlayerConnect=" + peerId); },		//What do do when a player connects
            (peerId) => { Debug.Log ("OnPlayerDisconnect=" + peerId); },	//What do do when a player disconnects
            (ready)  => { Debug.Log ("OnReady=" + ready); },				//What do do when the ready state of the session changes
            (packet) => { Debug.Log ("OnPacket=" + packet.ToString()); }	//What do do when a packet is recieved
        );

        //Now we are all configured, lets connect to the session.
        GameSparksRTUnity.Instance.Connect();

    });
```
## Send realtime data

Sending data to the other players in the session is performed using the SendData method on GameSparksRTUnity.Instance

```    
    public void SendData (int opCode,
                          GameSparksRT.DeliveryIntent deliveryIntent,
                          RTData structuredData,
                          byte[] unstructuredData,
                          params int[] targetPlayers);

```

Parameter Type Description

|Parameter   |Type   |Description   |
|---|---|--------------------------------|
|opCode   |uint   |Each packet you send to the server has a corresponding opCode. This opCode is available when the packet is received by the other player(s). This must be a non negative integer   |
|deliveryIntent   |GameSparksRT.DeliveryIntent |There are 3 options when sending a packet to the session RELIABLE - The packet will be queued, sent and received by the target players. The packets will be received in the order they are sent. UNRELIABLE - The packet will be sent with no guarantees of it being received. The recievers may get the packets in a different order than they are sent UNRELIABLE_SEQUENCED - The packet will be sent no guarantees of it being received. If it is received out of order it will be discarded|
|structuredData   |RTData (optional) |This is a structured dictionary keyed with integers that can contain doubles, floats, ints, longs, strings or nested RTData objects|
   |unstructuredData|byte[] (optional)|The supplied byte array will be sent with the packet. This is useful if you have your own binary serialization / deserialization|
|targetPlayers   |params int[]   |The peerId's of the players you want to send to. If omitted the packet is broadcast to all others players in the session   |


To reduce GC overhead, RTData objects are pooled and implement IDisposable. When sending an RTData object we recommend wrapping this in a using block to ensure the object is released to the pool once sent for resending. To get an RTData object from the pool you call RTData.Get();

```
    // RTData.Get() returns a pooled instance of an RTData object
    // RTData is a Disposable object, so you shoudl wrap this in a
    // using statement to ensure it's returned to the pool.
    using(RTData data = RTData.Get()){

        //Setup your RTData object
        data.SetDouble(1, 1d)                       //Add a double at key 1
            .SetFloat(2, 2f)                        //Add a float at key 2
            .SetInt(3, 3)                           //Add an int at key 3
            .SetLong(4, 4)                          //Add a long at key 4
            .SetString(5, "This is a string")       //Add a string at key 5
            .SetData(6, RTData.Get().SetInt(1, 1)); //You can also add nested RTData objects

        byte[] unstructured = {0,1};

        GameSparksRTUnity.Instance.SendData(120, GameSparksRT.DeliveryIntent.UNRELIABLE_SEQUENCED, data, unstructured);
    }
```

## Receive realtime data

When you configured the session manager in step 4 you provided a callback that should be called when a packet is received. The Packet struct has the following definition:

```
    public struct RTPacket {
        public int OpCode;          // The opCode set by the sending player
        public int Sender;          // The peerId of the sender
        public RTData Data;         // The RTData object sent
        public Stream Stream;       // A Stream object that represents the unstructuredData sent;
        public int StreamLength;    // The number of bytes in the stream;
    }
```

The RTData object in the packet is from the pool of RTData objects. Once you are finished with this object you should call Dispose() on it to make it available to the pool again. The Stream object in the packet should not be retained as it is returned to the pool as soon as the callback is completed. That's about it, we're looking forward to your feedback!
