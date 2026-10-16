
Listing 3-6 illustrates a test that accomplishes the same functionality as

DialTimeout, using context instead.

package ch03

import (

`context`

`net`

`syscall`

Reliable TCP Data Streams `57`

`testing`

`time`

)

func TestDialContext(t \*testing.T) {

1 dl := time.Now().Add(5 \* time.Second)

2 ctx, cancel := context.WithDeadline(context.Background(), dl)

3 defer cancel()

var d net.Dialer // DialContext is a method on a Dialer

d.Control = 4func(\_, \_ string, \_ syscall.RawConn) error {

// Sleep long enough to reach the context's deadline.

time.Sleep(5\*time.Second + time.Millisecond)

return nil

}

conn, err := d.DialContext(5ctx, "tcp", "10.0.0.0:80")

if err == nil {

conn.Close()

t.Fatal("connection did not time out")

}

nErr, ok := err.(net.Error)

if !ok {

t.Error(err)

} else {

if !nErr.Timeout() {

t.Errorf("error is not a timeout: %v", err)

}

}

6 if ctx.Err() != context.DeadlineExceeded {

t.Errorf("expected deadline exceeded; actual: %v", ctx.Err())

}

}

*Listing 3-6: Using a context with a deadline to time out the connection at empt* *(* dial_context_test .go *)*

Before you make a connection attempt, you create the context with

a deadline of five seconds into the future 1, after which the context will

automatically cancel. Next, you create the context and its cancel function by

using the context.WithDeadline function 2, setting the deadline in the pro-

cess. It’s good practice to defer the cancel function 3 to make sure the con-

text is garbage collected as soon as possible. Then, you override the dialer’s

Control function 4 to delay the connection just long enough to make sure

you exceed the context’s deadline. Finally, you pass in the context as the

first argument to the DialContext function 5. The sanity check 6 at the end

of the test makes sure that reaching the deadline canceled the context, not

an erroneous call to cancel.

As with DialTimeout, if a host resolves to multiple IP addresses, Go starts

a connection race between each IP address, giving the primary IP address

a head start. The first connection to succeed persists, and the remaining

contenders cancel their connection attempts. If all connections fail or the

context reaches its deadline, net.Dialer.DialContext returns an error.

**58** Chapter 3

**Aborting a Connection by Canceling the Context**

Another advantage to using a context is the cancel function itself. You can

use it to cancel the connection attempt on demand, without specifying a

deadline, as shown in Listing 3-7.

package ch03

import (

`context`

`net`

`syscall`

`testing`

`time`

)

func TestDialContextCancel(t \*testing.T) {

ctx, cancel := 1context.WithCancel(context.Background())

sync := make(chan struct{}

2 go func() {

defer func() { sync <- struct{}{} }()

var d net.Dialer

d.Control = func(\_, \_ string, \_ syscall.RawConn) error {

time.Sleep(time.Second)

return nil

}

conn, err := d.DialContext(ctx, "tcp", "10.0.0.1:80")

if err != nil {

t.Log(err)

return

}

conn.Close()

t.Error("connection did not time out")

}

3 cancel()

<-sync

if ctx.Err() != 4context.Canceled {

t.Errorf("expected canceled context; actual: %q", ctx.Err())

}

}

*Listing 3-7: Directly canceling the context to abort the connection at empt*

*(* dial_cancel_test .go *)*

Instead of creating a context with a deadline and waiting for the dead-

line to abort the connection attempt, you use context.WithCancel to return

a context and a function to cancel the context 1. Since you’re manually

canceling the context, you create a closure and spin it off in a goroutine to

handle the connection attempt 2. Once the dialer is attempting to connect

to and handshake with the remote node, you call the cancel function 3

Reliable TCP Data Streams **59**

to cancel the context. This causes the DialContext method to immediately return with a non-nil error, exiting the goroutine. You can check the context’s Err method to make sure the call to cancel was what resulted in the

canceled context, as opposed to a deadline in Listing 3-6. In this case, the

context’s Err method should return a context.Canceled error 4.

**Canceling Multiple Dialers**

You can pass the same context to multiple DialContext calls and cancel

all the calls at the same time by executing the context’s cancel function.

For example, let’s assume you need to retrieve a resource via TCP that is

on several servers. You can asynchronously dial each server, passing each

dialer the same context. You can then abort the remaining dialers after you

receive a response from one of the servers.

In Listing 3-8, you pass the same context to multiple dialers. When you

receive the first response, you cancel the context and abort the remaining

dialers.

package ch03

import (

`context`

`net`

`sync`

`testing`

`time`

)

func TestDialContextCancelFanOut(t \*testing.T) {

1 ctx, cancel := context.WithDeadline(

context.Background(),

time.Now().Add(10\*time.Second),

)

listener, err := net.Listen("tcp", "127.0.0.1:")

if err != nil {

t.Fatal(err)

}

defer listener.Close()

2 go func() {

// Only accepting a single connection.

conn, err := listener.Accept()

if err == nil {

conn.Close()

}

}()

3 dial := func(ctx context.Context, address string, response chan int,

id int, wg \*sync.WaitGroup) {

defer wg.Done()

var d net.Dialer

**60** Chapter 3

 c, err := d.DialContext(ctx, "tcp", address)

if err != nil {

return

}

c.Close()

select {

case <-ctx.Done():

case response <- id:

}

}

res := make(chan int)

var wg sync.WaitGroup

4 for i := 0; i < 10; i++ {

wg.Add(1)

go dial(ctx, listener.Addr().String(), res, i+1, &wg)

}

5 response := <-res

cancel()

wg.Wait()

close(res)

if ctx.Err() != 6context.Canceled {

t.Errorf("expected canceled context; actual: %s",

ctx.Err(),

)

}

t.Logf("dialer %d retrieved the resource", response)

}

*Listing 3-8: Canceling all outstanding dialers after receiving the first response* *(* dial_fanout_test .go *)*

You create a context by using context.WithDeadline 1 because you want

to have three potential results when checking the context’s Err method:

context.Canceled, context.DeadlineExceeded, or nil. You expect Err will return

the context.Canceled error, since your test aborts the dialers with a call to the cancel function.

First, you need a listener. This listener accepts a single connection and

closes it after the successful handshake 2. Next, you create your dialers. Since

you’re spinning up multiple dialers, it makes sense to abstract the dialing code

to its own function 3. This anonymous function dials out to the given address

by using DialContext. If it succeeds, it sends the dialer’s ID across the response channel, provided you haven’t yet canceled the context. You spin up multiple

dialers by calling dial in separate goroutines using a for loop 4. If dial blocks on the call to DialContext because another dialer won the race, you cancel the

context, either by way of the cancel function or the deadline, causing the dial

function to exit early. You use a wait group to make sure the test doesn’t pro-

ceed until all dial goroutines terminate after you cancel the context.

Reliable TCP Data Streams **61**

Once the goroutines are running, one will win the race and make a successful connection to the listener. You receive the winning dialer’s ID on the

res channel 5, then abort the losing dialers by canceling the context. At this

point, the call to wg.Wait blocks until the aborted dialer goroutines return.

Finally, you make sure it was your call to cancel that caused the cancelation

of the context 6. Calling cancel does not guarantee that Err will return

context.Canceled. The deadline can cancel the context, at which point calls

to cancel become a no-op and Err will return context.DeadlineExceeded. In

practice, the distinction may not matter to you, but it’s there if you need it.

***Implementing Deadlines***
