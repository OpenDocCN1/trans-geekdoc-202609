

```go
	fmt.Printf("Consumer %d done\n", id)
}

func main() {
	rand.Seed(42)

	ch := make(chan int, 10)
	var wg sync.WaitGroup

	wg.Add(3)

	go generator(ch, &wg)
	go consumer(1, 400, &wg)
	go consumer(2, 100, &wg)

	wg.Wait()
}
```

可以使用通道获得类似的行为。然而，在多个 goroutine 阻塞执行流且其终止可以由 goroutine 自身判断的情况下，这种方法是高度推荐的。

## 6.5 定时器、计时器（Ticker）和超时

在并发场景下，时间管理变得非常重要。在执行过程中，可能会发生具有不同周期或时间线的事件。为了让单次事件在未来发生，`time` 包提供了 `Timer` 类型。`Timer` 拥有一个通道 `c`，在给定时间后触发信号。同样，`ticker` 类型每隔一个给定周期为通道 `c` 触发一次信号。

示例 6.13：Timer 和 Ticker。

```go
package main
import (
	"fmt"
	"time"
)

func worker(x *int) {
	for {
		time.Sleep(time.Millisecond * 500)
		*x = *x + 1
	}
}

func main() {
	timer := time.NewTimer(time.Second * 5)
	ticker := time.NewTicker(time.Second)

	x := 0
	go worker(&x)

	for {
		select {
		case <-timer.C:
			fmt.Printf("timer -> %d\n", x)
		case <-ticker.C:
			fmt.Printf("ticker -> %d\n", x)
		}
		if x != 10 {
			break
		}
	}
}
```

| ticker -> 2 |
| ticker -> 3 |
| ticker -> 5 |
| ticker -> 7 |
| ticker -> 9 |
| ticker -> 11 |

示例 6.13 使用 Timer 和 Ticker 随时间检查 x 的值。worker 每 500 毫秒将 x 增加一。这里可以使用 `select` 语句在 timer 和 ticker 发送事件时做出反应。ticker 每秒唤醒一次 x 使其增加两次。注意 worker 在每次迭代中都会睡眠半秒。对于 timer，在五秒后会有单次操作。注意，worker 使用 Ticker 代替 `time.Sleep` 实现。

## 示例 6.14：Timer 和 Ticker 的管理。

```go
package main

import (
	"fmt"
	"time"
)

func reaction(t *time.Ticker) {
	for {
		select {
		case x := <-t.C:
			fmt.Println("quick", x)
		}
	}
}

func slowReaction(t *time.Timer) {
	select {
	case x := <-t.C:
		fmt.Println("slow", x)
	}
}

func main() {
	quick := time.NewTicker(time.Second)
	slow := time.NewTicker(time.Second * 5)
	stopper := time.NewTimer(time.Second * 4)
	go reaction(quick)
	go slowReaction(slow)

	<-stopper.C

	quick.Stop()

	stopped := slow.Stop()
	fmt.Println("Stopped before the event", stopped)
}
```

```
quick 2021-01-13 19:56:59.2428 +0100 CET m+=1.004374708
quick 2021-01-13 19:57:00.240984 +0100 CET m+=2.002541186
quick 2021-01-13 19:57:01.240728 +0100 CET m+=3.002627699
quick 2021-01-13 19:57:02.241683 +0100 CET m+=4.002028251
Stopped before the event true
```

可以使用 `Stop()` 和 `Reset()` 来管理 timers 和 tickers。调用 `Stop` 方法会关闭通道并终止新事件的触发。在 timer 的情况下，如果调用是在事件触发之前进行的，该方法返回 true。

在示例 6.14 中，我们定义了事件：使用每秒触发一次的 ticker 定义 quick，使用 5 秒后触发的 timer 定义 slow。第三个定时器设置为 4 秒。当到达停止定时器时，我们停止了 quick 和 slow。注意 `quick.Stop` 没有返回值。在 `slow.Stop` 的情况下，返回了 true 值，因为定时器没有被触发。

## 6.6 CONTEXT（上下文）

处理 API 和进程需要额外的逻辑，如取消、超时和截止日期。如果我们向 API 发送请求，我们将等待完成。之后，我们可以假设请求过期。Go 的 `context` 包提供了处理这些情况的构造。`Context` 接口定义了 Go 中通用上下文的元素：

```go
type Context interface {
	Deadline() (time.Time, bool)
	Done() <-chan struct{}
	Err() error
	Value(key interface{}) interface{}
}
```

