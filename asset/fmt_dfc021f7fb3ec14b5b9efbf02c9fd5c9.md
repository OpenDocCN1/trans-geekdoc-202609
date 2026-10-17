
`var d bool    bool [false]`

```
字符串使用 UTF8 字符集，但它们实际上只是字节的集合。
```

字符串在 Go 中是一个两个字的内部数据结构：

- 第一个字代表指向底层字节数组的指针
- 第二个字代表底层数组的长度或字节数
- 如果字符串被设置为其零值状态，则第一个字为 `nil`，第二个字为 `0`。

使用短变量声明操作符，我可以同时完成值的声明、构造和初始化。

```go
aa := 10          // int [10]

bb := "hello"     // string [hello]

cc := 3.14159     // float64 [3.14159]

dd := true         // bool [true]
```

```go
fmt.Printf("aa := %v %T %+v\n", aa, aa)

fmt.Printf("bb := %v %T %+v\n", bb, bb)

fmt.Printf("cc := %v %T %+v\n", cc, cc)

fmt.Printf("dd := %v %T %+v\n", dd, dd)
```

```go
Output:

aa := 10          int [10]

bb := "hello"     string [hello]

cc := 3.14159     float64 [3.14159]

dd := true         bool [true]
```

### 2.5 强制类型转换（Conversion with Casting）

Go 没有强制类型转换（casting），只有转换（conversion）。与其告诉编译器将一组字节集映射到不同的表示形式，不如将这些字节复制到新的内存位置以形成新的表示形式。

#### 列表 2.4

```go
aaa := int32(10)

fmt.Printf("aaa := int32(10) %T %+v\n", aaa, aaa)
```

```go
Output:

aaa := int32(10) int32 [10]
```

如果我需要执行实际的强制转换操作，Go 在标准库中有一个名为 `unsafe` 的包。我真的会尽量避免这样做，并诚实地反思自己为什么要考虑使用它。执行转换为此类操作提供了最高水平的完整性。

### 2.6 结构体与构造机制

此声明将一个具体的自定义类型表示为不同字段和类型的复合体。

#### 列表 2.5

```go
type example struct {
    flag    bool
    counter int16
    p       float32
}
```

声明一个 `example` 类型的变量并将其初始化为零值。

#### 列表 2.6

```go
var el example

fmt.Printf("%+v\n", el)
```

Output:

`{flag:false counter:0 p:0}`

使用字面量语法将变量设置为零值。

#### 列表 2.7

```go
e2 := struct {
    flag    bool
    counter int16
    p       float32
}{
  flag: true,
  counter: 10,
  p: 3.14159,
}

fmt.Println("Flag", e2.flag)
fmt.Println("Counter", e2.counter)
fmt.Println("Pi", e2.p)
```

Output:
Flag true
Counter 10
Pi 3.14159

使用字面量语法声明一个非零值的变量。这是其中一个。

#### 列表 2.8

```go
e3 := struct {
    flag    bool
    counter int16
    p       float32
}{
  flag: true,
  counter: 10,
  p: 3.14159,
}
fmt.Println("Flag", e3.flag)
fmt.Println("Counter", e3.counter)
fmt.Println("Pi", e3.p)
```

Output:

Flag true

Counter 10

Pi 3.14159

字面量构造只是为了构造某些东西而不是零值状态。因为这样，我应该使用 `var` 用于零值构造。

### 2.7 填充与对齐（Padding and Alignment）

为 `example` 类型的值分配了多少内存？

#### 列表 2.9

```go
type example struct {
    flag    bool
    counter int16
    p       float32
}
```

`bool` 是 1 字节，`int16` 是 2 字节，`float32` 是 4 字节。将它们加起来得到 7 字节。然而，由于对齐的原因，实际答案是 8 字节，在 `flag` 和 `counter` 字段之间存在填充。

#### 图 2.1

| Flag | Counter | Pi |
|---|---|---|
| 0 | 2 | 8 |

对齐的思想是通过将内存放置在特定的边界上允许硬件更有效地读取内存。编译器负责对齐，所以我不需要。根据字段的大小及其在结构体中的位置，Go 决定填充。

#### 列表 2.10

