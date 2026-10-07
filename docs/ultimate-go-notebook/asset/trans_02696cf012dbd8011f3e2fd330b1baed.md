
以提供一个合理的性能基准测试数值。

该循环创建了子 Goroutine 池，每个子 Goroutine 都会通过通道的 `range` 机制处于阻塞接收调用中。

# 列表 6.37

```go
for c := 0; c < g; c++ {
    go func(child int) {
        for d := range ch {
            fmt.Printf("child %d : recv'd signal: %s\n", child, d)
        }
        fmt.Printf("child %d : recv'd shutdown signal\n", child)
    }
}(c)
```

`for range` 有帮助减少我原本为了接收信号并在关闭后关闭通道而需要编写的代码量。如果没有 `for/range` 机制，我必须编写下面的代码。

# 列表 6.38

```go
for c := 0; c < g; c++ {
    go func(child int) {
        for {
            d, ok := <-ch      <-- 修改处
            if !ok            <-- 修改处
                break          <-- 修改处
        }
        fmt.Printf("child %d : recv'd signal: %s\n", child, d)
        fmt.Printf("child %d : recv'd shutdown signal\n", child)
    } 
}(c)
```

`for/range` 删除了 4 行额外代码并简化了机制。需要注意的是，池中哪一个子 Goroutine 被选中接收信号并不重要。取决于被发送信号的工作量，可能是同一个子 Goroutine 反复一次地被选中，而其他 Goroutine 则可能永远不会被选中。

然后执行对 `close` 调用，这将导致循环终止并停止程序。如果使用的通道是缓冲通道，数据在子 Goroutine 接收到关闭信号之前会从缓冲区中溢出。

## 6.11.5 丢弃 (Drop)

丢弃模式对于有时会经历重负载负载的服务来说是一个重要模式，当服务达到待处理请求的容量限制时，它可以丢弃请求。例如，DNS 服务就需要采用这种模式。

```go
// 列表 6.39
func drop() {
  const cap = 100
  ch := make(chan string, cap)

  go func() {
    for p := range ch {
      fmt.Println("child : recv'd signal :", p)
    }
  }()
  const work = 2000
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

代码从创建缓冲通道开始。在这种情况下，拥有大缓冲区是合理的。确定容量值（缓冲区大小）需要在实验中完成。我希望这个数值能让服务在缓冲区满时仍保持合理的资源使用水平和性能。

接下来，创建了一个使用池化模式的子 Goroutine。这个子 Goroutine 正在等待信号以接收工作。在这个示例中，只有一个子 Goroutine 将导致发送端迅速产生背压。缓冲区缓冲区之前无法及时处理所有工作，这代表服务已满容量。

在 `for` 循环内部，我使用了 `select` 语句。`select` 语句是一个阻塞调用，允许父 Goroutine 同时处理多个通道操作。每个 `case` 代表一次通道操作，即发送或接收。然而，这个 `select` 也使用了 `default` 关键字，这使得 `select` 变成了一个非阻塞调用。

实现此模式的关键是使用 `default`。如果通道缓冲区满了，将导致 `case` 语句阻塞，因为发送无法完成。当 `select` 中的所有 `case` 都被阻塞且存在 `default` 时，就会执行 `default`。这就是放置丢弃代码的地方。

在丢弃代码中，我现在可以决定对请求进行什么操作。我可以向调用者返回 500 错误。我也可以将请求存储在其他地方。关键是我有多种选择。

## 6.11.6 取消 (Cancellation)

取消模式用于告知执行某些 I/O 操作的函数我愿意等待该操作多长时间。有时我可以取消该操作，有时我可以直接离开。

```go
// 列表 6.40
func cancellation() {
    duration := 150 * time.Millisecond
    ctx, cancel := context.WithTimeout(context.Background(), duration)
    defer cancel()

    ch := make(chan string, 1)

    go func() {
        // ... (逻辑省略)
    }()
}
```

取消模式用于告知执行某些 I/O 操作的函数我愿意等待该操作多长时间。有时我可以取消该操作，有时我可以直接离开。

取消模式通过 `context.WithTimeout` 创建一个带有超时的上下文。`defer cancel()` 确保资源被释放。当子 Goroutine 接收到 `ctx.Done()` 信号时，操作停止。

## 6.11.7 扇出扇入 (Fan Out/In)

Fan Out/In 模式通过信号量来控制 Goroutine 的并发数量。

```go
// 列表 6.41
func fanOutSem() {
	children := 2000
	ch := make(chan string)
	g := runtime.GAXPROCS(0)
	sem := make(chan bool, g)

	for c := 0; c < g; c++ {
		go func(child int) {
			// ... (处理逻辑)
			sem <- true
		}(c)
	}

	for children > 0 {
		<-ch
		children--
	}
}
```
