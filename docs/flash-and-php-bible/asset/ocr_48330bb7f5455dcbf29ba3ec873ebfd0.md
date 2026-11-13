```
function connectHandler(event:Event):void
{
    trace("Connected to [" + host + "]");
}
```

The connectHandler function is the place any calls to the server should be made. It would be a good place to add the sample message call, such as:

```
function connectHandler(event:Event):void
{
    trace("Connected to [" + host + "]");
    try
    {
        socket.writeUTFBytes("are you hungry?\\n");
    }
    catch(e:IOError)
    {
        trace(e);
    }
}
```

The second special event handler is called when a response is fully gathered from the socket server. This is used to ensure partial messages are not evaluated, as they could potentially cause programming errors that would be hard to track.

```
function socketDataHandler(event:ProgressEvent):void
{
    trace("Socket Server Response Loaded");
}
```

This is the function in which all response code should be placed, similar to the following:

```
function socketDataHandler(event:ProgressEvent):void
{
    var str:String = socket.readUTFBytes(socket.bytesAvailable);
    trace("Socket Server Response: " + str);
}
```

As you can see, working with sockets in Flash is not that different from any other data object. The consistency of the code across different packages is one very great aspect of ActionScript.

# Remote socket connections

The previous example was connecting to a local socket (on the same machine), but it is more realistic that your application would be connecting to a remote socket. This means you must set up a trust between the client and server running the socket server application.