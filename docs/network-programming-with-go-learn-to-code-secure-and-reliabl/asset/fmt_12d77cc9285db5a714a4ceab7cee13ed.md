
proxy supports replies if the `from` reader implements the `io.Writer` interface and the `to` writer implements the `io.Reader` interface.

Listing 4-16 creates a test to make sure the proxy functions as you expect.

Sending TCP Data `89`

`--snip--`

func TestProxy(`t *testing.T`) {

var wg sync.WaitGroup

// server listens for a "ping" message and responds with a

// "pong" message. All other messages are echoed back to the client.

1 server, err := net.Listen("tcp", "127.0.0.1:")

if err != nil {

t.Fatal(err)

}

wg.Add(1)

go func() {

defer wg.Done()

for {

conn, err := server.Accept()

if err != nil {

return

}

go func(c net.Conn) {

defer c.Close()

for {

buf := make(`[]byte`, 1024)

n, err := c.Read(buf)

if err != nil {

if err != io.EOF {

t.Error(err)

}

return

}

switch msg := string(buf[:n]); msg {

case "ping":

\_, err = c.Write(`[]byte("pong")`)

default:

\_, err = c.Write(buf[:n])

}

if err != nil {

if err != io.EOF {

t.Error(err)

}

return

}

}

}(conn)

}

}()

**90** Chapter 4

 }()

`--snip--`

Listing 4-16: Creating the listener (* proxy_test .go *)

You start by initializing a server 1 that listens for incoming connections. It reads bytes from each connection, replies with the string "pong" when it receives the string "ping," and echoes any other message it receives.

Listing 4-17 continues the test implementation.

`--snip--`

// proxyServer proxies messages from client connections to the

// destinationServer. Replies from the destinationServer are proxied

// back to the clients.

1 proxyServer, err := net.Listen("tcp", "127.0.0.1:")

if err != nil {

t.Fatal(err)

}

wg.Add(1)

go func() {

defer wg.Done()

for {

conn, err := 2proxyServer.Accept()

if err != nil {

return

}

go func(from net.Conn) {

defer from.Close()

to, err := 3net.Dial("tcp",

server.Addr().String())

if err != nil {

t.Error(err)

return

}

defer to.Close()

err = 4proxy(from, to)

if err != nil && err != io.EOF {

t.Error(err)

}

}(conn)

}

}()

`--snip--`

Listing 4-17: Set up the proxy between the client and server (* proxy_test .go *)

You start by initializing a server 1 that listens for incoming connections. It reads bytes from each connection, replies with the string "pong" when it receives the string "ping," and echoes any other message it receives.

Listing 4-18 implements the client portion of the test.

`--snip--`

conn, err := net.Dial("tcp", proxyServer.Addr().String())

if err != nil {

t.Fatal(err)

}

1 msgs := `[]struct{ Message, Reply string }{

{"ping", "pong"},

{"pong", "pong"},

{"echo", "echo"},

{"ping", "pong"},

}`

for i, m := range msgs {

\_, err = conn.Write(`[]byte(m.Message)`)

if err != nil {

t.Fatal(err)

}

buf := make(`[]byte`, 1024)

n, err := conn.Read(buf)

if err != nil {

t.Fatal(err)

}

actual := string(buf[:n])

t.Logf("%q -> proxy -> %q", m.Message, actual)

if actual != m.Reply {

t.Errorf("%d: expected reply: %q; actual: %q",

i, m.Reply, actual)

}

}

\_ = conn.Close()

\_ = proxyServer.Close()

\_ = server.Close()

**92** Chapter 4

 wg.Wait()

}

*Listing 4-18: Proxying data from an upstream server to a downstream server*

*(* proxy_test .go *)*

You run the proxy through a series of tests 1 to verify that your ping

messages result in pong replies and that the destination echoes anything

else you send. The output should look like the following:

$ `go test` 1`-race -v proxy_test.go`

\=== RUN TestProxy

\--- PASS: TestProxy (0.00s)

