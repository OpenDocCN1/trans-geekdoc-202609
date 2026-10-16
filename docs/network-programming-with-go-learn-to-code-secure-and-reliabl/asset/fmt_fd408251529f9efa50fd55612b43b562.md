
reasons, you won’t need to worry about fragmentation or packet order-ing when using Unix domain sockets. If you choose to forgo Unix domain sockets and exclusively use network sockets when communicating with local services (for example, to connect your application to a local database, a memory cache, and so on), you ignore significant security advantages and performance gains.

Though this system brings distinct advantages, it comes with a caveat:

Unix domain sockets are local to the node using them, so you cannot use them to communicate with other nodes, as you can with network sockets.

Therefore, Unix domain sockets may not be a good fit if you anticipate moving a service to another node or require maximum portability for your application. To maintain communication, you’d have to first migrate to a network socket.

# Binding to Unix Domain Socket Files

A Unix domain socket file is created when your code attempts to bind to an unused Unix domain socket address by using the net.Listen, net.ListenUnix, or net.ListenPacket functions. If the socket file for that address already exists, the operating system will return an error indicating that the address is in use. In most cases, simply removing the existing Unix domain socket file is enough to clear up the error. However, you should first make sure that the socket file exists not because a process is currently using that address but because you didn’t properly clean up the file from a defunct process.

If you wish to reuse a socket file, use the net package’s FileListener function to bind to an existing socket file. This function is beyond the scope of this book, but I encourage you to read its documentation.

## Changing a Socket File’s Ownership and Permissions

Once a service binds to the socket file, you can use Go’s os package to modify the file’s ownership and read/write permissions. Specifically, the os.Chown function allows you to modify the user and group that owns the file.

Windows does not support this function, though this function is supported on Windows Subsystem for Linux (WSL), Linux, and macOS, among others outside the scope of this book. We’ll look at the lines of code that change file ownership and permissions now but cover them in context later in this chapter.

The following line instructs the operating system to update the user and group ownership of the given file:

err := os.Chown("/path/to/socket/file", 1-1, 2100)

The os.Chown function accepts three arguments: the path to a file, the user ID of the owner 1, and the group ID of the owner 2. A user or group ID of -1 tells Go you want to maintain the current user or group ID. In this example, you want to maintain the socket file’s current user ID but set its group ID to 100, which here is assumed to be a valid group ID in the */etc/group* file.

Go’s os/user package includes functions to help you translate between user and group names and IDs. For example, this line of code uses the LookupGroup function to find the group ID for the *users* group:

grp, err := user.LookupGroup("users")

Provided user.LookupGroup did not return an error, the grp variable’s Gid field contains the group ID for the *users* group.

The os.Chmod function changes the file’s mode and the numeric notation of Unix-compatible permission bits. These bits inform the operating system of the file’s mode, the file’s user read/write/execute permissions, the file’s group read/write/execute permissions, and the read/write/execute permissions for any user not in the file’s group:

err := os.Chmod("/path/to/socket/file", os.ModeSocket|0660)

Unix Domain Sockets **143**

The os.Chmod function accepts a file path and an os.FileMode, which represents the file mode, the user permissions, the group permissions, and non-group user permissions. Since you’re dealing with a socket file, you should always set the os.ModeSocket mode on the file. You do that using a bitwise OR between the os.ModeSocket and the numeric file permission notation. Here, you’re passing the octal 0660, which gives the user and group read and write access but prevents anyone outside the group from reading or writing to the socket. You can read more about os.FileMode in Go’s documentation at *https://golang.org/pkg/os/#FileMode* and familiarize yourself with filesystem permissions numeric notation at *https://en.wikipedia.org/wiki/*

*File\_system\_permissions#Numeric\_notation*.

***Understanding Unix Domain Socket Types***

There are three types of Unix domain sockets: *streaming sockets*, which operate like TCP; *datagram sockets*, which operate like UDP; and *sequence packet* *sockets*, which combine elements of both. Go designates these types as unix, unixgram, and  unixpacket, respectively. In this section, we’ll write echo servers that work with each of these types.

The net.Conn interface allows you to write code once and use it across multiple network types. It abstracts many of the differences between the network sockets used by TCP and UDP and Unix domain sockets, which means that you can take code written for communication over TCP, for example, and use it over a Unix domain socket by simply changing the address and network type.

**The unix Streaming Socket**

The streaming Unix domain socket works like TCP without the overhead associated with TCP’s acknowledgments, checksums, flow control, and so on. The operating system is responsible for implementing the streaming inter-process communication over Unix domain sockets in lieu of TCP.

To illustrate this type of Unix domain socket, let’s write a function that creates a generic stream-based echo server (Listing 7-1). You’ll be able to use this function with any streaming network type. That means you can use it to create a TCP connection to a different node, but you’ll also be able to use it with the unix type to communicate with a Unix socket address.

**N O T E** 

*Linux, macOS, and Windows all support the unix network type.*

package echo

import (

"context"

"net"

)

func 1streamingEchoServer(ctx context.Context, network string,

**144** Chapter 7

 addr string) (net.Addr, error) {

s, err := 2net.Listen(network, addr)

if err != nil {

return nil, err

}

*Listing 7-1: Creating the streaming echo server function (* echo .go *)*

The streamingEchoServer function 1 accepts a string representing a stream-based network and a string representing an address and returns an address object and an error interface. You should recognize these arguments and return types from earlier in the book.

Since you’ve made the echo server a bit more generic by accepting a context, a network string, and an address string, you can pass it any stream-based network type, such as tcp, unix, or unixpacket. The address would then need to correspond to the network type. The context is used for signaling the server to close. If the network type is tcp, the address string must be an IP address and port combination, such as 127.0.0.1:80. If the network type is unix or unixpacket, the address must be the path to a nonexistent file. The socket file will be created when the echo server binds to it 2. Then the server will start listening for incoming connections.

Listing 7-2 completes the streaming echo server implementation.

*\--snip--*

go func() {

go func() {

1<-ctx.Done()

\_ = s.Close()

}()

for {

conn, err := 2s.Accept()

if err != nil {

return

}

go func() {

defer func() { \_ = conn.Close() }()

for {

buf := make(\[\]byte, 1024)

n, err := 3conn.Read(buf)

if err != nil {

return

}

\_, err = 4conn.Write(buf\[:n\])

if err != nil {

return

}

}

}()

Unix Domain Sockets **145**

}

}()

return s.Addr(), nil

}

*Listing 7-2: A stream-based echo server (* echo .go *)*

A listener created with either net.Listen or net.ListenUnix will auto-

matically remove the socket file when the listener exits. You can modify
