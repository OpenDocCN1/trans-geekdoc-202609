# Conclusion

Goroutines can be used to write concurrent programs in Golang.

When multiple goroutines execute at the same time, their sequence is not predictable. Any goroutine can start first or any goroutine can finish first.

When the main goroutine exits, all its children also exit.

If we want the parent goroutine to wait for the child goroutine to finish, then we use WaitGroup to control this.

The WaitGroup type has three useful methods: and

We can use MutexLock to protect a critical section so only one goroutine enters into the critical section.

We can use a channel for communication between two goroutines.

The <- operator can be used to send/read the message into/from the channel.

When a channel is closed, we cannot send more messages to the channel.