`Deadline()` 方法返回 context 的截止日期，如果没有过期则返回 false。`Done()` 方法返回一个通道，当 context 操作完成时关闭。最后，`Value()` 存储属于 context 的键值对。可以使用空 context（`context.Background()`）或之前定义的 context 构建。Go 提供了四种 context 类型及其初始化函数：`WithCancel()`、`WithTimeout()`、`WithDeadline()` 和 `WithValue()`。

### 6.6.1 WithCancel

`context.WithCancel()` 返回一个 context 和一个 CancelFunc。这种类型强制强制 context 终止。在示例 6.15 中，setter 在多个 goroutine 中同时增加一个共享变量。`cancel` 函数通过检查 `Done()` 方法通知其终止。

## 示例 6.15：Context WithCancel

```go
package main

import (
	"context"
	"fmt"
	"sync/atomic"
	"time"
)

func setter(id int, c *int, ctx context.Context) {
	t := time.NewTicker(time.Millisecond * 300)
	for {
		select {
		case <-ctx.Done():
			fmt.Println("Done", id)
			return
		case <-t.C:
			atomic.AddInt32((*int32)(c), 1)
		}
	}
}

func main() {
	ctx, cancel := context.WithCancel(context.Background())

	var c int32 = 0
	for i := 0; i < 5; i++ {
		go setter(i, (*int)(&c), ctx)
	}

	time.Sleep(time.Second * 1)
	fmt.Println("Final check: ", c)
	cancel()
}
```

| Final check: 15 |
| Done 1 |
| Done 3 |
| Done 2 |
| Done 4 |

通常，`cancel` 函数使用 `defer` 执行以确保 context 终止。如果在循环中声明了多个 context，如下文所示：

```go
for {
    ctx, cancel = context.WithCancel(context.Background())
    // defer cancel() -> 当函数返回时释放

    cancel()
}
```

### 6.6.2 WithTimeout

超时是避免长时间分配资源的常用方法。`context.WithTimeout` 函数接收一个 `Duration` 参数，设置等待 context 完成的时间。示例 6.16 执行了一个运行较长的 goroutine。`select` 语句阻塞执行直到收到新数字或 context 完成。注意在 context 到超时的情况下，`Err()` 方法会被填充相应的消息。

## 示例 6.16：Context Timeout

```go
package main

import (
	"context"
	"time"
)

func work(i int, info chan int) {
	t := time.Duration(i*100) * time.Millisecond
	time.Sleep(t)
	info <- i
}

func main() {
	d := time.Millisecond * 300
	ch := make(chan int)
	i := 0
	for {
		ctx, cancel := context.WithTimeout(context.Background(), d)
		work(i, ch)
		select {
		case x := <-ch:
			fmt.Println("Received", x)
		case <-ctx.Done():
			fmt.Println("Done!")
		}
		if ctx.Err() != nil {
			fmt.Println(ctx.Err())
			return
		}
		cancel()
		i++
	}
}
```

| Received 0 |
| Received 1 |
| Received 2 |
| Received 3 |
| Done! |
| context deadline exceeded |

> 在循环内部处理 context 时，不应该对 cancel 函数使用 defer。请记住 `defer` 在函数返回时执行，因此在此之前分配的所有资源都不会释放。

### 6.6.3 WithDeadline

与超时类似，这种 context 设置了绝对终止时间。当到达截止日期时，context 完成。6.17 使用各种 goroutine 修改共享变量。context 设置在三秒后过期。注意这与使用超时的 context 类似。我们阻塞执行直到 context 完成（`ctx.Done()`）。从输出中我们可以观察到 goroutine 如何被通知 context 的终止。并不是消息都打印了，因为程序在 goroutine 有时间打印消息之前就终止了。

## 示例 6.17：Context WithDeadline。

```go
package main

import (
	"context"
	"fmt"
	"sync/atomic"
	"time"
)

func accum(c *uint32, ctx context.Context) {
	t := time.NewTicker(time.Millisecond * 250)
	for {
		select {
			case <-t.C:
				atomic.AddUint32(c, 1)
			case <-ctx.Done():
				fmt.Println("Done context")
				return
		}
	}
}

func main() {
	d := time.Now().Add(time.Second * 3)
	ctx, cancel := context.WithDeadline(context.Background(), d)
	defer cancel()

	var counter uint32 = 0

	for i := 0; i < 5; i++ {
		go accum(&counter, ctx)
	}
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_85_0.png)