```go
type example2 struct {
    flag    bool
    counter int16
    flag2 bool
    p       float32
}
```

在这个示例中，我在 `counter` 和 `p` 字段之间添加了一个名为 `flag2` 的新字段。这导致结构体内部更多的填充。

#### 列表 2.11

```go
type example2 struct {
    flag bool      // 0x00010020 <- 起始地址
    byte          // 0x00010021 - 1 字节填充
    counter int16  // 0x00010022 - 2 字节对齐
    flag2 bool     // 0x00010024 - 1 字节对齐
    byte          // 0x00010025 - 1 字节填充
    byte          // 0x00010026 - 1 字节填充
    byte          // 0x00010027 - 1 字节填充
    pi float32    // 0x00010028 - 4 字节对齐
}
```

这就是对齐和填充的情况。`example2` 类型的值从地址 `0xc001020` 开始。`flag` 字段代表起始地址且大小只有 1 字节。由于 `counter` 字段需要 2 字节分配，它必须在内存中以 2 字节对齐放置，这意味着它需要落在 2 的倍数地址上。这要求 `counter` 字段从地址 `0x001022` 开始。这在 `flag` 和 `counter` 字段之间创建了一个 1 字节的间隙。

#### 图 2.2

| Flag | | Counter | | Flag2 | | | | | 12 |
|---|---|---|---|---|---|---|---|---|
| 0 | 1 | | 4 | 5 | 6 | 7 | 8 | | 12 |

`flag2` 字段是一个 `bool`，可以落在下一个地址 `0xc001024`。最后一个字段是 `pi`，它需要 4 字节分配，因为它需要落在 4 字节对齐的边界。4 字节值的下一个地址是 `0xc001028`。这意味着需要 3 个填充字节来保持适当的对齐。这导致 `example2` 类型的值需要共 12 字节的内存分配。

结构体中最大的字段代表整个结构体的对齐边界。在这种情况下，最大的字段是 4 字节，因此该结构体值的起始地址必须是 4 的倍数。可以看到地址 `0xc001020` 是 4 的倍数。

如果我需要尽量减少填充字节的数量，我必须从高分配到低分配排列字段。这将任何必要的填充字节都推到结构体的底部，并减少所需的填充字节总数。

#### 列表 2.12

```go
type example struct {
    pi float32    // 0x00010020 <- 起始地址
    counter int16  // 0x00010024 - 2 字节对齐
    flag bool      // 0x00010026 - 1 字节对齐
    flag2 bool     // 0x00010027 - 1 字节对齐
}
```

在重新排列字段后，该结构体值只需要 8 字节的分配。

而不是 12 字节。由于所有字段都允许结构体值落在 4 字节对齐上，因此不需要额外的填充字节。

#### 图 2.3

| Pi | Counter | Flag | Flag2 |
|---|---|---|---|
| 0 | 4 | 6 | 7 8 |

### 2.8 变量赋值

如果我有两个结构完全相同的不同命名类型，我无法将其中一个值赋值给另一个。

例如，如果类型 `example1` 和 `example2` 使用完全相同的声明声明，并且我们初始化了两个变量。

#### 代码列表 2.13

```
var ex1 example1
var ex2 example2
```

我无法将这两个变量互相赋值，因为它们是不同的命名类型。它们结构相同这一事实无关。

#### 代码列表 2.14

```
ex1 = ex2 // 不允许，编译器错误
```

要执行此赋值，我将必须使用转换语法，由于它们的结构相同，编译器将允许这种操作。

#### 代码列表 2.15

```
ex1 = example1(ex2) // 允许，没有编译器错误
```

然而，如果 `ex2` 被更改为使用 `ex1` 相同的声明定义的匿名类型，则不需要转换语法。

#### 代码列表 2.16

```
var ex2 struct {
  flag bool
  counter int
  pi float32
}

ex1 = ex2 // 允许，不需要转换语法
```

编译器将允许赋值而不需要转换。

### 2.9 指针

指针的作用跨程序边界共享值。有几种类型的边界。最常见的是函数调用之间的。还有 Goroutine 之间的边界。

当 Go 程序启动时，运行时创建 Goroutine。Goroutine 是与操作系统线程语义类似的轻量级线程。每个 Go 程序都有一个称为栈的内存块。栈从 2048 字节（2k）开始，非常小，但大小会随时间增长。

