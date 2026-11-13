# Set up the callback

The final step in setting up a data loader is the callback. The callback is another name for the “handler” function that is called when the data is completely loaded. This function is assigned to the Event.COMPLETE event on the URLLoader class.

```
var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, loadHandler);
```

This callback function requires one argument of the type Event, which is automatically passed in when the ActionScript is called. This argument is where the contents of the loaded data will be stored.

If you forget to include the argument in the event Handler you will get an argument count mismatch error.

```
ArgumentError: Error #1063: Argument count mismatch on
sendtophp_fla::MainTimeline/serverResponse(). Expected 0,
got 1.
at flash.events::EventDispatcher/dispatchEventFunction()
at flash.events::EventDispatcher/dispatchEvent()
at flash.net::URLLoader/onComplete()
```

# Putting it all together

Now that you have an understanding of how the code to load data using ActionScript works you can move on to more specific examples of sending and loading. In this example, you can experiment and build from the URLLoader class because it has a lot more Events than just the simple COMPLETE you used. For example, there is an IOError event that is called when the load or send fails. The code for various Events is pretty much the same; for your IOError example it would look like this:

```
var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, ioHandler);
function ioHandler(e:Event):void
{
trace("File loading was terminated");
}
```

You will quickly notice the only thing that changed is the Event string and the handler function. Multiple events can also be assigned, and it is often a good idea to maintain a high level of compatibility. You also are able to quickly debug code if you set up the proper events.

# Assigning multiple events

Assume that you want to handle the IOError and Complete event for the loader instance. You could enter each event handler; however, this may become a long process when working with multiple loaders. One way to achieve the intended result is to use a function to assign the handlers. You basically pass in the target as an argument and dynamically assign your event handlers.

```
var txtFile:String = "sample.txt";
var urlRequest:URLRequest = new URLRequest(txtFile);
```