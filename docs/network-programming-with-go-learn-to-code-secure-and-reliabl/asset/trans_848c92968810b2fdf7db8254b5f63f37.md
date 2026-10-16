
ucred, err = 2unix.GetsockoptUcred(int(3file.Fd()), unix.SOL_SOCKET, unix.SO_PEERCRED)

if err == unix.EINTR {
    continue // syscall interrupted, try again
}

if err != nil {
    log.Println(err)
    return false
}

break

}

u, err := 4user.LookupId(string(ucred.Uid))

if err != nil {
    log.Println(err)
    return false
}

gids, err := 5u.GroupIds()

if err != nil {
    log.Println(err)
    return false
}

for _, gid := range gids {
    if _, ok := 6groups[gid]; ok {
        Unix Domain Sockets **155**
        return true
    }
}

return false

}

*Listing 7-13: Retrieving the peer credentials for a socket connection (* creds/auth/al owed\_

linux .go *)*

To retrieve the peer’s Unix credentials, you first grab the underlying

file object from net.UnixConn 1, the object that represents your side of the

Unix domain socket connection. It’s analogous to net.TCPConn of a TCP con-

nection in Go. Since you need to extract the file descriptor details from the

connection, you cannot simply rely on the net.Conn interface that you receive

from the listener’s Accept method. Instead, your Allowed function requires

the caller to pass in a pointer to the underlying net.UnixConn object, typically

returned from the listener’s AcceptUnix method. You’ll see this method in

action in the next section.

You can then pass the file object’s descriptor 3, the protocol-level unix

.SOL_SOCKET, and the option name unix.SO_PEERCRED to the unix.GetsockoptUcred

function 2. Retrieving socket options from the Linux kernel requires that

you specify both the option you want and the level at which the option resides.

The unix.SOL_SOCKET tells the Linux kernel you want a socket-level option, as

opposed to, for example, unix.SOL_TCP, which indicates TCP-level options. The

unix.SO_PEERCRED constant tells the Linux kernel that you want the peer creden-

tials option. If the Linux kernel finds the peer credentials option at the Unix

domain socket level, unix.GetsockoptUcred returns a pointer to a valid unix.Ucred object.

The unix.Ucred object contains the peer’s process, user, and group IDs.

You pass the peer’s user ID to the user.LookupId function 4. If successful,

you then retrieve a list of group IDs from the user object 5. The user can

belong to more than one group, and you want to consider each one for

access. Finally, you check each group ID against a map of allowed groups 6.

If any one of the peer’s group IDs is in your map, you return true, allowing

the peer to connect.

This example is largely didactic. You can achieve similar results by

