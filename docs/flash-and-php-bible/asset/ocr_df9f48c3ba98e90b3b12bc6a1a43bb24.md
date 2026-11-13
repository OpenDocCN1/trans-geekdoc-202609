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

  private function notifyClients($clients, $sock, $buffer,
  $admin) {}

  private function handleError($str, $err) {}

  private function endSocket($sockID=null) {}

  private function serverMessage($str) {}

}
```

# Chat properties

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