

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

# 6.2.3 使用 range 消费数据

通常，我们无法预先知道将通过通道发送多少值。我们可以使用 `range` 来阻塞执行并等待值，直到通道关闭。查看 `main` 函数中的示例 6.7 如何从通道中消费数据，直到该通道关闭，这与生成值的数量无关。

> 示例 6.7：使用 range 进行通道消费。

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

# 6.2.4 通道的方向

通道中的数据流方向是可以指定的。

```go
ch := make(chan int) // 发送和接收
ch := make(<-chan int) // 接收
ch := make(chan<- int) // 发送
```

这提供了更好的类型安全并允许更好地利用通道。在示例 6.8 中，我们定义了发送者和接收者函数分别发送和接收值。由于设置了通道方向，如果接收者尝试使用通道发送数据，将在编译时出现错误。同样地，发送者无法从通道读取数据。

# 示例 6.8：通道方向。

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

`select` 语句与 `switch` 语句有些相似。它从一组发送/接收操作中阻塞执行，直到其中一个操作就绪。示例 6.9 执行了两个不同的 goroutine，通过两个不同的通道发送值。查看 `select` 语句如何在单次操作中接收操作。在 `select` 内部，`case` 按照它们定义的顺序进行评估。如果有两个或多个 `case` 就绪，则通过伪随机选择选择下一个。`select` 语句仅执行单次操作，或者为了继续等待更多消息，必须像循环一样迭代执行。

**示例 6.9：** select。

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

select 多值接收 (x, ok := ch)。此功能可以用于判断通道是否已准备好接收。示例 6.10 扩展了上一个示例，当两个通道都关闭时停止接收数据。记住在多值接收中，通道关闭时第二个值会变为 `false`。与上一个示例相比，我们不需要预先知道要接收的消息数量。我们可以直到

# 示例 6.10：带多值的 select。

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

`select` 语句是阻塞的。执行将阻塞，直到至少有一个声明的通信操作就绪。这可以通过添加 `default` case 来改变，当所有通道都未就绪时将执行 `default`。它可以用于在通道未就绪时避免错误。在示例 6.11 中，我们使用了一个永远不会就绪的无缓冲通道。使用 `default` case 我们可以控制这种情况并运行而不会发生 panic（崩溃）。作为一个练习，你可以使用缓冲通道来检查执行的变化。

# 示例 6.11：使用 default case 的非阻塞 select。

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
}
```

# 6.4 WAITGROUP

通常，当与 goroutine 工作时，我们需要等待它们完成。为了方便这一点，Go 提供了 `sync` 包中的 `WaitGroup` 类型。该类型有三个方法：`Add`, `Done` 和 `Wait`。`WaitGroup` 工作原理类似于计数等待完成的 goroutine 数量。每当一个 goroutine 完成，`Done` 方法减少计数器。`Wait` 方法阻塞执行直到计数器归零。

示例 6.12 定义了一个生产者/消费者示例，任务（随机数）由其他 goroutine 消费。`WaitGroup` 变量被实例化并增加 3 个元素 `Add(3)`。通知 wg 完成由 goroutine 执行。为此，我们通过引用传递 wg以便它们通知完成。注意这是通过 `Done()` 实现的。最后，`Wait()` 等待所有 goroutine 完成。

# 示例 6.12：WaitGroup 和多个 goroutine。

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