assigning group ownership to the socket file, as we discussed in [“Changing](#index_split_003.html#p165)

[a Socket File’s Ownership and Permissions” on page 143](#index_split_003.html#p165). However, knowledge of group membership could be used for access control and other secu-

rity decisions within your application.

***Writing the Service***

Let’s now use this function in a service that you can run from the command

line. This service will accept one or more group names found in the Linux

operating system’s */etc/group* file as arguments on the command line and

begin listening to a Unix domain socket file. The service will allow clients to

connect only if they are a member of one of the groups specified on the com-

mand line. Clients can then make a Unix domain socket connection to the

**156** Chapter 7

service. The service will retrieve the peer credentials of the client and either allow the client to remain connected, if the client is a member of one of the

allowed groups, or immediately disconnect the unauthorized client. The ser-

vice doesn’t do anything beyond authenticating the client’s group ID.

In Listing 7-14, you specify the imports you’ll need and create a mean-

ingful usage message for the service.

package main

import (

"flag"

"fmt"

"log"

"net"

"os"

"os/signal"

"os/user"

"path/filepath"

"github.com/awoodbeck/gnp/ch07/creds/auth"

)

func init() {

flag.Usage = func() {

\_, \_ = fmt.Fprintf(flag.CommandLine.Output(),

"Usage:\\n\\t%s 1<group names>\\n", filepath.Base(os.Args\[0\]))

flag.PrintDefaults()

}

}

*Listing 7-14: Expecting group names on the command line (* creds/creds .go *)* Our application expects a series of group names as arguments 1. You’ll

add the group ID for each group name to the map of allowed groups. The

code in Listing 7-15 parses these group names.

*\--snip--*

func parseGroupNames(args \[\]string) map\[string\]struct{} {

groups := make(map\[string\]struct{})

for \_, arg := range args {

grp, err := 1user.LookupGroup(arg)

if err != nil {

log.Println(err)

continue

}

groups\[2grp.Gid\] = struct{}{}

}

return groups

}

*Listing 7-15: Parsing group names into group IDs (* creds/creds .go *)*

Unix Domain Sockets **157**

The parseGroupNames function accepts a string slice of group names, retrieves the group information for each group name 1, and inserts

each group ID into the groups map 2.

Listing 7-16 ties the last few listings together into a service that you can

connect to from the command line.

*\--snip--*

func main() {

flag.Parse()

groups := parseGroupNames(flag.Args())

socket := filepath.Join(os.TempDir(), "creds.sock")

addr, err := net.ResolveUnixAddr("unix", socket)

if err != nil {

log.Fatal(err)

}

s, err := net.ListenUnix("unix", addr)

if err != nil {

log.Fatal(err)

}

c := make(chan os.Signal, 1)

signal.Notify(c, 1os.Interrupt)

2 go func() {

<-c

\_ = s.Close()

}()

fmt.Printf("Listening on %s ...\\n", socket)

for {

conn, err := 3s.AcceptUnix()

if err != nil {

break

}

if 4auth.Allowed(conn, groups) {

\_, err = conn.Write(\[\]byte("Welcome\\n"))

if err == nil {

// handle the connection in a goroutine here

continue

}

} else {

\_, err = conn.Write(\[\]byte("Access denied\\n"))

}

if err != nil {

log.Println(err)

}

\_ = conn.Close()

}

}

*Listing 7-16: Authorizing peers based on their credentials (* creds/creds .go *continued)* **158** Chapter 7

You start by parsing the command line arguments to create the map of allowed group IDs. You then create a listener on the */tmp/creds.sock* socket.

The listener accepts connections by using AcceptUnix 3 so a \*net.UnixConn

is returned instead of the usual net.Conn, since your auth.Allowed function

requires a \*net.UnixConn type as its first argument. You then determine

whether the peer’s credentials are allowed 4. Allowed peers stay connected.

Disallowed peers are immediately disconnected.

Since you’ll execute this service on the command line, you’ll stop the

service by sending an interrupt signal, usually with the ctrl-C key combina-

tion. However, this signal abruptly terminates the service before Go has a

chance to clean up the socket file, despite your diligent use of net.ListenUnix.

Therefore, you need to listen for this signal 1 and spin off a goroutine in

which you gracefully close the listener after receiving the signal 2. This will

make sure Go properly cleans up the socket file.

***Testing the Service with Netcat***

Netcat is a popular command line utility that allows you to make TCP, UDP,

and Unix domain socket connections. You’ll use it to test the service from

the command line. You can likely find Netcat in your Linux distribution’s

package manager. For example, to install the OpenBSD rewrite of Netcat

on Debian 10, run the following command:

$ **sudo apt install netcat-openbsd**

The command uses the sudo command line utility to run apt install

netcat-openbsd masquerading as the root user. CentOS 8.1 offers Nmap’s

Netcat replacement. Run this command to install it:

$ **sudo dnf install nmap-ncat**

Once it’s installed, you should find the *nc* binary in your PATH environ-

ment variable.

Before you can connect to your credential-checking service, you need

to run the service so that it binds to a socket file:

$ **cd $GOPATH/src/github.com/awoodbeck/gnp/ch07/creds**

$ **go run . -- users staff**

Listening on /tmp/creds.sock …
