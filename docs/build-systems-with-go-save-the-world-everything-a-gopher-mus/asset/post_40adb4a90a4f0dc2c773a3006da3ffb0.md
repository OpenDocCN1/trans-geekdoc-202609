
```go
import "time"

func sender(out chan int) {
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 500)
		out <- i
	}
	close(out)
	fmt.Println("sender finished")
}

func main() {

	ch := make(chan int)

	go sender(ch)

	for {
		num, found := <-ch
		if found {
			fmt.Println(num)
		} else {
			fmt.Println("finished")
			break
		}
	}
}
```

finished

# 6.2.3 Consuming data with range

Normally, we cannot know beforehand the number of values that are going to be sent through a channel. We can use range to block the execution and wait for values until the channel is closed. Check how Example 6.7 in the main function consumes data from the channel until this is closed independently of the number of generated values.

> Example 6.7: Channel consumption using range.

```go
package main

import "fmt"
func generator(ch chan int) {
	for i := 0; i < 5; i++ {
		ch <- 1
	}
	close(ch)
}

func main() {
	ch := make(chan int)
	go generator(ch)

	for x := range ch {
		fmt.Println(x)
	}
	fmt.Println("Done")
}
```

# 6.2.4 Channels direction

The data flow direction in a channel can be specified.

```go
ch := make(chan int) // sender and receiver
ch := make(chan int) // receiver
ch := make(chan int) // sender
```

This provides better type-safety and permits better utilization of channels. In Example 6.8, we define sender and receiver functions to send and receive values respectively. Because channel directions are set, if receiver tries to send data using the channel an error at compilation time will appear. And similarly, sender cannot read data from the channel.

# Example 6.8: Channels direction.

```go
package main

import (
	"fmt"
	"time"
)

func receiver(input <-chan int) {
	for i := range input {
		fmt.Println(i)
	}
}

func sender(output chan<- int, n int) {
	for i := 0; i < n; i++ {
		time.Sleep(time.Millisecond * 500)
		output <- i * i
	}
	close(output)
}

func main() {

	ch := make(chan int, 4)

	go sender(ch, 4)
	go receiver(ch)
	time.Sleep(time.Second * 5)
	fmt.Println("Done")

}
```

# 6.3 SELECT

The select statement is somehow similar to the switch statement. From a set of send/receive operations, it blocks the execution until one is ready. Example 6.9, executes two different goroutines that send values through two different channels. See how the select statement can receive operations in a single operation. Inside the select, cases are evaluated in the same order they are defined. If two or more cases are ready then, a pseudo-random selection chooses the next one. The select statement is executed only for a single operation, or to keep waiting for more messages it has to be iteratively executed like in a loop.

**Example 6.9:** select.

```go
package main

import (
	"fmt"
	"strconv"
	"time"
)

func sendNumbers(out chan int) {
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 500)
		out <- i
	}
	fmt.Println("no more numbers")
}

func sendMsgs(out chan string) {
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 300)
		out <- strconv.Itoa(i)
	}
	fmt.Println("no more msgs")
}

func main() {
	numbers := make(chan int)
	msgs := make(chan string)

	go sendNumbers(numbers)
	go sendMsgs(msgs)

	for i := 0; i < 10; i++ {
		select {
		case num := <-numbers:
			fmt.Printf("number %d\n", num)
		case msg := <-msgs:
			fmt.Printf("msg %s\n", msg)
		}
	}
}
```

select multi-value reception (x, ok := ch). This feature can be used to know if a channel is ready for reception or not. Example 6.10 extends the previous example to stop data reception when both channels are closed. Remember that in multi-value reception, the second value turns false when the channel is closed. Compared with the previous example we do not need to know beforehand the number of messages to be received. We can wait until

# Example 6.10: select with multi values.

```go
package main

import (
	"fmt"
	"strconv"
	"time"
)

func sendNumbers(out chan int) {
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 500)
		out <- i
	}
	fmt.Println("no more numbers")
	close(out)
}

func sendMsgs(out chan string) {
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 300)
		out <- strconv.Itoa(i)
	}
	fmt.Println("no more msgs")
	close(out)
}

func main() {
	numbers := make(chan int)
	msgs := make(chan string)

	go sendNumbers(numbers)
	go sendMsgs(msgs)

	closedNums, closedMsgs := false, false
	for !closedNums || !closedMsgs {
		select {
		case num, ok := <-numbers:
			if ok {
				fmt.Printf("%d\n", num)
			} else {
				closedNums = true
			}
		case msg, ok := <-msgs:
			if ok {
				fmt.Printf("%s\n", msg)
			} else {
				closedMsgs = true
			}
		}
	}
}
```

| msg | number |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 4 | 4 |
| no more msgs | no more numbers |

The select statement is blocking. The execution will be blocked until at least one of the declared communications are ready. This can be changed by adding a default case which is executed when none of the channels is ready. It can be used to avoid errors when channels are not ready. In Example 6.11, we use an unbuffered channel that is never going to be ready. Using the default case we can control this situation and run without panic. As an exercise, you can use a buffered channel to check the execution changes.

# Example 6.11: Non-blocking select using default cases.

```go
package main
import "fmt"

func main() {
	ch := make(chan int)
	// ch := make(chan int, 1)

	select {
	case i := <-ch:
		fmt.Println("Received", i)
	default:
		fmt.Println("Nothing received")
	}

	select {
	case ch <- 42:
		fmt.Println("Send 42")
	default:
		fmt.Println("Nothing sent")
	}

	select {
	case i := <-ch:
		fmt.Println("Received", i)
	default:
		fmt.Println("Nothing received")
	}
}
```

# 6.4 WAITGROUP

Normally, when working with goroutines we have to wait until their completion. In order to facilitate this, Go offers the WaitGroup type in the sync package. This type has three methods Add, Done, and Wait. A WaitGroup works like a counter with the number of goroutines we are waiting to be finished. Every time a goroutine finishes, the Done method decreases the counter. The Wait method blocks the execution until the counter reaches zero.

Example 6.12 defines an example of consumer/producer with a function generating tasks (random numbers) that are consumed by other goroutines. The WaitGroup variable is instantiated and increments to 3 elements wg.Add(3). Notifying wg about completion is up to the goroutines. For this, we pass the wg by reference so they can notify their completion. Note that this is done with wg.Done(). Finally, wg.Wait() waits until all the goroutines are finished.

# Example 6.12: WaitGroup and several goroutines.

```go
package main

import (
	"fmt"
	"math/rand"
	"sync"
	"time"
)

func generator(ch chan int, wg *sync.WaitGroup) {
	defer wg.Done()
	for i := 0; i < 5; i++ {
		time.Sleep(time.Millisecond * 200)
		ch <- rand.Intn(100)
	}
	close(ch)
	fmt.Println("Generator done")
}

func consumer(id int, sleep time.Duration, ch chan int, wg *sync.WaitGroup) {
	defer wg.Done()
	for task := range ch {
		time.Sleep(time.Millisecond * sleep)
		fmt.Printf("%d task[%d]\n", id, task)
	}
}

func main() {
	ch := make(chan int)
	var wg sync.WaitGroup

	wg.Add(3)
	go generator(ch, &wg)
	go consumer(1, 100, ch, &wg)
	go consumer(2, 200, ch, &wg)

	wg.Wait()
}
```

| task | count |
|---|---|
| task[34] | 2 |
| task[50] | 4 |
| task[61] | 1 |
| task[19] | 5 |
| Generator done | |
| task[40] | 1 |
| Consumer 1 done | |
