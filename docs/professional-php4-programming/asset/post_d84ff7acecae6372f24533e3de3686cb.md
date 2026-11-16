
As of PHP 4.0.6, the sockets APIs are still classified as "experimental". Most of the functions discussed in this section are subject to change in future versions with respect to the number and type of arguments, return values and in some cases, even the name of the function itself. Most of these are likely to be syntactic changes to the application programmer; however, it is not advisable to rely on these interfaces for production quality code until the dust settles on this topic.

### socket()

```
int socket(int domain, int type, int protocol)
```

This function creates a socket which is a communication endpoint variable. It takes two possible values for the domain argument, that is, AF_INET and AF_UNIX. If the argument is AF_INET, it indicates that the protocol family is the Internet protocol family or the TCP/IP suite of protocols. This argument is required since sockets can also be used for another mode of inter-process communication, such as UNIX domain sockets, in which case the value should be AF_UNIX.

Although the AF_UNIX argument is now supported on PHP versions built for Microsoft Windows, as of PHP 4.0.6 the behavior is incorrect and should be avoided wherever possible to enhance code portability. The type argument indicates the level of protocol interaction, for example, whether the socket interacts with the IP layer or with the transport layer. It also specifies the packet transfer mechanism, that is, if the communication is stream-based or connectionless. The table below has a list of possible values:

| Socket Type | Description |
| :--- | :--- |
| SOCK_STREAM | This indicates a stream-based reliable delivery service. |
| SOCK_DGRAM | This indicates a connectionless delivery service. |
| SOCK_SEQPACKET | This indicates that the packets are guaranteed to be delivered sequentially. |
| SOCK_RAW | This indicates that the layer of interaction is the IP layer or the network layer. |
| SOCK_RDM | This indicates a model of reliable but connectionless datagrams. Datagrams arrive in the order they are sent and the sender is notified of non-delivery, but unlike other reliable models, there is no need to set up a connection. |
| SOCK_PACKET | This indicates a model where the packet can be sent as-is. For example, Ethernet addresses can be sent on a per-packet basis. |

Not all combinations of the domain argument and the type argument make sense. For example, specifying AF_UNIX as the first argument and SOCK_RAW does not make any sense, since the UNIX stream-based protocol has nothing to do with the IP layer. Hence the third argument exists to disambiguate the various combinations. Since the implementation in PHP does not seem to be complete with regards to the third argument and as a value of 0 works for most situations, it seems that the safest thing to do is to specify the value as 0.

The return value of the socket function is an integer indicating a socket descriptor on which read/write operations can be performed. A negative return value indicates an error condition. This value can be passed to the strerror() function which returns a message string describing the error condition.

### bind()

```
int bind(int socket, string address [, int port])
```

When creating a server socket it is necessary to bind it to an IP address and a well-known port. The `bind()` function takes a socket descriptor as the first argument and the local address which is an IP address (in the case that the socket descriptor was created for the `AF_INET` protocol family) as the second argument. If the socket was created for the `AF_UNIX` family, the first argument is a UNIX pathname leading to the actual UNIX domain socket.

The `port` argument is valid only for the `AF_INET` case and indicates the port to which the server should bind. If a port is already occupied by another service, the `bind()` function will fail. If the return value is negative, it indicates an error condition, the textual description for which can be obtained by passing it as an argument to the `strerror()` function.

### connect()

```
int connect(int socket, string address [, int port])
```

After a client program has created a socket, it needs to connect to a server. The `connect()` function provides this functionality. The first argument is a socket descriptor returned as a result of a `socket()` call. The second argument is the IP address of the server if the `socket()` call specified the protocol family as `AF_INET`. It needs to be a UNIX path name if the protocol family was specified as `AF_UNIX` when the `socket()` call was made.

The `port` argument is valid only for the `AF_INET` case and indicates the port at which the remote server is listening. If the return value of the `connect()` function is negative, it indicates an error condition, the textual description for which can be obtained by passing it as an argument to the `strerror()` function.

### listen()

```
int listen(int socket, int backlog)
```

After a server application has created a socket and done a `bind()` to associate itself with the local IP address and its well-known port, it needs to listen to incoming requests from clients. The `listen()` function provides this functionality. It takes as the first argument, the `socket`, which needs to be listening for incoming connections and a `backlog` argument as the second which indicates the maximum number of requests that can be queued up for this socket.

A negative return value indicates an error condition and the return value can be passed to the `strerror()` function to get a textual description of the error.

### accept_connect()

```
int accept_connect(int socket)
```

As part of creating a server program we need to create a socket using the `socket()` function, bind it to an address and port number using the `bind()` function, and specify that it should listen to incoming connections using the `listen()` call. After this, we need to call the `accept_connect()` function passing the socket descriptor returned as the result of the `socket()` function as an argument. This function blocks until a new request arrives for the socket. When a new request arrives, it creates a new socket descriptor and returns it to the program, which may use it to read and write data from the connection. If the socket is non-blocking (see below for the socket_set_blocking() function) and no data is available at the socket as soon as accept_connect() is called, this function returns with an error code integer.

### fsockopen() and pfsockopen()

```
int fsockopen (string [udp://]hostname, int port [, int errno [, string errstr [, double timeout]]])
```

This is a general-purpose convenience function that can be used by clients to connect to a server. It encapsulates the functionality of creating a socket, resolving the server's IP address, and connecting to the server address at the specified port. It can be used to connect to TCP, UDP, and UNIX domain sockets:

- $fp = fsockopen("myTCPServer.wrox.com", 4567); will connect to a TCP socket listening on the server myTCPServer.wrox.com at port number 4567.
- $fp = fsockopen("udp://myUDPServer.wrox.com", 6789); will connect to a UDP socket listening on the server myUDPServer.wrox.com at port number 6789.
- $fp = fsockopen("/tmp/unixsocket456", 0); will connect to a UNIX domain socket addressed by the file-system path /tmp/unixsocket456. It is mandatory to set the port argument to 0 when UNIX domain sockets are to be used.

The optional arguments errno and errstr can be supplied in all of the above cases to indicate any error conditions that might arise when connecting to the socket. errno indicates the error number and errstr indicates the error message. If errno returns a value of 0 and the function returns false, this indicates a problem with initializing the socket.

Optionally, a timeout argument can also be specified with TCP and UDP sockets to indicate the number of seconds the function must wait before giving up on establishing a connection. A return value of false indicates failure. If the function succeeds, it returns a file pointer which can be used with functions capable of reading and writing to file pointers such as fgets() and fputs().

pfsockopen() has the same functionality as fsockopen() and takes the same type of arguments. The only difference being that while connections opened by fsockopen() are destroyed after a script exits and the ones opened by pfsockopen() will remain persistent even after the script exits.

> pfsockopen() has the same caveats as most other persistent functions and then some. The connection is persistent only in the Apache process that created the connection in the first place. If a subsequent request is serviced by a different Apache process we need to call this function again. Further, it is entirely possible that application logic on the server may not tolerate an idle connection beyond a certain interval and may close the connection. This means that it is not safe to assume that the connection will always be available.