#### 图 2.4 ![](img/8be06d7892d0a851e9bad632.png)

每次调用函数时，都会占用一个栈空间来帮助 Goroutine 执行与该函数相关的指令。给定函数的栈帧大小是在编译时计算的。除非编译器在编译时知道该值的大小，否则该值必须在堆上构造。栈是自动清理的。每次我调用函数时，都会产生一个内存帧，该帧被初始化，这就是栈如何自动清理的。函数返回时，内存帧保持原样，因为不再需要该内存。

### 2.10 值传递

所有数据通过值在程序中移动。这意味着当数据跨程序边界时，每个函数或 Goroutine 都有自己的数据拷贝。我们有两种类型的数据：值本身（int, string）或值的地址。地址需要跨程序边界复制和存储的数据。

以下代码尝试解释这一点。

#### 代码列表 2.17

```go
func main() {
  // 声明值为 10 的 int 类型变量
  count := 10
  // 要获取值的地址，使用 & 运算符
  println("count:\tValueOf(",", count, "\tAddrOf(",", &count, ")")
  // 将 count 的“值”（框里的的内容）传递给 increment1 函数
  increment1(count)
  // 打印 count 的“值”和“地址”。
  // 在函数调用后，count 的值不会改变。
  println("count:\tValueOf(",", count, "\tAddrOf(",", &count, ")")
  // 将 count 的“地址”拷贝传递给 increment2 函数。
  // 这仍然被视为值传递而不是引用传递，因为地址是值。
  increment2(&count)
  // 打印 count 的“值”和“地址”。
  // 在函数调用后，count 的值已经改变了。
  println("count:\tValueOf(",", count, "\tAddrOf(",", &count, ")")
}

// increment1 声明接受整数值的它自己的拷贝。
func increment1(inc int) {
  // 增加调用者 int 值的本地拷贝
  inc++
  println("inc:\tValueOf(",", inc, "\tAddrOf(",", &inc, ")")
}

// increment2 声明接受指向整数值的地址的自己的拷贝。
// 指针变量是字面类型，并使用 * 定义。
func increment2(inc *int) {
  // 通过指针增加调用者的值。
  *inc++
  println("inc2:\tValueOf(",", inc, "\tAddrOf(",", inc, "\tPointsTo(", inc, ")")
}
```

输出：
count: Value Of[ 10 ] Addr Of[ 0xc00050738 ]
incl: Value Of[ 11 ] Addr Of[ 0xc00050730 ]
count: Value Of[ 10 ] Addr Of[ 0xc00050738 ]
inc2: Value Of[ 0xc00050738 ] Addr Of[ 0xc00050748 ] Points To[ 11 ]
count: Value Of[ 11 ] Addr Of[ 0xc00050738 ]

关于栈和指针有很多细节，要了解更多信息，请阅读第 14 章中题为“栈和指针机制”的文章。

### 2.11 逃逸分析

编译器用于判断值应该在栈上还是堆上构造的算法。理解逃逸分析是关于值的所有权。其思想是，当一个值在函数作用范围内构造时，函数会询问：正在构造的值在函数返回时还必须存在吗？如果答案是否，则该值可以在栈上构造。如果答案是是，则该值必须在堆上构造。

注意：所有权规则是识别导致分配的代码的良好基础。然而，我必须意识到逃逸分析存在缺陷。

#### 代码列表 2.18

```go
// user 代表系统中的一个用户
type user struct {
    name string
    email string
}

func stayOnStack() user {
    u := user(
        name: "Bill",
        email: "bill@email.com",
    )
    return u
}
```

`stayOnStack` 函数使用值语义将值返回给调用者。换句话说，调用者获得了构造值的自己的拷贝。当 `stayOnStack` 函数被调用并返回时，它构造的值不再需要存在，因为调用者拥有自己的拷贝。因此，在 `stayOnStack` 内部对值的构造可以在栈上进行。不需要分配。

#### 代码列表 2.19

```go
type user struct {
    name string
    email string
}

func escapeToHeap() *user {
    u := user(
        name: "Bill",
        email: "bill@email.com",
    )
    return &u
}
```
