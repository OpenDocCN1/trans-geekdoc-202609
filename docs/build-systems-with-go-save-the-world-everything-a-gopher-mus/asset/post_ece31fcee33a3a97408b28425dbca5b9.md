
Now v is a pointer to an integer. If we set this value, we are trying to modify the pointer. What we are looking for is the content that is been pointed by this pointer. This is where we use the Elem() method.

```go
var a int32 = 42
v := reflect.ValueOf(&a).Elem()
v.SetInt(16)
fmt.Println(v.Interface())
```

The settability of a field can be checked using the method `canSet()` as discussed in Example 5.9.

## 5.6 SUMMARY

In this Chapter, we explored how to use reflection in Go and how to use types, values, and tags. We enumerated the three laws of reflection and showed examples for each of the rules. Reflection is a powerful tool in advanced programming projects and will appear in different Chapters of this book. However, the developer must consider that code introspection comes with a cost in terms of performance, code readability, and maintenance. It is for this reason that reflection is expected to be used in certain scenarios where it is the only solution for a given problem.

# CHAPTER 6
CONCURRENCY

The title of this Chapter may sound intimidating. Concurrency is a tough topic in computer science that causes developer headaches. Frankly, Go was designed with simplicity in mind. It facilitates the creation of concurrent programs, inter-thread communication, and other topics that in other languages require deep tech knowledge. At the end of this Chapter you will understand concepts as goroutines, channels, and how they can be used to design sophisticated concurrent programs.

## 6.1 GOUTINES

A Goroutine is a lightweight thread managed by the Go runtime. Goroutines are declared using the go statement followed by the execution. Example 6.1 launches the Showit function that runs concurrently with the main function. Both functions print a message after sleeping (time.Sleep). The main function sleeps the time of Showit, which is why we have a ratio of two messages from one function versus the other. It is important to notice that the loop in Showit is endless; the program execution terminates when the main function finishes. Goroutines will remain running when the main function finishes.

### Example 6.1: Creation of goroutines.

```go
1 package main
2
3 import (
4    "fmt"
5    "time"
6 )
7
8 func Showit() {
9    for {
10        time.Sleep(time.Millisecond * 100)
11        fmt.Println("Here is it!!!")
12    }
13 }
14
15 func main() {
16
17    go Showit()
18
19    for i := 0; i < 5; i++ {
20        time.Sleep(time.Millisecond * 50)
21        fmt.Println("Where is it?")
22    }
23 }
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_69_0.png)

Goroutines are very lightweight with a very small memory demand (only 2Kb) when compared with a thread. We can expect to have several goroutines concurrently running. This can be as easy as invoking the go statement when required. Example 6.2 creates three goroutines that print a number after sleeping for a given time. The output shows the proportion of messages we expect depending on the sleeping time. Observe that multiple executions of this program may not return the same output. Why? Because the goroutines initialization time may vary and we are using the console output which may be a single output for multiple routines.

### Example 6.2: Creation of multiple goroutines.

```go
package main

import (
	"time"
	"fmt"
)

func ShowIt(time time.Duration, num int) {
	for {
		time.Sleep(time)
		fmt.Println(num)
	}
}

func main() {
	go ShowIt(time.Second, 100)
	go ShowIt(time.Millisecond*500,10)
	go ShowIt(time.Millisecond*250,1)
		time.Sleep(time.Millisecond*1200)
}
```

## 6.2 CHANNELS

Channels are a mechanism that provides communication for concurrently running functions. A channel can send or receive elements of a specified type.

Channels are instantiated using the make built-in function. Example 6.3 make(chan int) instantiates a channel that can send or receive integers. In this particular example, the generator runs in a goroutine that computes the sum of the first five integers and sends it through the channel. Meanwhile, the main function waits until something is sent through the channel with result := ch. Note that this last operation is blocking and will not be completed until something is sent through the channel.

### Example 6.3: Goroutine using reading channels.

```go
package main

import (
	"fmt"
)

main waits for result.
```

```go
5 "time"
6 )
7 func generator(ch chan int) {
8 sum := 0
10 for i:=0;i<5;i++ {
11 time.Sleep(time.Millisecond * 500)
12 sum = sum + i
13 }
14 ch <- sum
15 }
```

```go
17 func main() {
18
19 ch := make(chan int)
20
21 go generator(ch)
22
```

We can enhance this by using channels in both directions: reading and writing. **Example 6.4:** Goroutine using reading/write.

```go
package main

import (
	"fmt"
	"time"
)

func generator(ch chan int) {
	sum := 0
	for i:=0; i<5; i++ {
		time.Sleep(time.Millisecond * 500)
		sum = sum + i
	}
	ch <- sum
}

func main() {
	ch := make(chan int)

	go generator(ch)

	result := <-ch
	fmt.Println(result)
}
```

### 6.2.1 Buffered channels

Channels can be buffered or unbuffered. Buffered channels have capacity: make(chan int, n). In this case, the channel can store values.

**Example 6.5:** Channel buffering.

```go
package main

import (
	"fmt"
	"time"
)

func MrA(chan string) {
	time.Sleep(time.Millisecond * 500)
	ch <- "This is MrA"
}

func MrB(chan string) {
	time.Sleep(time.Millisecond * 500)
	ch <- "This is MrB"
}

func main() {
	ch := make(chan string, 1)

	ch <- "This is main"

	go MrA(ch)
	go MrB(ch)

	fmt.Println(<-ch)
	fmt.Println(<-ch)
	fmt.Println(<-ch)
}
```

### 6.2.2 Close

When a channel is not going to be used anymore, it can be terminated with the close() function. If a closed channel is used, it causes a runtime panic. Receivers can know if a channel was closed using the multi-value receive operation (x, ok := ch). The first returned is a value sent through the channel, the second is a boolean indicating whether the reception was correct or not. This second value can be used to identify closed channels.

In Example 6.6, a goroutine sends numbers through a channel. Once it has finished, the channel is closed. The receiver (main function) runs an endless loop consuming the elements through the channel. When the channel is closed, the found variable becomes false and we know that the channel was closed.

Example 6.6: close function in channels.

```go
package main

import (
	"fmt"
)

func generator(ch chan int) {
	sum := 0
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 500)
		sum = sum + i
	}
	ch <- sum
	close(ch)
}

func main() {
	ch := make(chan int)

	go generator(ch)

	for {
		result, ok := <-ch
		if !ok {
			break
		}
		fmt.Println(result)
	}
}
```
