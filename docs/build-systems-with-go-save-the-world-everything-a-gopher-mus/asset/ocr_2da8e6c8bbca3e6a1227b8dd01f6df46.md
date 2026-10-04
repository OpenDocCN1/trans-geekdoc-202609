```
14 go generator(ch)
15
16 for x := range(ch) {
17 fmt.Println(x)
18 }
19 fmt.Println("Done")
20 }
```

#  6.2.4 Channels direction

The data flow direction in a channel can be specified.

```
ch := make(chan int) // sender and receiver
ch := make<-(chan int) // receiver
ch := make(chan int) // sender
```

This provides better type-safety and permits better utilization of channels. In Example 6.8, we define sender and receiver functions to send and receive values respectively. Because channel directions are set, if receiver tries to send data using the channel an error at compilation time will appear. And similarly, sender cannot read data from the channel.

# Example 6.8: Channels direction.

```
1 package main
2
3 import (
4 "fmt"
5 "time"
6 )
7
8 func receiver(input <- chan int) {
9 for i := range input {
10 fmt.Println(i)
11 }
12 }
13
14 func sender(output chan<- int, n int) {
15 for i := 0; i < n; i++ {
16 time.Sleep(time.Millisecond * 500)
17 output <- i * i
18 }
19 close(output)
20 }
21
22
23 func main() {
24
25 ch := make(chan int, 4)
26
27 go sender(ch, 4)
28 go receiver(ch)
29 }
```