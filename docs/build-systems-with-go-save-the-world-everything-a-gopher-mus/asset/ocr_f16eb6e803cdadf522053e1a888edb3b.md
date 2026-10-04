```
5 "time"
6 \)
7
8 func sender(out chan int) {
9  for i:=0;i<5;i++ {
10   time.Sleep(time.Millisecond * 500)
11  out <- i
12 }
13 close(out)
14 fmt.Println("sender finished")
15 }
16
17 func main() {
18
19 ch := make(chan int)
20
21 go sender(ch)
22
23 for {
24  num, found := <- ch
25  if found {
26    fmt.Println(num)
27  }
28 } else {
29  fmt.Println("finished")
30  break
31  
32 }
33 }
```

3
4
finished

# 6.2.3 Consuming data with range

Normally, we cannot know beforehand the number of values that are going to be sent through a channel. We can use to block the execution and wait for values until the channel is closed. Check how Example 6.7 in the main function consumes data from the channel until this is closed independently of the number of generated values.

> Example 6.7: Channel consumption using range.

```
1 package main
2
3 import "fmt"
4 func generator(ch chan int) {
5  for i:=0;i<5;i++ {
6   ch <- 1
7 }
8 close(ch)
9 }
10
11 func main() {
12  ch := make(chan int)
13 }
```

1
2
3
4
5
6
7
8
Done