# GameSparks Debugger

The GameSparks Debugger allows you to test your [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html). If you have a an Event, Request, Response or Message that has custom [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) written to it. By enabling the GameSparks Debugger, you can step through your code to examine what's happening, as it's happening.

The GameSparks Debugger can be both enabled exclusively and in combination for Requests, Responses and Messages. Please note that the Debugger panel will only display if there is some [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) written against the Event, Request, Response or Message.

To enable the GameSparks Debugger, check any or all of the tick boxes that you wish to debug [Cloud Code](https://docs.gamesparks.net/developer-portal/cloud-code) for, under the "Statistics" panel on the [Test Harness](https://docs.gamesparks.net/developer-portal/test-harness):

![](img\GSDebugger\1.png)

For example, checking only the Debug checkbox for Responses, will only activate the GameSparks Debugger when the Response is triggered, providing the Response has come [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) written for it.

Now when you send a request that has some [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) written to it, the GameSparks Debugger will appear as an overlay on the left side of the screen:

![](img\GSDebugger\2.png)

The Context menu (centre) is where all your variables and objects will be shown.  As your variables and objects are defined, you will see their values being populated there. The buttons on the Context menu are:

![](img\GSDebugger\3.png) *Continue* - This will continue execution of the current script until either a breakpoint is hit, or the script finishes.

![](img\GSDebugger\4.png) *Step Over* \- Proceeds to the next line in your current scope (i.e. it goes to the next line), without descending into any method calls on the way. This is generally used for following the logic through a particular method without worrying about the details of its collaborators, and can be useful for finding at what point in a method the expected conditions are violated.

![](img\GSDebugger\5.png) *Step In* - This will cause the debugger to descend into any method calls on the current line. If there are multiple method calls, they'll be visited in order of execution; if there are no method calls, this is same as step over. This is broadly equivalent to following every individual line of execution as would be seen by the interpreter.

![](img\GSDebugger\6.png) *Step Out* - Proceeds until the next "return" or equivalent - i.e. until control has returned to the preceding stack frame. This is generally used when you've seen all you need to at this point/method, and want to bubble up the stack a few layers to where the value is actually used.

![](img\GSDebugger\7.png) *Stop* - Stops the debugging session, the script will be executed and the debug session will stop.

Objects that you create in your [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) will appear as hierarchical trees in the context menu so you can expand and minimise them to view their variables. [SendRequests](https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/spark#sendRequest) are also shown as hierarchical trees in which you can check the responses by expanding them in the Context menu.  Responses to [SendRequests](https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/spark#sendRequest) within [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) viewed within the Debugger, are displayed similar to the way the Test Harness Inspector displays them. Here, the [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) calls an [AuthenticationRequest ](https://docs.gamesparks.net/documentation/request-api/authentication-request-api/authenticationrequest)and an [AuthenticationResponse](https://docs.gamesparks.net/documentation/response-api/authentication-response-api/authenticationresponse). The values attributed to the Request and Response and are shown as child properties of that object:

![](img\GSDebugger\8.png)

### Breakpoints

As in standard developer IDE's, the Breakpoint feature allows you to navigate to and wait at desired steps within the [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html). This is enabled by clicking to the left of the line number of the [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) that you wish to set the breakpoint:

![](img\GSDebugger\9.png)

The line number will be highlighted in orange. These breakpoints are persistent and will be retained, even if you exit and re-enter the [Test Harness](..\Cloud Code, and the Test Harness\Test Harness.html) at a later date. They can be disabled by clicking again to the left of the line number.

If you have multiple Debug checkboxes enabled and your [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) invokes other [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html) items which in turn, also have [Cloud Code](..\Cloud Code, and the Test Harness\Cloud Code.html)attributed to them, then multiple debugging panels may be opened simultaneously in the form of tabbed panels:

![](img\GSDebugger\10.png)

###Time-outs

If the Debugger has been inactive or idle for 2 minutes, the GameSparks Debugger pane will automatically close. This is for multiple reasons (for our benefit and for yours!). From, assuming that the user has finished debugging to, closing any infinite loops they may have found themselves in! The socket connections we keep open internally whilst using the Debugger consume a lot of resources so we allow ample time for these to be closed automatically, freeing up our platforms resources, meaning the system is in it’s best possible shape just for you.

###Break on Error

Another feature available is that of the ‘Break on Error’.There may be instances when your Cloud Code throws an error exception that is not seen within the Test Harness or won’t necessarily halt the rest of the event but invalidates the test.

The ‘Break on Error’ will display any exceptions encountered within the Context menu.

![](img\GSDebugger\11.png)