proxy_test.go:138: "ping" -> proxy -> "pong"

proxy_test.go:138: "pong" -> proxy -> "pong"

proxy_test.go:138: "echo" -> proxy -> "echo"

proxy_test.go:138: "ping" -> proxy -> "pong"

PASS

ok command-line-arguments 1.018s

I’m in the habit of running my tests with the -race flag 1 to enable the

race detector. The race detector can help alert you to data races that need

your attention. Although not necessary for this test, enabling it is a good

habit.

***Monitoring a Network Connection***

The `io` package includes useful tools that allow you to do more with

network data than just send and receive it using connection objects. For

example, you could use `io.MultiWriter` to write a single payload to multiple

network connections. You could also use `io.TeeReader` to log data read

from a network connection. Listing 4-19 gives an example of using the

`io.TeeReader` and `io.MultiWriter` to log all network traffic on a TCP listener.

package main

import (

`io`

`log`

`net`

`os`

)

// Monitor embeds a log.Logger meant for logging network traffic.

type Monitor struct {

`*log.Logger`

}

// Write implements the io.Writer interface.

func (m `*Monitor`) 1Write(p `[]byte`) (int, error) {

return len(p), m.Output(2, string(p))

}

Sending TCP Data `93`

func ExampleMonitor() {

2 monitor := &Monitor{Logger: log.New(os.Stdout, "monitor: ", 0)}

listener, err := net.Listen("tcp", "127.0.0.1:")

if err != nil {

monitor.Fatal(err)

}

done := make(chan struct{})

go func() {

defer close(done)

conn, err := listener.Accept()

if err != nil {

return

}

defer conn.Close()

b := make(`[]byte`, 1024)

3 r := io.TeeReader(conn, monitor)

n, err := r.Read(b)

if err != nil && err != io.EOF {

monitor.Println(err)

return

}

4 w := io.MultiWriter(conn, monitor)

\_, err = w.Write(b[:n]) // echo the message

if err != nil && err != io.EOF {

monitor.Println(err)

return

}

}()

`--snip--`

Listing 4-19: Using `io.TeeReader` and `io.MultiWriter` to capture a network connection’s input and output (* monitor_test .go *)

You create a new struct named Monitor that embeds a log.Logger for the

purposes of logging the server’s network traffic. Since the `io.TeeReader` and

the `io.MultiWriter` expect an io.Writer, the monitor implements the io.Writer

interface 1.

You start by creating an instance of Monitor 2 that writes to os.Stdout.

You use the monitor in conjunction with the connection object in an

io.TeeReader 3. This results in an io.Reader that will read from the network

connection and write all input to the monitor before passing along the input

to the caller. Likewise, you log server output by creating an io.MultiWriter 4,

writing to the network connection and the monitor.

**94** Chapter 4

Listing 4-20 details the client portion of the example and its output.

`--snip--`

conn, err := net.Dial("tcp", listener.Addr().String())

if err != nil {

monitor.Fatal(err)

}

\_, err = 1conn.Write(`[]byte("Test\\n")`)

if err != nil {

monitor.Fatal(err)

}

\_ = conn.Close()

<-done

// 2Output:

// monitor: Test

// monitor: Test

}

*Listing 4-20: The client implementation and example output (* monitor_test .go *)* When you send the message Test\\n  1, it’s logged to os.Stdout twice 2:

once when you read the message from the connection, and again when

you echo the message back to the client. If you want to get fancy, you could

decorate the log entries to differentiate between incoming and outgoing

data. One way to do this would be to create an object that implements

the io.Writer interface and embeds the monitor. When its Write method is

called, it prepends the data with the prefix before passing the data along

to the monitor’s Write method.

Although using the io.TeeReader and the io.MultiWriter in this fashion

is powerful, it isn’t without a few caveats. First, both the io.TeeReader and

the io.MultiWriter will block while writing to your writer. Your writer will

add latency to the network connection, so be mindful not to block too
