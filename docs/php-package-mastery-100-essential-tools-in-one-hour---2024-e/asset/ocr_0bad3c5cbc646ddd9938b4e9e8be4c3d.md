# 12. sockets

The sockets extension in PHP allows for the creation of socket-based connections, enabling PHP scripts to communicate with other servers or clients over the network. It supports various socket operations like creating, binding, listening, accepting connections, sending, and receiving data over TCP/IP or UDP.

Ex:sockets

```
$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
$result = socket_connect($socket, 'www.example.com', 80);
$message = "GET / HTTP/1.1\r\nHost: www.example.com\r\nConnection: Close\r\n\r\n";
socket_write($socket, $message, strlen($message));
$result = socket_read($socket, 1024);
socket_close($socket);
echo $result;
?>
```

The code displays the HTTP response received from www.example.com.