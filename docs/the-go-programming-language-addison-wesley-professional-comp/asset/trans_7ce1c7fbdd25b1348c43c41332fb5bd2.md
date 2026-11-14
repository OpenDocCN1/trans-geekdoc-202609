

# RWMutex：多读单写锁

由于 `Balance` 函数只需要*读取*变量的状态，实际上多个 `Balance` 调用并发运行是安全的，只要没有 `Deposit` 或 `Withdraw` 调用正在运行。在这种情况下，我们需要一种特殊的锁，允许只读操作彼此并行进行，但写操作拥有完全独占的访问权。这种锁称为*多读单写*锁，在 Go 语言中由 `sync.RWMutex` 提供：

```
var mu sync.RWMutex
var balance int

func Balance() int {
    mu.RLock() // 读锁
    defer mu.RUnlock()
    return balance
}
```

`Balance` 函数现在调用 `RLock` 和 `RUnlock` 方法来获取和释放*读锁*或*共享锁`。`Deposit` 函数保持不变，它调用 `mu.Lock` 和 `mu.Unlock` 方法来获取和释放*写锁*或*独占锁*。

做出此更改后，Bob 的大多数 `Balance` 请求彼此并行运行，完成得更快。锁可用的时间更多，`Deposit` 请求能及时进行处理。

只有在临界区没有对共享变量进行写入时，才能使用 `RLock`。通常，我们不应假设*逻辑上*只读的函数或方法不也会更新某些变量。例如，一个看似简单的访问器方法可能也会增加内部使用计数器，或更新缓存以使重复调用更快。如果拿不准，请使用独占的 `Lock`。

只有当获取锁的大多数 goroutine 是读者，且锁处于*竞争*状态时（即 goroutine 经常不得不等待以获取锁），使用 `RWMutex` 才有利。`RWMutex` 需要更复杂的内部记账，使其在无竞争锁的情况下比普通互斥锁更慢。

## 9.4 内存同步

你可能会想知道为什么 `Balance` 方法需要互斥锁，无论是基于通道的还是基于互斥锁的。毕竟，与 `Deposit` 不同，它仅包含单个操作，因此没有其他 goroutine 在它“中间”执行的危险。我们需要互斥锁有两个原因。第一个原因是，`Balance` 不在像 `Withdraw` 这样的其他操作中间执行，这一点同样重要。第二个（更微妙的）原因是，同步不仅关乎多个 goroutine 执行顺序；同步还影响内存。

在现代计算机中，可能有数十个处理器，每个处理器都有自己的主内存本地缓存。为了效率，对内存的写入会在每个处理器内部缓冲，仅在必要时才刷新到主内存。它们甚至可能以不同于写入 goroutine 编写的顺序提交到主内存。像通道通信和互斥锁操作这样的同步原语会导致处理器刷新并提交所有累积的写入，从而保证截至该点 goroutine 执行的效果对运行在其他处理器上的 goroutine 可见。

考虑以下代码片段的可能输出：

```
var x, y int
go func() {
    x = 1                   // A1
    fmt.Print("y:", y, " ") // A2
}()
go func() {
    y = 1                   // B1
    fmt.Print("x:", x, " ") // B2
}()
```

由于这两个 goroutine 是并发的，且在没有互斥的情况下访问共享变量，因此存在数据竞争，所以我们不应惊讶于程序是不确定的。我们可能期望它打印以下四种结果中的任意一种，它们对应于程序标记语句的直观交织：

```
y:0 x:1
x:0 y:1
x:1 y:1
y:1 x:1
```

例如，第四行可以用序列 `A1,B1,A2,B2` 或 `B1,A1,A2,B2` 来解释。然而，这两种结果可能会让人感到意外：

```
x:0 y:0
y:0 x:0
```

但根据编译器、CPU 和许多其他因素，它们也可能发生。这四条语句的哪种可能交织能解释它们？

在单个 goroutine 内部，每条语句的效果保证按执行顺序发生；goroutine 是*顺序一致的*。但在没有使用通道或互斥锁进行显式同步的情况下，无法保证所有 goroutine 以相同顺序看到事件。虽然 goroutine *A* 必须在读取 `y` 的值之前观察到写入 `x = 1` 的效果，但它不一定观察到 goroutine *B* 对 `y` 的写入，因此 *A* 可能会打印 `y` 的*陈旧*值。

人们很容易试图理解并发，就好像它对应于每个 goroutine 语句的*某些*交织，但正如上面的例子所示，现代编译器或 CPU 并非这样工作。因为赋值和 `Print` 引用不同的变量，编译器可能得出结论：这两条语句的顺序不会影响结果，从而交换它们。如果两个 goroutine 在不同的 CPU 上执行，每个 CPU 都有自己的缓存，那么一个 goroutine 的写入在缓存与主内存同步之前，对另一个 goroutine 的 `Print` 是不可见的。

所有这些并发问题都可以通过一致地使用简单、成熟的模式来避免。如果可能，将变量限制在单个 goroutine 中；对于所有其他变量，使用互斥锁。

## 9.5 惰性初始化：`sync.Once`

将昂贵的初始化步骤推迟到需要时刻是一种好习惯。提前初始化变量会增加程序的启动延迟，而且如果执行过程不总是到达使用该变量的程序部分，则是不必要的。让我们回到本章前面看到的 `icons` 变量：

```
var icons map[string]image.Image
```

这个版本的 `Icon` 使用了*惰性初始化*：

```
func loadIcons() {
    icons = map[string]image.Image{
        "spades.png":   loadIcon("spades.png"),
        "hearts.png":   loadIcon("hearts.png"),
        "diamonds.png": loadIcon("diamonds.png"),
        "clubs.png":    loadIcon("clubs.png"),
    }
}

// 注意：非并发安全！
func Icon(name string) image.Image {
    if icons == nil {
        loadIcons() // 一次性初始化
    }
    return icons[name]
}
```

对于仅由单个 goroutine 访问的变量，我们可以使用上述模式，但如果 `Icon` 被并发调用，此模式是不安全的。就像银行最初的 `Deposit` 函数一样，`Icon` 包含多个步骤：它测试 `icons` 是否为 nil，然后加载图标，然后将 `icons` 更新为非 nil 值。直觉可能会认为，上述竞争条件最坏的结果是 `loadIcons` 函数被调用多次。当第一个 goroutine 正忙于加载图标时，另一个进入 `Icon` 的 goroutine 会发现变量仍等于 `nil`，并也会调用 `loadIcons`。

但这种直觉也是错的。（希望到现在你已建立起关于并发的新直觉，即不应信任关于并发的直觉！）回顾 [9.4 节](#part0091.html#id-memorysynchronization) 对内存的讨论。在没有显式同步的情况下，编译器和 CPU 可以以任意方式重排内存访问，只要每个 goroutine 的行为保持顺序一致。下面展示了 `loadIcons` 语句的一种可能重排。它在填充 map 之前，将空 map 存储在 `icons` 变量中：

