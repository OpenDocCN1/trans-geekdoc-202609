
# Go 语言通道与管道模式

第一个 goroutine `counter` 生成整数 0, 1, 2, ...，并通过通道发送给第二个 goroutine `squarer`。`squarer` 接收每个值，计算其平方，并通过另一个通道发送给第三个 goroutine `printer`。`printer` 接收平方值并打印它们。为了示例清晰，我们特意选择了非常简单的函数，尽管在实际程序中，它们的计算太简单，不值得单独开启 goroutine。

[Click here to view code image](#part0138_split_017.html#id228pro01_r)

gopl.io/ch8/pipeline1

```
func main() {
    naturals := make(chan int)
    squares := make(chan int)

    // Counter
    go func() {
        for x := 0; ; x++ {
            naturals <- x
        }
    }()

    // Squarer
    go func() {
        for {
            x := <-naturals
            squares <- x * x
        }
    }()

    // Printer (in main goroutine)
    for {
        fmt.Println(<-squares)
    }
}
```

正如预期，程序打印无限平方数列：0, 1, 4, 9 等。这种管道常见于长期运行的服务器程序中，通道用于包含无限循环的 goroutine 间的终身通信。但如果我们只想通过管道发送有限数量的值怎么办？

如果发送者知道某通道再不会发送值，将此事实告知接收 goroutine 很有用，这样它们就能停止等待。这通过内置函数 `close` 关闭通道来实现：

```
close(naturals)
```

通道关闭后，对其再执行发送操作将引发 panic。关闭的通道被*耗尽*后（即最后一个发送的元素被接收后），后续所有接收操作将不再阻塞，但会返回零值。关闭上述 `naturals` 通道会导致 `squarer` 的循环因接收源源不断的零值而空转，并将这些零值发送给 `printer`。

无法直接测试通道是否已关闭，但接收操作有一个变体可产生两个结果：接收到的通道元素，加一个布尔值（通常称为 `ok`），成功接收时为 `true`，在已关闭且耗尽的通道上接收时为 `false`。利用此特性，我们可以修改 `squarer` 的循环，使其在 `naturals` 通道耗尽时停止，并依次关闭 `squares` 通道。

[Click here to view code image](#part0138_split_018.html#id229pro01_r)

```
// Squarer
go func() {
    for {
        x, ok := <-naturals
        if !ok {
            break // channel was closed and drained
        }
        squares <- x * x
    }
    close(squares)
}()
```

由于上述语法笨拙且该模式常见，Go 语言允许用 `range` 循环遍历通道。这是接收通道上所有发送值并在最后一个值后终止循环的更便捷语法。

在下面的管道中，`counter` goroutine 发送 100 个元素后结束循环并关闭 `naturals` 通道，导致 `squarer` 结束循环并关闭 `squares` 通道。（在更复杂的程序中，`counter` 和 `squarer` 函数在开头用 `defer` 调用 `close` 可能更合理。）最后，主 goroutine 结束循环，程序退出。

[Click here to view code image](#part0138_split_019.html#id229pro02_r)

gopl.io/ch8/pipeline2

```
func main() {
    naturals := make(chan int)
    squares := make(chan int)

    // Counter
    go func() {
        for x := 0; x < 100; x++ {
            naturals <- x
        }
        close(naturals)
    }()

    // Squarer
    go func() {
        for x := range naturals {
            squares <- x * x
        }
        close(squares)
    }()

    // Printer (in main goroutine)
    for x := range squares {
        fmt.Println(x)
    }
}
```

并非每个通道用完都必须关闭。只有当需要告诉接收 goroutine 所有数据已发送完毕时，才需关闭通道。垃圾回收器判定不可达的通道，无论是否关闭，其资源都会被回收。（别混淆了文件的 `close` 操作。用完文件后调用 `Close` 方法*很重要*。）

尝试关闭已关闭的通道会引发 panic，关闭 `nil` 通道也会。关闭通道还可作为广播机制，详见 [8.9 节](#part0085.html#id-cancellation)。

## 8.4.3 单向通道类型

随着程序增长，将大函数拆分为小函数是自然的。前例用三个 goroutine、两个通道（均为 `main` 的局部变量）通信。程序自然分为三个函数：

```
func counter(out chan int)
func squarer(out, in chan int)
func printer(in chan int)
```

处于管道中间的 `squarer` 函数接受两个参数：输入通道和输出通道。两者类型相同，但预期用途相反：`in` 只用于接收，`out` 只用于发送。参数名 `in` 和 `out` 传达了此意图，但无法阻止 `squarer` 向 `in` 发送或从 `out` 接收。

这种安排很典型。通道作为函数参数时，几乎总是意图专门用于发送或专门用于接收。

为记录此意图并防止误用，Go 类型系统提供*单向*通道类型，仅暴露发送或接收操作之一。类型 `chan<- int` 是 `int` 的*只发送*通道，允许发送但不允许接收。反之，`<-chan int` 是 `int` 的*只接收*通道，允许接收但不允许发送。（`<-` 箭头相对 `chan` 关键字的位置是个助记符。）违反此规则会在编译时被检测。

因 `close` 操作断言通道不再有发送，只有发送 goroutine 有资格调用它，因此尝试关闭只接收通道会导致编译错误。

下面是再次用单向通道类型重写的平方管道：

[Click here to view code image](#part0138_split_020.html#id231pro01_r)

gopl.io/ch8/pipeline3

```
func counter(out chan<- int) {
    for x := 0; x < 100; x++ {
        out <- x
    }
    close(out)
}

func squarer(out chan<- int, in <-chan int) {
    for v := range in {
        out <- v * v
    }
    close(out)
}

func printer(in <-chan int) {
    for v := range in {
        fmt.Println(v)
    }
}

func main() {
    naturals := make(chan int)
    squares := make(chan int)

    go counter(naturals)
    go squarer(squares, naturals)
    printer(squares)
}
```

调用 `counter(naturals)` 隐式将 `naturals`（类型 `chan int`）转换为参数类型 `chan<- int`。`printer(squares)` 同样隐式转换为 `<-chan int`。从双向到单向通道类型的转换在任何赋值中均允许。但无法逆向：一旦拥有 `chan<- int` 等单向类型值，就无法从中获得指向同一通道数据结构的 `chan int` 类型值。

## 8.4.4 缓冲通道

缓冲通道拥有元素队列。队列最大长度由创建时 `make` 的容量参数决定。下面语句创建一个可容纳三个 `string` 值的缓冲通道。[图 8.2](#part0080.html#id-figures-emptychannel) 是 `ch` 及其引用通道的图形表示。

```
ch = make(chan string, 3)
```
