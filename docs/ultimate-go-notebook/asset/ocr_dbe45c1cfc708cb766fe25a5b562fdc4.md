```
Listing 6.39
func drop() {
  const cap = 100
  ch := make(chan string, cap)

  go func() {
    for p := range ch {
      fmt.Println("child : recv'd signal :", p)
    }
  }()\n  const work = 2000
  for w := 0; w < work; w++ {
    select {
      case ch <- "data":
        fmt.Println("parent : sent signal :", w)
      default:
        fmt.Println("parent : dropped data :", w)
    }
  }
  close(ch)
  fmt.Println("parent : sent shutdown signal")

  time.Sleep(time.Second)
  fmt.Println("---------------------------------")
}
```

The code starts with the creation of a buffered channel. This is a case where it's reasonable to have a large buffer. Identifying the capacity value (buffer size) will require work in the lab. I want a number that allows the service to maintain reasonable levels of resource usage and performance when the buffer is full.

Next a child Goroutine using the pooling pattern is created. This child Goroutine is waiting for a signal to receive work on. In this example, having only one child Goroutine will cause back pressure quickly on the sending side. One child Goroutine will not be able to process all the work in time before the buffer gets full. Representing the service is at capacity.

Inside the for loop, I use the select of statement. The select statement is a blocking call that allows the parent Goroutine to handle multiple channel operations at the same time. Each case represents a channel operation, a send or a receive. However, this select is using the default keyword as well, which turns the select into a non-blocking call.

The key to implementing this pattern is the use of default. If the channel buffer is full, that will cause the case statement to block since the send can't complete. When every case in a select is blocked, and there is a default, the default is then executed. This is where the drop code is placed.

In the drop code, I can now decide what to do with the request. I can return a 500 to the caller. I could store the request somewhere else. The key is I have options.