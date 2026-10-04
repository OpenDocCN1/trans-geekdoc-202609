```
22 for {
23 select < {
24 case <- timer.C:
25 fmt.Fprint("timer -> %d\n", x)
26 case <- ticker.C:
27 fmt.Fprint("ticker -> %d\n", x)
28 }
29 if x != 10 {
30 break
31 }
32 }
33 }
```

Example 6.13, checks the value of x over time using a Timer and a Ticker. The worker increases x by one every 500 milliseconds. The select statement can be used here to react when timer and ticker send an event. ticker will wake up every second x to be increased by two. Notice that worker sleeps for half second in every iteration. For timer there will be the single operation after five seconds. Notice, that worker could be implemented using a Ticker instead of time.Sleep.

# Example 6.14: Timer and Ticker management.

```
1 package main
2
3 import (
4 "fmt"
5 "time"
6 }
7
8 func reaction(t *time.Ticker) {
9 for {
10 select {
11 case x := <-t.C:
12 fmt.Println("quick", x)
13 }
14 }
15 }
16
17 func slowReaction(t *time.Timer) {
18 select {
19 case x := <-t.C:
20 fmt.Println("slow", x)
21 }
22 }
23
24 func main() {
25 quick := time.NewTicker(time.Second)
26 slow := time.NewTicker(time.Second * 5)
27 stopper := time.NewTimer(time.Second * 4)
28 go reaction(quick)
29 go slowReaction(slow)
30
31 <- stopper.C
```