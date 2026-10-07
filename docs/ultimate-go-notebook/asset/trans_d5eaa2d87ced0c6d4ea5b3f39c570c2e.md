
而不是 12 字节。由于所有字段都允许结构体值落在 4 字节对齐上，因此不需要额外的填充字节。

图 2.3

| Pi | Counter | Flag | Flag2 |
|---|---|---|---|
| 0 | 4 | 6 | 7 8 |

## 2.8 变量赋值

如果我有两个结构完全相同的不同命名类型，我无法将其中一个值赋值给另一个。

例如，如果类型 `example1` 和 `example2` 使用完全相同的声明声明，并且我们初始化了两个变量。

代码列表 2.13

```
var ex1 example1
var ex2 example2
```

我无法将这两个变量互相赋值，因为它们是不同的命名类型。它们结构相同这一事实无关。

代码列表 2.14

```
ex1 = ex2 // 不允许，编译器错误
```

要执行此赋值，我将必须使用转换语法，由于它们的结构相同，编译器将允许这种操作。

代码列表 2.15

```
ex1 = example1(ex2) // 允许，没有编译器错误
```

然而，如果 `ex2` 被更改为使用 `ex1` 相同的声明定义的匿名类型，则不需要转换语法。

代码列表 2.16

```
var ex2 struct {
  flag bool
  counter int
  pi float32
}
ex1 = ex2 // 允许，不需要转换语法
```

编译器将允许赋值而不需要转换。

## 2.9 指针

指针的作用跨程序边界共享值。有几种类型的边界。最常见的是函数调用之间的。还有 Goroutine 之间的边界。

当 Go 程序启动时，运行时创建 Goroutine。Goroutine 是与操作系统线程语义类似的轻量级线程。每个 Go 程序都有一个称为栈的内存块。栈从 2048 字节（2k）开始，非常小，但大小会随时间增长。

图 2.4 ![](img/8be06d7892d0a851e9bad632.png)

每次调用函数时，都会占用一个栈空间来帮助 Goroutine 执行与该函数相关的指令。给定函数的栈帧大小是在编译时计算的。除非编译器在编译时知道该值的大小，否则该值必须在堆上构造。栈是自动清理的。每次我调用函数时，都会产生一个内存帧，该帧被初始化，这就是栈如何自动清理的。函数返回时，内存帧保持原样，因为不再需要该内存。

## 2.10 值传递

所有数据通过值在程序中移动。这意味着当数据跨程序边界时，每个函数或 Goroutine 都有自己的数据拷贝。我们有两种类型的数据：值本身（int, string）或值的地址。地址需要跨程序边界复制和存储的数据。

以下代码尝试解释这一点。

代码列表 2.17

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

## 2.11 逃逸分析

编译器用于判断值应该在栈上还是堆上构造的算法。理解逃逸分析是关于值的所有权。其思想是，当一个值在函数作用范围内构造时，函数会询问：正在构造的值在函数返回时还必须存在吗？如果答案是否，则该值可以在栈上构造。如果答案是是，则该值必须在堆上构造。

注意：所有权规则是识别导致分配的代码的良好基础。然而，我必须意识到逃逸分析存在缺陷。

代码列表 2.18

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

stayOnStack 函数使用值语义将值返回给调用者。换句话说，调用者获得了构造值的自己的拷贝。当 stayOnStack 函数被调用并返回时，它构造的值不再需要存在，因为调用者拥有自己的拷贝。因此，在 stayOnStack 内部对值的构造可以在栈上进行。不需要分配。

代码列表 2.19

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

escapeToHeap 函数使用指针语义将值返回给调用者。换句话说，调用者获得了对构造值的共享访问权限（地址）。当 escapeToHeap 函数被调用并返回时，它构造的值仍然需要存在，因为调用者拥有该值的共享访问权限。因此，在 escapeToHeap 内部对值的构造不能在栈上进行，它必须在堆上进行。有分配。

思考一下，如果上一个例子中的 user 值在返回时使用指针语义在栈上构造，会发生什么。

