

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

## Remote socket connections

The previous example was connecting to a local socket (on the same machine), but it is more realistic that your application would be connecting to a remote socket. This means you must set up a trust between the client and server running the socket server application.

## Security trust

A trust uses the crossdomain.xml file with the ports that are allowed, such as:

```
<?xml version="1.0"?>
<!DOCTYPE cross-domain-policy SYSTEM
"http://www.macromedia.com/xml/dtds/cross-domain-policy.dtd">
<cross-domain-policy>
<allow-access-from domain="*" to-ports="8888" />
</cross-domain-policy>
```

This access file is allowing any client to connect on port 8888 and no other. You can also define a domain if this socket application will be accessible only from another Web site, such as.

```
<?xml version="1.0"?>
<!DOCTYPE cross-domain-policy SYSTEM
"http://www.macromedia.com/xml/dtds/cross-domain-policy.dtd">
<cross-domain-policy>
<allow-access-from domain="anothersite.com" to-ports="8888" />
</cross-domain-policy>
```

The second part of the security trust is a call to allowDomain in the Flash file. This method of the Security class is responsible for defining a domain that is allowed to connect to this client. This connection will only occur if the remote site has a proper crossdomain file.

```
Security.allowDomain("example.com");
```

## Loading the policy file

In rare cases, the cross-domain policy file is not in the default location, so a call to loadPolicyFile can be made to inform Flash where to find the crossdomain.xml file.

```
Security.loadPolicyFile("http://example.com/newloc/crossdomain.xml");
```

You should now know how to set up a client-based socket connection in Flash. As you can see, the majority of the code used in a socket connection is handled by Flash.

As stated in the beginning of this section, the code used to build a socket connection can be reused throughout your projects.

## Using a class for socket connections

To better understand socket connections in Flash, let's start off by building a basic socket example. Then once the basics are in place, the next section will cover building a complete socket-based chat application using Flash and PHP.

### Basic socket class

Here is a basic socket class that easily defines the customizable elements. Simply save this code in an ActionScript file with the name SimpleSocket in the same directory as your sample Flash document.

```
package
{

import flash.errors.*;
import flash.events.*;
import flash.net.Socket;

public class SimpleSocket extends Socket
{

public var host:String;
public var port:uint;
private var socket:Socket;

public static var SOCK_CONNECTED:String = "onSockConnect";
public static var SOCK_IOERROR:String = "onSockIOError";

function SimpleSocket(h:String, p:uint)
{
host = h;
port = p;
socket = this;
super(host, port);
initListeners();
}

public function sendMessage(str:String):void
{
if(connected)
{
socket.writeUTFBytes(str + "\\n");
}
else
{
trace("Not connected, message not sent!");
}
}

public function readMessage():void
{
if(connected)
{
var str:String = socket.readUTFBytes(socket.bytesAvailable);
trace("Socket Server Response: " + str);
}
else
{
    trace("No message read, not connected!");
}
}

private function initListeners():void
{
    socket.addEventListener(Event.CLOSE, closeHandler);
    socket.addEventListener(Event.CONNECT, connectHandler);
    socket.addEventListener(IOErrorEvent.IO_ERROR, ioErrorHandler);
}

private function closeHandler(event:Event):void
{
    trace("Connection to [" + host + "] closed");
}

private function ioErrorHandler(event:IOErrorEvent):void
{
    dispatchEvent(new Event(SOCK_IOERROR));
}

private function connectHandler(event:Event):void
{
    trace("Connected to [" + host + "]");
    dispatchEvent(new Event(SOCK_CONNECTED));
}

private function socketDataHandler(event:ProgressEvent):void
{
    readMessage();
}
} // last two braces are lined up for printing purposes
```

### Using the SimpleSocket class

The process of using the SimpleSocket class is fairly simple. Start by setting up a new Flash movie. This movie makes an import call, which is responsible for loading the custom class.

```
import SimpleSocket;
```

```
var sock:SimpleSocket;
```

To create a socket connection, start by making a new instance of the SimpleSocket class, passing in the host and port information for the socket server you want to connect to.

```
sock = new SimpleSocket('127.0.0.1', 8888);
```

When the socket connection call is finished, you will want to assign listeners to the custom events. This simple class only has events for a successful connection and another for any connection error. You can expand the class and add more event handlers as needed.

```
sock.addEventListener(SimpleSocket.SOCK_CONNECTED, connected);
sock.addEventListener(SimpleSocket.SOCK_IOERROR, ioError);
```

The final step is to define the event handler functions, such as:

```
function ioError(e:Event):void
{
   trace("Can't connect to " + sock.host + " on port " + sock.port);
}
function connected(e:Event):void
{
   sock.sendMessage("are you hungry?");
}
```

You can now run the movie and should see the following output if you built or loaded the socket server code and the server is currently running.

> "Connected to [127.0.0.1] Socket Server Response: ARE YOU THERE?"

This class can be expanded upon to allow for more specific requirements, but you should have a basic understanding of how the socket system works in Flash. At this point you should also know how to construct a custom class to handle the majority of the socket connecting and communicating process.

The final section focuses on building a custom multiuser chat client using the information learned in the previous sections.

## Building a Chat Client with Sockets Using Flash and PHP

In the previous sections, you learned how to construct a simple PHP socket server. You then built a basic Flash client to communicate with the PHP socket server. In this section, you combine the steps into one real-world application. The application you will be building is a multiuser chat client running in Flash with a PHP socket server to handle the connections.

This multiuser chat application will allow multiple client connections to talk to each other with the admin being able to send specific messages about status and connection details.

### PHP socket server for the chat client

The PHP portion of the application will be two files: the actual socket server class and the calling page to start the socket server.

The socket server class skeleton looks like the following block of code. As you can see, the socket class has many methods. Breaking them up into easy-to-maintain portions will create a better product in the end.

```
class ChatServer
{
  ...

  function ChatServer($ip='192.168.1.110', $port=8888) {}

  public function startServer() {}

  public function stopServer() {}

  private function initLoop() {}

  private function createMasterClient() {}

  private function notifyClient($sockID, $buffer) {}

  private function notifyClients($clients, $sock, $buffer, $admin) {}

  private function handleError($str, $err) {}

  private function endSocket($sockID=null) {}

  private function serverMessage($str) {}

}
```

### Chat properties

The first part to focus on in the class is the properties, which are responsible for storing the various error messages, as well as connection details.

```
private $ipAddress = null;
private $port = null;

private $masterClient = null;
private $clients;

// Server Messages
private static $SOCKET_CREATE_FAIL = "socket_create() failed";
private static $SOCKET_BIND_FAIL = "socket_bind() failed";
private static $SOCKET_LISTEN_FAIL = "socket_listen() failed";
private static $SOCKET_ACCEPT_FAIL = "";

private $LINE_ENDING = "\n";
private static $SHOW_ERRORS = 1; // display errors (0=off, 1=on)
```

