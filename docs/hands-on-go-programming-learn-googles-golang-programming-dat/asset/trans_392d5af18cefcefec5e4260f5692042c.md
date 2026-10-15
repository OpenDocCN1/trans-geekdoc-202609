
我们在 main 函数中定义了一个 int 类型的通道。我们调用 writeVal 函数作为 goroutine，并将通道变量传递给它。在 main 函数中，我们从通道中读取值，将其赋给变量并打印该值。请注意，main 函数中的读取操作将一直阻塞，直到 writeVal 函数向通道中写入数据。因此，main 函数将等待通道上有可用的值。

由于上述代码中的读写操作都是阻塞调用，如果 main 函数正在等待从通道读取，却不存在任何 goroutine，Go 运行时会将其判定为死锁，程序将发生 panic。这可以在程序 11.8 中看到。

**程序 11.8**

```go
package main

import (
"fmt"
)

func main() {

ch := make(chan int, 0)
a := <-ch
fmt.Println(a)
}
```

上述程序的输出如下：

```text
fatal error: all goroutines are asleep - deadlock!

goroutine 1 [chan receive]:
main.main()
		/Users/prithvipalsingh/PRITHVI/Github/src/go-practice/main.go:9 +0x5b
exit status 2
```

**图 11.1**

**注意：理解通道中的读取和发送操作是原子性的，这一点非常重要。**

## 11.3.2 通道上的操作

我们可以对通道执行操作。我们可以关闭通道，也可以遍历通道。这些操作在通道中非常常用。

```
}
```

上述程序将产生如下错误：

```text
panic: send on closed channel

goroutine 19 [running]:
main.writeVal(0xc000094060, 0xc000098000)
/Users/prithvipalsingh/go/src/workspace/main.go:17 +0x37
created by main.main

/Users/prithvipalsingh/go/src/workspace/main.go:12 +0xa5
exit status 2
```

在程序 11.9 中，我们在创建通道之后将其关闭。我们将已关闭的通道传递给了 writeVal() 函数。当 writeVal 函数中执行发送操作时，程序会发生 panic，因为不允许对已关闭的通道执行发送/写入操作。我们在 main 函数中使用 WaitGroup 进行等待，因此在 writeVal goroutine 有机会启动之前，main 函数不会结束。

可以对已关闭的通道执行读取操作。当我们对已关闭的通道执行读取操作时，它总是返回零值。零值可能是通道中的有效值。我们可以区分从通道返回的零值究竟是通道中实际存在的零值，还是因为通道已关闭而导致的返回值。通道会返回两个值：第一个是值，第二个是检查通道是否已关闭的标志。当通道关闭时，我们会收到第二个值为 false：

**程序 11.10**

```go
package main

import (
"fmt"
)

func main() {
ch := make(chan int)
close(ch)
val, ok := <-ch
if !ok {

fmt.Printf("Value %v is returned. the channel is closed\n", val)
}
}
```

上述程序的输出如下：

**返回了值 0。通道已关闭**

### 11.3.2.2 遍历通道

我们可以在读取通道时遍历通道。遍历通道读取数据有两种方式。一种方式是使用通道返回的第二个值。我们可以使用无限循环进行遍历，并在第二个值为 false 时跳出循环。另一种方式是使用 range 子句。

程序 11.11 演示了第一种方式：

**程序 11.11**

```go
package main

import "fmt"

func main() {

ch := make(chan int)
go func() {
for i := 0; i < 10; i++ {
ch <- i
}
close(ch)
}()

for {
val, ok := <-ch
if !ok {
    break
}
fmt.Println(val)
}
}
```

上述程序的输出如下：

```text
0
1
2
3
4
5
6
7
8
9
```

*程序 11.11* 可以重构，读取代码可以精简为：

**程序 11.12**

```go
package main

import "fmt"

func main() {

ch := make(chan int)

go func() {
for i := 0; i < 10; i++ {
ch <- i
}
close(ch)
}()

for val, ok := <-ch; ok; val, ok = <-ch {
fmt.Println(val)
}
}
```

上述程序的输出如下：

```text
0
1
2
3
4
5
6
7
8
9
```

我们对 for 循环进行了重构。我们在 for 循环的初始化部分读取了值和 ok。在条件部分检查 ok 变量的值，并在后置条件中再次读取值和 ok。

第二种方式是使用 range 子句。这是最好的方式，因为我们不需要条件，当通道被关闭且通道中的所有值都已被读取时，range 子句会自动结束：

**程序 11.13**

```go
package main

import "fmt"

func main() {

ch := make(chan int)

go func() {
for i := 0; i < 10; i++ {
ch <- i
}
close(ch)
}()

for val := range ch {
fmt.Println(val)

}
}
```

上述程序的输出如下：

```text
0
1
2
3
4
5
6
7
8
9
```

## 11.3.3 通道的类型

通道有两种类型：无缓冲通道和有缓冲通道。当我们声明一个通道时如果没有指定容量，它将被声明为无缓冲通道。当我们声明一个通道时如果指定了容量，它将被声明为有缓冲通道。

### 11.3.3.1 无缓冲通道

当通道中没有容量时，该通道被称为无缓冲通道。在无缓冲通道中，发送操作将会被阻塞，直到某个 goroutine 执行读取。读取操作也是如此。读取操作会一直阻塞，直到某个 goroutine 向其中发送数据。

让我们编写一个生产者-消费者程序，看看读取操作只会在某个 goroutine 向通道写入值时才会执行。

**程序 11.14**

```go
package main

import (
"fmt"
)

func main() {

ch := make(chan int)
done := make(chan bool)
go producer(ch, done)
go consumer(ch)
<-done
}
```

上述程序的输出如下：

```text
PRODUCER: sending 6
PRODUCER: sending 7
CONSUMER: read 6
CONSUMER: read 7
PRODUCER: sending 8
PRODUCER: sending 9
CONSUMER: read 8
CONSUMER: read 9
```

请注意 *程序 11.14* 的输出。生产者会一直等待，直到消费者从通道中读取一个值，反之亦然。我们会看到发送和读取分别连续出现两次，因为当消费者读取后打印时，生产者已经打印了发送消息，尽管它还没有发送。同样的情况也发生在：生产者已经发送了一个值，打印了第二个值，并在发送第二个值前阻塞；当消费者第一次读取并打印时，生产者已经打印了下一个值。因此，生产者发送第二个值，然后消费者读取并打印。这就是为什么我们会看到生产者和消费者各打印两次。

### 11.3.3.2 有缓冲通道

有缓冲通道是那些在创建时指定了容量的通道。例如：

```go
ch := make(chan int, 5)
```

在有缓冲通道中，当通道的容量/缓冲区已满时，写入操作会被阻塞。在上述语句中，当通道中已经有五个值，而我们尝试发送第 6 个值时，操作会被阻塞，因为没有可用空间。

当通道为空时，读取操作会被阻塞。

让我们再次使用有缓冲通道编写生产者-消费者问题：

**程序 11.15**

```go
package main

import (
    "fmt"
)

func main() {

ch := make(chan int, 5)
done := make(chan bool)
go producer(ch, done)
go consumer(ch)
<-done
}

func producer(ch chan int, done chan bool) {
for index := 0; index < 10; index++ {
fmt.Printf("PRODUCER: sending %v\n", index)
ch <- index
}

close(ch)
done <- true
}

func consumer(ch chan int) {
for val := range ch {
fmt.Printf("CONSUMER: read %v\n", val)
}
}
```

上述程序的输出如下：

```text
PRODUCER: sending 0
PRODUCER: sending 1
PRODUCER: sending 2
PRODUCER: sending 3
```
