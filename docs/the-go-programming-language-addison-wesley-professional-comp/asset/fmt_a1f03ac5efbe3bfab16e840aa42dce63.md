
# 9.1 Data Races

最终语句中 `x` 的值未定义；它可能是 `nil`，或长度为 10 的切片，或长度为 1,000,000 的切片。但请回忆，切片有三个部分：指针、长度和容量。如果指针来自第一次 `make` 调用，而长度来自第二次，`x` 将是一个嵌合体——一个名义长度为 1,000,000 但底层数组只有 10 个元素的切片。在这种情况下，向元素 999,999 存储数据会破坏任意遥远的内存位置，后果无法预测，也难以调试和定位。这种语义雷区称为**未定义行为**（*undefined behavior*），C 程序员对此深有体会；幸运的是，在 Go 中它很少像在 C 中那样麻烦。

即使“并发程序是多个顺序程序的交织”这一概念也是错误的直觉。正如我们将在 [9.4 节](#part0091.html#id-memorysynchronization) 看到的，数据竞争可能产生更奇怪的结果。许多程序员——甚至一些非常聪明的程序员——偶尔会为其程序中已知的数据竞争辩护：“互斥的成本太高”、“这只是用于日志记录”、“我不介意丢失一些消息”，等等。在特定编译器和平台上没有出现问题可能会给他们虚假的信心。一个好的经验法则是：**不存在良性的数据竞争**。那么我们如何避免程序中的数据竞争？

我们重复一下定义，因为它非常重要：**当两个 goroutine 并发访问同一变量，且至少有一个访问是写入时，就会发生数据竞争**。根据这个定义，避免数据竞争有三种方法。

## 第一种方法：不写入变量

考虑下面的 map，它在每个键首次被请求时惰性填充。如果 `Icon` 顺序调用，程序运行正常；但如果 `Icon` 并发调用，访问 map 就会发生数据竞争。

[点击查看代码图像](#part0139_split_005.html#id260pro01_r)

```
var icons = make(map[string]image.Image)

func loadIcon(name string) image.Image

// NOTE: not concurrency-safe!
func Icon(name string) image.Image {
    icon, ok := icons[name]
    if !ok {
        icon = loadIcon(name)
        icons[name] = icon
    }
    return icon
}
```

如果我们在创建额外 goroutine 之前用所有必要条目初始化 map，且之后不再修改它，那么任意数量的 goroutine 可以安全地并发调用 `Icon`，因为每个 goroutine 只读取 map。

[点击查看代码图像](#part0139_split_006.html#id260pro02_r)

```
var icons = map[string]image.Image{
    "spades.png":   loadIcon("spades.png"),
    "hearts.png":   loadIcon("hearts.png"),
    "diamonds.png": loadIcon("diamonds.png"),
    "clubs.png":    loadIcon("clubs.png"),
}

// Concurrency-safe.
func Icon(name string) image.Image { return icons[name] }
```

在上面的示例中，`icons` 变量在包初始化期间赋值，这发生在程序的 `main` 函数开始运行**之前**（*happens before*）。一旦初始化，`icons` 就不再修改。从不修改或不可变的数据结构天生是并发安全的，无需同步。但显然，如果更新是必要的（如银行账户），我们就不能使用这种方法。

## 第二种方法：避免从多个 goroutine 访问变量

这是上一章许多程序采用的方法。例如，并发网络爬虫（[§8.6](#part0082.html#id-exampleconcurrentwebcrawler)）中的主 goroutine 是唯一访问 `seen` map 的 goroutine，聊天服务器（[§8.10](#part0086.html#id-examplechatserver)）中的 `broadcaster` goroutine 是唯一访问 `clients` map 的 goroutine。这些变量被**限制**（*confined*）在单个 goroutine 中。

由于其他 goroutine 无法直接访问该变量，它们必须通过通道向限制该变量的 goroutine 发送请求来查询或更新变量。这正是 Go 格言“不要通过共享内存来通信；而要通过通信来共享内存”的含义。一个使用通道请求来代理对受限变量访问的 goroutine 被称为该变量的**监控 goroutine**（*monitor goroutine*）。例如，`broadcaster` goroutine 监控对 `clients` map 的访问。

下面是用监控 goroutine `teller` 限制 `balance` 变量的银行示例重写：

[点击查看代码图像](#part0139_split_007.html#id261pro01_r)

`gopl.io/ch9/bank1`

```
// Package bank provides a concurrency-safe bank with one account.
package bank

var deposits = make(chan int) // send amount to deposit
var balances = make(chan int) // receive balance

func Deposit(amount int) { deposits <- amount }
func Balance() int       { return <-balances }

func teller() {
    var balance int // balance is confined to teller goroutine
    for {
        select {
        case amount := <-deposits:
            balance += amount
        case balances <- balance:
        }
    }
}

func init() {
    go teller() // start the monitor goroutine
}
```

即使变量在其整个生命周期内无法限制在单个 goroutine 中，限制仍可能是解决并发访问问题的方案。例如，在管道中通过通道将变量地址从一个阶段传递到下一个阶段，在 goroutine 间共享变量是常见的。如果管道的每个阶段在发送变量给下一阶段后不再访问它，那么对该变量的所有访问就是顺序的。实际上，变量先被限制在管道的一个阶段，然后是下一个阶段，依此类推。这种规律有时称为**串行限制**（*serial confinement*）。

在下面的示例中，`Cake` 先被串行限制在 `baker` goroutine，然后是 `icer` goroutine：

[点击查看代码图像](#part0139_split_008.html#id262pro01_r)

```
type Cake struct{ state string }

func baker(cooked chan<- *Cake) {
    for {
        cake := new(Cake)
        cake.state = "cooked"
        cooked <- cake // baker never touches this cake again
    }
}

func icer(iced chan<- *Cake, cooked <-chan *Cake) {
    for cake := range cooked {
        cake.state = "iced"
        iced <- cake // icer never touches this cake again
    }
}
```

## 第三种方法：允许多个 goroutine 访问变量，但同一时间只能有一个

这种方法称为**互斥**（*mutual exclusion*），是下一节的主题。

**练习 9.1：** 向 `gopl.io/ch9/bank1` 程序添加函数 `Withdraw(amount int) bool`。结果应指示事务是成功还是因资金不足而失败。发送给监控 goroutine 的消息必须包含要取款的金额和一个新通道，监控 goroutine 可通过该通道将布尔结果发回给 `Withdraw`。

# 9.2 互斥：`sync.Mutex`

在 [8.6 节](#part0082.html#id-exampleconcurrentwebcrawler) 中，我们使用带缓冲的通道作为**计数信号量**（*counting semaphore*），确保不超过 20 个 goroutine 同时发起 HTTP 请求。用同样的思路，我们可以使用容量为 1 的通道，确保同一时间最多只有一个 goroutine 访问共享变量。只能计数到 1 的信号量称为**二元信号量**（*binary semaphore*）。

[点击查看代码图像](#part0139_split_009.html#id262pro02_r)

`gopl.io/ch9/bank2`

```
var (
    sema    = make(chan struct{}, 1) // a binary semaphore guarding balance
    balance int
)

func Deposit(amount int) {
    sema <- struct{}{} // acquire token
    balance = balance + amount
    <-sema // release token
}

func Balance() int {
    sema <- struct{}{} // acquire token
    b := balance
    <-sema // release token
    return b
}
```
