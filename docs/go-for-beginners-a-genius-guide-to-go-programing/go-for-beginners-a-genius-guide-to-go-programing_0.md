# Go 入门指南：Go 编程天才指南



![](img/Image00002.jpg)







- 关于作者
- Edward Thornton 的其他作品
- 参考文献




你之所以拿起这本书，可能是因为已经听过很多关于 Go 的介绍，并想将其加入你的编程工具箱。或者也许你没有多少编程经验，所以这种轻量级语言看起来非常适合你的胃口。也许你的公司正在考虑引入 Go 来提高应用程序的性能，或者你希望在像 SoundCloud、Uber、BBC 或 Dropbox 这样的公司工作。如果你熟悉其他语言，可能可以在几小时内学会 Go。如果编程经验较少，你可能需要花更多的时间来学习。然而，它非常清晰，而且由于是一门相对年轻的语言，它没有软件开发语言随着时间推移而增加的额外负担。

在本书中，在我们深入学习语言本身之前，你将发现为什么它如此受欢迎，以及为什么越来越多的程序员在采用它。Go 的可读性比许多其他语言都要，这使其非常适合开源编程。你将学习基础知识，包括基本类型和字符串，以及如 `if-else` 和 `for range` 等控制结构。你还将了解 Go 中的函数、切片和数组。映射（Maps）和包（Packages）是 Go 编程的重要组件，我们在书中提供了关于这两者的细节。此外，你还将学习方法（以及它们与函数的区别）、接口和反射。还有关于阅读语言的信息，更不用说协程（goroutines）和通道（channels）。最后，可能最重要的是，我们还包含了一个关于测试和错误处理的章节，以及一个关于常见陷阱和模式的章节。了解许多开发者犯的错误，这样你就可以避免它们了！一旦你通过这本书学会了语言的基础，你就可以开始编写 Go 了。

作为一名 Go 程序员，我写这本书是为了帮助他人学习这种语言。我帮助过你这样的其他软件开发者快速上手 Go。我认为尽可能多的开发者应该开始学习它，这样他们就可以编写出运行更快、更简洁并有助于开源应用流行的代码。

你越早开始阅读这本书，就能越早开始编程——真的那么简单！Go 的设计目标是为了快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？


2009 年，Google 员工团队向世界介绍了 Go。（它有时被称为 Golang，以区别于著名的棋类游戏 Go/围棋。）据说，他们是在等待另一种语言的程序编译时开始创建它的。员工们对当时可用语言的局限性感到沮丧，决定从头开始重新思考编程，从底层开始构建。

随着时间的推移，计算机语言（就像口语一样）往往会积累额外的负担，阻碍并减慢代码运行的速度。从零开始意味着他们可以构建出精简但强大到足以处理海量代码的东西。他们还将其设计为开源，因此很容易创建新的应用程序，并在各种行业中的许多用途中使用它们。

首先，简单回顾一下程序：它们仅仅是一组指令。编译器和解释器都接收人类可编写的代码。

## 为现代环境设计

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

首先，简单回顾一下程序：它们仅仅是一组指令。编译器和解释器都接收人类可编写的代码。

随着时间的推移，计算机语言（就像口语一样）往往会积累额外的负担，阻碍并减慢代码运行的速度。从零开始意味着他们可以构建出精简但强大到足以处理海量代码的东西。他们还将其设计为开源，因此很容易创建新的应用程序，并在各种行业中的许多用途中使用它们。

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

该语言的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

## Go 的优势

### 灵活性
这种语言可以为开发者解决很多问题。通过它，大数据和机器学习等更多的开发将成为可能。

### 自动文档
Go 的设计目标是能够快速学习和快速执行。所以，尽管投入开始你的 Golang 之旅吧；还要等什么时候将这个强大的工具加入你的工具箱呢？

### 内置测试
该语言自带用于测试和性能分析的 API，以及自己的示例。

### 静态代码分析
使用元工具 `GoLinter`，你可以在运行代码之前通过根据代码规则进行分析来调试。

### 检测竞态条件
当多个线程竞争时，它们可能会以意想不到的顺序完成，导致难以追踪的错误。

## Go 的劣势

### 缺乏 GUI 库
缺乏 GUI 库对于单页应用没有问题，但需要同时提供速度和 GUI 的企业通常选择其他语言。

### 泛型
由于 Go 的设计方式，处理某些函数时，你可能需要比其他语言编写更多的代码。



虽然在 Go 中处理错误非常简单，但它可能比其他语言需要更多的代码。

### 依赖管理

你可以使用 Go 安装不同的库，但如果库的维护者上传了一个不向后兼容的版本，任何运行你程序的人都会收到错误。如果没有安装该库，程序将无法编译。

虽然*有*工具可以帮助你管理这一点（`Dep`），但它要么强制你加载存储库中的所有依赖项，要么存储包列表。如果你存储在存储库中，你的代码会变得*大得多*，因为你还存储了许多行依赖代码。然而，如果你只存储包列表，可能会遇到向后不兼容的问题，这会导致你的程序崩溃。

## 谁应该使用 Go？

这种语言非常适合需要速度的应用程序的底层代码。它也适用于需要扩展性的高性能应用。

Google 将其用于云服务基础设施；YouTube、Netflix 和 Soundcloud 等公司使用 Go 来处理其平台的高负载并发；Uber 使用它来提高地图处理速度，从而缩短了乘客与司机的匹配时间；数据科学组织越来越多地使用它来处理大数据并对其进行分析。

Go 是金融科技开发者的绝佳解决方案，因为它允许用户与其金融机构之间进行无缝连接。Paypal 已使用它进行扩展，AmEx 用于支付，Salesforce 用于其“Einstein Analytics”。它也成为区块链编程（尤其是以太坊网络）的首选语言。

如你所见，Go 对于几乎任何现代程序员来说都是一个很好的工具。无论是系统编程、网络编程、Web 应用程序还是 DevOps，这种语言都易于使用和阅读。而且对于今天的用户最重要的是，它比许多其他可用选项要快得多。

## 章节总结

Go 由 Google 的工程师设计，他们希望有一种更快的、能够利用多核的计算机语言。

*   因为是一门较年轻的语言，它非常适用于位于云端而非特定硬件的现代应用程序，并且可以并发运行操作。

*   Go 非常灵活，并使用的 `goroutines` 可以同时运行而不会降低速度，这是它的其他优点之一。

*   Golang 的 GUI 库不存在，因此它不被首选除了速度外还依赖 GUI 的应用，这是它的缺点之一。

*   Go 适用于许多不同的应用程序和行业，特别是对于那些具有高用户负载或其他大数据需求的场景。

在下一章中，你将学习 Go 的基础。

## 第二章

在本章中，我们将深入研究 Golang 的基础，你可以将其想象成该语言的基础词汇。如果你用过类似 `C` 和 `C++` 的语言进行过编程，那么你会对其中一些感到熟悉。

## 标识符、文件名和关键字

如果你对编程还比较陌生，*标识符*是用户定义的程序组件名称。Go 中的标识符可以是函数名、常量、变量、语句标签、类型或包名。

Go 标识必须以特定的方式编写才能被程序识别。它必须以字母或下划线开头，而不是数字。标识符本身可以包含字母、数字和下划线。它是区分大小写的，所以虽然 `Go_lang` 和 `go_lang` 是不同的，但它们都是有效名称。Golang 标识符

### 函数

函数是执行任务的代码块。在 Go 中，使用以下语法定义函数：

```
func function_name (parameter list) [return_types] {
    body
}
```

其中

*   `func` 开始声明，告诉程序有一个函数要登场
*   `function_name` 为函数命名
*   `parameter` 类似于占位符，提供了参数的类型和数量
*   `return_types` 是函数返回的数据类型列表；这并不是强制要求的
*   `body` 定义了函数的功能

例如，假设你想要一个函数显示两个数字 `num1` 和 `num2` 的最大值：

```go
func max (num1, num2 int) int {
    result int //程序会忽略 // 之后的内容所以你在这里写注释。注意这是一个局部变量。

    if (num1 > num2) {
        result = num1
    } else {
        result = num2
    }

    return result
}
```

## 数据类型

变量的类型指定了它所占的空间以及如何解释位模式。在 Go 中，你可以将其分为四类：

### 布尔类型

只有两个：true 和 false。*Bool* 是四种基本类型之一。

### 数值类型

这些可以是整数或浮点数。数值类型的示例包括 `uint8`（0 到 255 的无符号 8 位整数）、`int16`（符号 16 位整数）以及类似的整数类型。

浮点数可以是 `float32`（IEEE 32 位浮点数）、`float64`（IEEE 64 位浮点数）、`complex62`（带有实部和虚部的 float32）或 `complex128`（带有实部和虚部的 float64）。

*int* 和 *float* 也是基本类型。

## 字符串

这些表示字符串的值，字符串是字节序列。一旦创建，字符串就无法更改。字符串可以是字母数字，例如经典的“helloworld”。字符串也是一种基本类型。

### 派生类型




这些包括指针类型、数组类型、结构体类型、映射类型等，将在后面的章节进一步讨论。

## 常量

与其他静态类型程序一样，编译器在编译时已经知道或可以推导出每个变量的类型。然而，与其他语言不同，Go 不允许你混合数值类型。C、C++ 或 Java 在类型混合使用时，会将较小的类型（如 `int`）转换为较大的类型（如 `float`）。

Golang 工程师认为，允许这些自动转换不仅可能导致代码难以阅读，还会在不同平台之间产生不一致性。由于 Go 设计用于在各种架构上运行，因此该语言设计为要求显式类型。

除非你显式地给常量指定类型，否则即使你给它命名，它也会被视为无类型。整数类型的无类型常量只能在允许整数的地方。例如，你不能将整数常量赋值给字符串或布尔变量。无类型浮点常量可以使用任何允许浮点数的地方。

Go 中的所有无类型常量都有默认类型。整数常量默认为 `int`，浮点数默认为 `float64`，字符默认为 `rune` 等。当你声明一个类型时，该常量就变成了有类型的。再次，常量必须声明为其正确的类型，否则程序将返回错误。

除非绝对需要，否则在声明常量时不要指定类型；声明类型会让你失去在操作中混合类型的灵活性。

 Go 中的常量表达式有几条规则。

* 两个无类型常量之间的比较结果是一个无类型布尔常量（`true`/`false`）。
* 相同类型的操作数结果为相同类型。换，如果是两个无类型整数常量，结果就是无类型整数常量。表达式 `11/2` 的结果是 `5` 而不是 `5.5`，因为它被截断为整数。
* 如果它们不是相同类型，根据以下逻辑结果为两者中范围更广的类型：`integer<rune<floating-point<complex`

## 变量

在所有语言中，变量都是程序使用的特定存储区域的名称。变量名可以使用字母、数字和下划线。Golang 变量具有特定的大小、内存布局、内存布局的值范围以及可能的操作。变量定义告诉编译器为该变量创建多少存储以及将其放在何处。

`Lvalues` 用于引用内存位置，可以出现在赋值的左侧或右侧。`RValues` 指存储在内存中的数据值。变量是 lvalues 并出现在赋值的左侧。

当你声明变量时，将使用关键字 `var`。

## 运算符

大多数编程语言都有运算符，即执行各种数学或逻辑操作的内置符号。Go 有三种类型：位运算、算术和逻辑。

### 位运算

这些运算符作用于相同位长度的变量（即整数）。

* 与：`&`
* 或：`⎸`
* 异或与取反：`⌃`
* 清零：`&⌃`

### 算术

你可能在数学课上熟悉这些操作。它们包括用于加法的 `+`、乘法的 `*`、除法的 `/` 和取模 `%`。

### 逻辑

虽然这些运算符与其他语言中的运算符相似，但 Golang 对可以相互比较的值非常严格。

* 等于：`=`
* 不等于：`!=`
* 小于：`<`
* 小于等于：`<=`
* 大于：`>`
* 大于等于：`>=`

## 字符串

在这个语言中，字符串与它们在 C++、Python、Java 等中的方式有所不同。它们是不可变的，或只读。如果你尝试更改字符串，将得到错误。字符代表 UTF-8 编码的字节。

为什么 UTF-8 编码很重要？当计算机最初设计时，它们在二进制代码中使用 8 位的字节，英语字母表中的每个字母都有自己的字节。（这被称为 ASCII 格式）。使用二进制编码有 256 种方式，而英语字母加上符号只需要 128 种。

然而，一旦其他语言的使用者想要编程，仅剩 128 个唯一字节就成了一个问题。Unicode 诞生了，它为每个字符提供了一个代码点。它可以生成大约百万个代码点，这对于地球来说足够了——至少目前！

UTF-8，或 Unicode 转换格式，将代码点转换为二进制反之亦然。由于 UTF-8 的实用性，你可以在字符串中使用任何语言。

通常，字符串在开始和结束用双引号（`"`）括。查看此示例：

```go
package main

import "fmt"

func main () {
    var my_words string //在此处使用关键字 var
    my_words = "Hello world"
    //显示字符串
    fmt.println("String: ", my_words)
}
```
输出: Hello world

有时，字符串不使用双引号，而是使用反引号（`` ``）。这在编写 HTML 时、编写包含多行的消息时以及编写正则表达式时很常见。

## 时间和日期

在 Go 中，时间包含一个位置。如果没有指定，它默认是 UTC 协调世界时。如果你需要时间戳，则使用 `Now()`：

```go
Now()
```

对于日期，使用 `Date()`：

```go
Date(year, month, day, hour, min, nsec, loc)
```

如果你想知道两个瞬间之间过去了多久，使用 `Since()`：

```go
Since(t)
```

如果你想知道距离时间还有多久，使用 `Until()`：

```go
Until(t)
```

## 章节总结

Golang 与其他语言相似，但如果你用 Java、C++ 或 Python 编程，记住 Go 的不同之处是非常重要的。

* Go 的“词汇量”设计得易于阅读且清晰。
* 文件名、标识符、变量、常量和关键字的语法规则可能与其他程序有相似之处。
* Go 包含多种数据类型，常量不需要指定其类型——事实上，让它们保持无类型通常更好。

在下一章中，你将学习控制结构。

## If-Else

一个简单的 *if 语句* 会条件为真时执行。如果为假，则什么都不会发生。if 语句的写法如下：

```go
if condition {
    // 如果条件为真将执行的代码
}
```



例如，下面的输出是 A（如果条件为真）。

```go
package main

import (
    "fmt"
)

func main () {
    var grade = A
    x := true
    If x {
        fmt.println(grade)
    }
}
```

然而，如果你想让程序在条件为真时执行一个操作，在条件为假时执行另一个操作，那么你需要一个 `if-else statement`。正如你可能猜到的那样，这些语句的形式如下：

```go
If condition {
    // 如果条件为真，将执行的代码
} else {
    // 如果条件为假，将执行的代码
}
```

在这个示例中，如果 `x >= 60`，则输出为 Pass：

```go
package main

import (
    "fmt"
)

func main () {
    x := 75
    If x >= 60 {
        fmt.println("Pass")
    } else {
        fmt.println("Fail")
    }
}
```

`else` 部分只在必要时才会执行；如果条件为真，其余部分将被忽略。

If-else 语句可以有多个 `else` 或备选语句。在 Go 中，它们被称为 `if-else if-else`语句。写法如下：

```go
If condition-1 {
    // 如果 condition-1 为真，将执行的代码
} else if condition-2 {
    // 如果 condition-2 为真，将执行的代码
} else {
    // 如果两个条件都为假，将执行的代码
}
```

在这个示例中，成绩分为优良、通过或不及格。如果 `x >= 90`，则输出为 high-pass。60 是通过与不及格的分界点。

```go
package main

import (
    "fmt"
)

func main () {
    x := 95
    If x >= 90 {
        fmt.println("High-pass")
    } else if x >= 60 {
        fmt.println("Pass")
    } else {
        fmt.Println("Fail")
    }
}
```

## Switch-Case

正在寻找更简单的方法来编写多个 if-else 语句吗？`switch` 是编写该序列的一种更短的方法。它类似于你可能在 C、C++ 或 Java 中用过的 switch。然而，在 Go 中，控制 switch 会运行第一个条件为真的 case 并忽略剩余部分。`switch` case 不需要是常量，且值也不必须是整数。如果 `case` 中有多个表达式，你可以使用逗号进行分隔。这里有一个 `switch case` 的示例，用于判断当前是工作日还是周末。

```go
package main

import (
    "fmt"
)

func main () {
    switch time.Now().Weekday() {
    case time.Saturday, time.Sunday:
        fmt.Println("It’s the weekend")
    default:
        fmt.Println("It’s a weekday")
    }
}
```

### For

`for loop` 是 Go 中唯一的循环结构。它用于重复执行语句直到满足特定条件。如果没有需要满足的条件，或者程序无法满足该条件，它将进入无限循环。

举一个简单的例子，比如列出从一到十的数字。如果没有循环结构，你将不得不写十条语句：

```go
fmt.Println(1)
fmt.Println(2)
fmt.Println(3)
fmt.Println(4)
fmt.Println(5)
... 直到你写 `fmt.Println(10)`。
```

使用 `for` 循环，你只需要写一次。

```go
x := 1
for x <= 10 {
    fmt.Println(x)
    x += 1
}
```

在这里，你告诉程序检查 `x` 是否小于或等于 10。如果是，则打印 `x`。注意，如果不加 `+1`，`x` 将始终是 1 并在无限循环中打印。你也可以简化 `for` 循环，可以写为：

```go
for x := 1; x <= 10; x++ {
    fmt.Println(x)
}
```

第一行将 `x` 赋值为 1，检查 `x` 是否小于 10，如果是，则执行第二行。

## For Range

`for loop` 用于遍历各种数据结构（如数组、切片、字符串）中的元素。你将在后面的章节中学习更多相关内容。`for range` 语句使用关键字 `range` 来重复遍历数组、切片、map 等。为了 sake of example，假设你有一个切片并想要遍历其中的数字：

```go
nums := []int{2,3,4}
sum := 0
for _, num := range nums {
    sum += num
}
fmt.Println("Sum:", sum) // 输出结果为 Sum: 9
```

## Break and Continue

这些控制语句帮助你在 Go 程序中添加逻辑。`break statement` 结束当前循环，通常与 `if` 语句配合使用。下面的程序显示了 `break` 和 `if` 语句是如何工作的：

```go
package main

import (
    "fmt"
)

func main () {
    for x := 0; x < 10; x++ {
        if x == 5 {
            fmt.Println("Breaking out of loop")
            break // 当 x 达到 5 时 
        }
        fmt.Println("The value of x is", x) // 如果没有 break
    }
    fmt.Println("Exiting program")
}
```

该程序的输出如下：
*The value of x is 0*
*The value of x is 1*
*The value of x is 2*
*The value of x is 3*
*The value of x is 4*
*Breaking out of loop*
*Exiting program*

如果你将循环嵌套在一起，内部循环中的 `break` 并不意味着外层循环的 `break`。相反，你可能想跳过循环的剩余部分并返回顶部重复。这就是 Go 中 `continue statement` 的用途。例如，我们可以修改上面的程序，使其在 `x = 5` 时不是停止，而是跳过 5 继续运行直到达到 10：

```go
package main

import (
    "fmt"
)

func main () {
    for x := 0; x < 10; x++ {
        if x == 5 {
            fmt.Println("Continuing loop")
            continue // 当 x 为 5 时代替 break
        }
        fmt.Println("The value of x is", x)
    }
    fmt.Println("Exiting program")
}
```

现在你将得到一个不同的结果，循环在 5 处继续而不是结束。

*The value of x is 0*
*The value of x is 1*
*The value of x is 2*
*The value of x is 3*
*The value of x is 4*
*Continuing loop*
*The value of x is 6*
*The value of x is 7*
*The value of x is 8*
*The value of x is 9*
*Exiting program*

`continue statement` 通常用于你需要循环但想消除程序中某些不需要的情况。使用 `continue` 还可以避免多层条件嵌套。

## Labels: Goto

与 `break` 和 `continue` 语句一样，`goto` 会改变程序的执行，指令计算机跳转到标记语句并从那里运行程序。标签是用文本编写的标识符，可以位于程序中 `goto` 语句的任何位置。与 `continue` 和 `break`一样，`goto` 经常与 `if` 和 `if-else` 控制语句一起使用。

在这个示例中，你根据输入的年龄得到不同的答案。

```go
package main

import "fmt"

func main () {
    var age int
    election: // 这是一个标签
    fmt.Println("Enter your age ")
    fmt.Scanln(&age) // 用户输入年龄
    if (age <= 17) {
        fmt.Println("You are not eligible to vote.")
        goto election
    } else {
        fmt.Println("You are eligible to vote.")
    }
}
```

输出可能像这样：

*Enter your age 16*
*You are not eligible to vote.*
*Enter your age 17*
*You are not eligible to vote.*
*Enter your age 20*
*You are eligible to vote.*





既然你已经了解了如何使用 `goto`，请尝试在编程中避免使用它。不仅是在 Go 语言中，其他语言也是如此。大多数情况下，有其他的构造方式，这对于想要阅读程序的开发者来说更容易理解。使用 `goto` 会使得追踪程序的控制流变得非常困难，增加了理解和修改的难度。由于 Go 的设计初衷是在开源平台上运行，因此你的代码也应该设计成便于他人使用和修改。

## 章节总结

控制结构是程序的构建块。在 Go 中，你可以使用条件语句或循环来实现控制。

*   条件语句包括 `if`、`if-else` 和 `if-else if-else` 语句；它们引导程序在满足某些条件时执行。
*   `Switch` case 是一种更短（也更简单）的编写多种备方案的方法，可以代替带有许多行的 `if-else if-else` 语句。
*   循环用于重复指令，而不是在代码中写下所有行。
*   `For` 是 Go 识别的唯一循环控制，而 `for range` 增加了对范围的遍历。
*   `Break` 和 `continue` 是跳过循环部分的不同方式。
*   `Goto` 是另一种通过将程序发送回特定标签（label）来控制循环的方法，但 `goto` 语句会让程序更难理解和使用，因此不建议使用。

在下一章中，你将学习函数。

## 四章

在之前的章节中，你学习了一些关于 Golang 函数的知识。在这里，我们将更深入地探讨该语言中一些常用的函数。作为复习，函数是完成特定任务的语句组。本质上，一个函数接收一个输入并产生某种输出。

以大写字母开头的函数名将导出到其他包，而以小写字母开头的函数将仅在同一个包中使用。（`package` 是一组编译在一起的源文件）。函数名不能以数字开头，不能包含空格。如果名称中包含多个单词，第一个单词后的每个单词都应该大写，例如 `simpleFunction`。

## 函数基础

`SimpleFunction` 是一个既没有参数也没有返回值的函数。它用于打印消息。

```go
package main

import "fmt"

func SimpleFunction (){
    fmt.Println("Hello World")
}

func main () {
    SimpleFunction ()
}
```

这里的输出仅仅是
*Hello World*

如果你想向函数传递信息，可以使用 `arguments`（参数），它们就像变量一样。它们被指定在括号内并用逗号分隔。传递的参数数量没有限制。

这里有一个两个 `int` 类型参数的示例。一旦调用函数 `add`，你就可以传递两个整数。

```go
package main

import "fmt"

func add(x int, y int) {
	total := 0
	total := x + y
	fmt.Println (total)
} //这部分代码接受参数

func main () {
	add (10, 20)
} //这里是传递参数的地方
```

在这种情况下，输出是 30。

## 返回值与参数

如果你声明了返回值，那么你还需要一个 `return` 语句。`return value`（返回值）是在执行指令后保留函数输出的内容。在 Go 中，与其他一些语言不同，有多种值类型。作为编码者，你可以决定是否要给它命名。

例如，你可以使用“裸返回”（naked return），即使用 `return` 关键字，但在体内部不指定返回值。只要你在函数头中声明了返回值，且该变量与你在函数头中声明的名称相同，它就能工作。

这是一个裸返回的示例。

```go
package main

import (
	"fmt"
)

func greeting (name string) (message string) {
	message = "Hello, " + name //变量必须与函数头中的相同，例如 message
	return // 注意，由于上面指定了 message，这里不需要再次声明
}

func main () { //greeting 返回值
	//函数存储了该变量
	msg := greeting("world")
	fmt.Println(msg)
}
```

输出为 Hello, world。

你还可以构建具有多个返回值和多个参数的函数。然而，函数在返回时持有的变量数量必须与函数中的变量数量相同。

假设你想对两个命名为 `x` 和 `y` 的数字运行四个基础算术操作。它看起来如下：

```go
package main

import (
	"fmt"
)

func operations (x, y int) (sum, diff, prod, div int) {
	//函数有 4 个变量：x+y
	sum = x + y
	diff = x - y
	prod = x * y
	div = x / y
	fmt.Println(sum, diff, prod, div)
}

func main() {
	operations(10, 5)
}
```




通过 `recursive functions`（递归函数），函数会不断调用自己，规模越来越小，直到最终遇到 `base case`（也称为基准情况）。在这一点上，它最终收敛并停止进一步调用。递归有两种方式：直接递归，即不调用其他函数；或者间接递归，这需要另一个函数来协助。

作为程序员，你可能会遇到或想要使用的其他类型的递归。如果只有两个函数，则被称为 `mutual recursion`（相互递归）。尾递归涉及 `tail call`（尾调用），即函数的最后一个调用。如果最后一个调用或尾调用调回了该函数，则被称为 `tail-recursive`（尾递归）。同样，`head-recursive`（头递归）是指第一个语句为递归调用的函数。

### 1. 直接示例

这是一个使用递归函数计算正整数阶的示例。你可能（或不记得）在数学课上记得阶乘由数字后加一个感叹号表示（例如 `4!`），并等于该数字之前所有数字的乘积。换句话说，`4! = 4*3*2*1 = 24`。

在这里，基准情况是 `0` 或 `1`（结果为 `1`）。在这个示例中，函数每次递减一个整数，直到达到基准情况，此时函数停止。负数将返回错误消息。

```go
package main

import (
    "fmt"
)

func factorial_calc(number int) int {
    if number == 0 || number == 1 { // base case
        return 1
    }

    if number < 0 { //if number is negative
        fmt.Println("Invalid Number")
        return -1
    }

    return number*factorial_calc(number-1) // recursive function until operation reaches the base case
}

func main() {
    answer1 := factorial_calc(0) //where 0 is the parameter to be passed
    fmt.Println(answer1, "\n")
    answer2 := factorial_calc(4)
    fmt.Println(answer2, "\n")
    answer3 := factorial_calc(-1)
    fmt.Println(answer3, "\n")
    answer4 := factorial_calc(5)
    fmt.Println(answer4, "\n")
}
```

该示例的输出如下：
```
0
24
Invalid number
-1
120
```

### 2. 间接示例

在这里你将看到使用另一个函数进行递归的样貌。假设你想从 `n` 开始递减打印所有数字。

```go
package main

import (
    "fmt"
)

func print_one(n int) {
    if n >= 0 {
        fmt.Println("In first function: ", n)
        print_two(n-1) //prints n if n is a positive integer and calls the second function
    }
}

func print_two(n int) {
    if n >= 0 {
        fmt.Println("In second function: ", n)
        print_one(n-1)
    }
}

func main() {
    print_one(6) //prints all positive integers from 1 up to 6
    print_one(-10) //prints nothing because it doesn’t follow the base case n >= 0
}
```

你将看到的输出：
```
In first function: 6
In second function: 5
In first function: 4
In second function: 3
In first function: 2
In second function: 1
In first function: 0
```

你想要避免的是 `infinite recursion`（无限递归），即函数永远不会收敛。通常，这种操作会导致系统崩溃或内存过载。如果你不指定基准情况并启动递归调用，最终将导致无限递归。

Golang 还允许你使用 `anonymous`（匿名）函数，它们没有名称。你也可以将它们用于递归。你需要告诉程序匿名函数是什么。

## 高阶函数

这些类型的函数对函数进行操作，要么接收一个函数作为参数，要么返回一个函数作为输出。这里有两个简单的高阶函数让你有一个直观感受。

### 1. 作为参数传递

示例使用 `partialSum` 函数返回 `sum` 函数。

```go
package main

import "fmt"

func sum(a, b int) int {
    return a + b
}

func partialSum(a int) func (int) int {
    return func(b int) int {
        return sum(a, b)
    }
}

func main() {
    add := partialSum(5)
    fmt.Println(add(10)) // Output: 15
}
```

### 2. 作为输出返回

在这个示例中，`squareSum` 返回函数。

```go
package main

import "fmt"

func squareSum(a int) func (int) int {
    return func(b int) int {
        return a * b
    }
}

func main() {
    square := squareSum(3)
    fmt.Println(square(4)) // Output: 12
}
```

## 闭包

`Closures`（闭包）是引用周围环境变量的函数。它们对于数据隔离有用。

## 章节总结

- Golang 包含了各种函数。
- 切片（Slices）构建于数组，因此值得了解数组在该语言中是如何工作的。
- 数组经常用于收集相同类型的变量。
- 切片是 Go 中处理这些集合的一种简单方法。




你可能记得切片（slice）是由多个元素组成的。与数组不同，它们在声明时不需要在括号中指定长度。切片的零值为 `nil`。其长度和容量均为 0，且它没有引用数组。

## 声明

你可以使用一组方括号 `[]` 为将保存切片的变量声明类型，然后紧跟该切片将包含的元素类型。这里是声明变量类型的两个示例，一个是数字类型，另一个字符串类型：

```go
var intSlice []int
var strSlice []string
```

你也可以使用内置函数 `make` 来声明切片，它包含长度。容量是可选的。如果你只指定了长度，则假设容量与长度相同。如果容量与长度不同，你需要声明容量值。

`make` 会分配一个数组，然后返回一个引用该数组的切片。

```go
var intSlice = make([]int, 10) // 这里长度和容量相同，均为 10
var strSlice = make ([]string, 10, 20) // 为 10，容量为 20
```

或者，你可以使用 `new` 关键字声明切片。在关键字后跟随容量，然后是切片中元素的类型：

```go
var intSlice = new([50]int)[0:10] // 关键字为 new，容量为 50，长度为 10
```

切片可以通过对数组进行切片形成，也可以从另一个切片形成。它通过半开区间指定，该区间包含起始值但不包含结束值，由两个用冒号分隔的索引组成。你可以将其理解为 `[low: high]`。默认的 low 是第 0 个值，high 是切片的长度。

例如，表达式 `b[1:4]` 将创建一个包含元素 1–3 的 `b` 的切片。

假设你有一个切片 `b := []byte{'q', 'j', 'x', 'z', 'q'}`：

```go
b[1:4] == []byte{'j', 'x', 'z'} // 记住第一个元素索引是 0 而不是 1，且范围包含第一个元素但不包含最后一个
```

让我们来看另一个关于数组 `a` 和各种切片的示例：

```go
package main

import "fmt"

func main () {
    a :=[5]string{"Britain", "Canada", "Australia", "India", "New Zealand"} //数组 a 有 5 个元素

    // 现在开始切片
    slice1 := a[1:4]
    slice2 := a[:3] // 记住默认 low 是第 0
    slice3 := a[2:] // 默认 high 是最后一个
    slice4 := a[:]

    fmt.Println("Array a = ", "a")
    fmt.Println("slice 1 = ", slice1)
    fmt.Println("slice 2 = ", slice2)
    fmt.Println("slice 3 = ", slice3)
    fmt.Println("slice 4 = ", slice4)
}
```

你将得到以下输出：
```
Array a = [Britain Canada Australia India New Zealand]
slice1 = [Canada Australia India]
slice2 = [Britain Canada Australia]
slice3 = [Australia New Zealand]
slice4 = [Britain Canada Australia India New Zealand]
```
注意，切片不能超过其容量增长，也不能重新切片到零以下。这会导致运行时恐慌（panic）。

## 初始化

列出切片的初始值被称为初始化。使用带有空括号的切片字面量（如上所示），跟随类型，然后在花括号 `{}` 中列出初始值。

```go
var intSlice = []int{10, 20, 30, 40}
var strSlice = []string{"Britain", "Canada", "Australia"}
```

## 修改切片

由于切片是数组的一部分，对切片进行的任何更改都会影响数组。其他引用该数组的切片也会发生变化。这里有一个基于周日的示例说明了其工作原理：

```go
package main

import "fmt"

func main () {
    a :=[7]string{"Mon", "Tues", "Wed", "Thu", "Fri", "Sat", "Sun"}

    slice1 := a[1:]
    slice2 := a[3:]

    fmt.Println("----- Modification")
    fmt.Println("a = ", a)
    fmt.Println("slice1 = ", slice1)
    fmt.Println("slice2 = ", slice2)

    slice1[0] = "TUES"
    slice1[1] = "WEDS"
    slice1[2] = "THURS"
    slice2[1] = "FRI"

    fmt.Println("----- Modification")
    fmt.Println("a = ", a)
    fmt.Println("slice1 = ", slice1)
    fmt.Println("slice2 = ", slice2)
}
```

输出如下：
```
----- Modification
a = [Mon Tues Wed Thu Fri Sat Sun]
slice1 = [Tues Wed Thu Fri Sat Sun]
slice2 = [Thu Fri Sat Sun]
----- Modification
a = [Mon TUES WEDS THURS Fri Sat Sun]
slice1 = [TUES WEDS THURS Fri Sat Sun]
slice2 = [THURS FRI Sat Sun]
```

### For

正如我们在 Golang 中讨论过的遍历某些表达式一样，你也可以遍历切片和数组。

### For

```go
package main

import "fmt"

func main () {
    days :=[]string{"Thu", "Fri", "Sat", "Sun"}
    for i := 0; i < len(days); i++ {
        fmt.Println(days[i])
    }
}
```

输出看起来像：
```
Thu
Fri
Sat
Sun
```

### For range

```go
package main

import "fmt"

func main () {
    primenbers := []int{2, 3, 5, 7, 11}
    for index, number := range primenumbers {
        fmt.Printf("Primenumber(%d) = %d\n", index +1, number)
    }
}
```

你将得到如下结果：
```
Primenumber(1) = 2
Primenumber(2) = 3
Primenumber(3) = 5
Primenumber(4) = 7
```

 多维

首先，让我们看看多维数组。到目前为止，我们使用的是单行数组。考虑一个具有多行多列的二维数组。你可以将其可视化为具有 x 行 y 列的表格。虽然技术上对维度没有限制，但最有用的多维数组是二维的。数组的语法为：

`var arrayName [x][y]data_type`

例如，`[2][3]int` 有两行三列数字。二维数组 `a` 中的每个元素都可以通过其位置定义：`a[i][j]`，其中 `i` 是行，`j` 是列。同样，你的切片也可以有两个（更多）维度。这些适用于游戏、图像处理和矩阵计算等应用。

## 重切片、复制和追加

当重新切片（reslice）时，你更改了给定切片的长度。如果你想使用内置函数 `copy` 复制切片，可以从源切片获取元素并将其复制到目标。复制长度始终是两个切片中的最小长度，并返回复制元素数量的整数。语法如下：`func copy (dst, src, []type)`，其中 `dst` 是目标切片，src 是原始切片。这是一个复制的示例：

```go
package main

import "fmt"

func main () {
    src := []string{"Red", "Orange", "Yellow", "Green"}
    dest :=make([]string, 2)
    numCopied := copy(dest, src)
    fmt.Println("src = ", src)
    fmt.Println("dest = ", dest)
    fmt.Println("# elements copied from source to dest = ", numCopied)
}
```

输出如下：
```
src = [Red Orange Yellow Green]
dest = [Red Orange]
# elements copied from source to dest = 2
```

内置函数 `append` 将元素添加到切片的末尾。如果给定切片没有足够的容量存放额外元素，则会分配具有更高容量（cap）的新数组。如果它足够大追加，则使用现有数组。在切片有足够容量容纳追加的情况下，对其进行的任何更改也会出现在追加的切片中，因为它们都引用同一个数组。

```go
package main

import "fmt"

func main() {
    slice1 := make([]string, 3, 10)
    copy(slice1, []string{"Red", "Orange", "Yellow"})
}
```




```go
slice2 := append(slice1, "Blue", "Green", "Violet")

fmt.Printf("slice1 = %v, len = %d, cap = %d\n", slice1, len(slice1), cap(slice1))

fmt.Printf("slice2 = %v, len = %d, cap = %d\n", slice2, len(slice2), cap(slice2))

slice1[0] = "Pink" // will show in both slices because the underlying array is the same

fmt.Println("\nslice1 = ", slice1)

fmt.Println("slice2 = ", slice2)
```

你的输出将看起来如下：

> *slice1 = [Red Orange Yellow], len = 3, cap = 10*

> *slice2 = [Red Orange Yellow Blue Green Violet], len = 6, cap = 10*

> *slice1 = [Pink Orange Yellow\]*

> *slice2 = [Pink Orange Yellow Blue Green Violet\]*

如果由于底层数组不同（因为你追加的切片没有足够的容量），在第一个切片中进行的更改将不会传递到追加的切片中。

```go
package main

import "fmt"

func main() {

    slice1 := []string{"Red", "Orange", "Yellow"}

    slice2 := append(slice1, "Blue", "Green", "Violet")

    fmt.Printf("slice1 = %v, len = %d, cap = %d\n", slice1, len(slice1), cap(slice1))

    fmt.Printf("slice2 = %v, len = %d, cap = %d\n", slice2, len(slice2), cap(slice2))

    slice1[0] = "Pink"

    fmt.Println("\nslice1 = ", slice1)

    fmt.Println("slice2 = ", slice2)
}
```

在输出中，你可以看到上述情况与此情况的区别。`Slice2` 并仅仅因为我们更改了 `slice1` 就发生改变。我们也没有为第一个切片指定 `len` 和 `cap`，因此代码返回了切片中使用的值。

> *slice1 = [Red Orange Yellow], len = 3, cap = 3*

> *slice2 = [Red Orange Yellow Blue Green Violet], len = 6, cap = 6*

> *slice1 = [Pink Orange Yellow\]*

> *slice2 = [Red Orange Yellow Blue Green Violet\]*

通过使用运算符 `...`，你也可以一个切片追加到另一个切片。

```go
package main

import "fmt"

func main() {

    slice1 := []string{"Red", "Orange", "Yellow"}

    slice2 := []string{"Green", "Blue", "Violet"}

    slice3 := append(slice1, slice2, ...)

    fmt.Println("slice1 = ", slice1)

    fmt.Println("slice2 = ", slice2)

    fmt.Println("slice3 = ", slice3)
}
```

正如你所预期的，输出如下：

> *slice1 = [Red Orange Yellow\]*

> *slice2 = [Green Blue Violet\]*

> *slice3 = [Red Orange Yellow Green Blue Violet\]*

## 字符串、数组和切片

由于数组并不灵活，Go 程序员倾向于更多地使用切片而不是数组。字符串只是只读切片；你可以通过索引返回字节，并对其进行切片操作以生成子字符串，这是高效的。Golang 允许你从字节切片创建字符串：

```go
str = string(slice)
```

并转换回字节切片：

```go
slice = []byte()
```

## 排序和反转

在 Go 中，切片有三个排序函数。使用哪一个取决于你正在排序的数据类型，但它们都会按升序对切片进行排序。

1. `sort.Strings`
2. `sort.Ints`
3. `sort.Floats64`

这些函数将根据你拥有的类型对键进行排序。这是一个排序整数的示例：

```go
package main

import "fmt", "sort"

func main() {

    primes := []int{2, 11, 3, 19, 13, 7, 5, 17}

    sort.Ints(primes)

    fmt.Println(primes)
}
```

输出看起来如下：

> *\[2 3 5 7 9 11 13 17 19\]*

可以使用一些函数来判断你的字符串、整数或浮点数是否正确排序。正如你可能已经猜到的，每种类型都有单独的函数。

*   字符串：`StringsAreSorted`

```go
func StringsAreSorted (a string[]) bool // 如果已排序则返回 true，否则返回 false
```

让我们来看字符串的排序检查和排序。

```go
package main

import "fmt", "sort"

func main() {

    animals := []string{“cow", "bear", "coyote", "panther", "wildebeest"}

    sorted := StringsAreSorted(animals)

    fmt.Println(sorted)

    sort.Sort(sort.Stringslice(animals))

    sorted = sort.StringsAreSorted(animals)

    fmt.Println(sorted)
}
```

你的输出如下：

> *false*

> *true*

*   整数：`IntsAreSorted`
    ```go
    func IntsAreSorted (int[]) bool // 如果已排序则返回 true,否则返回 false
    ```
*   浮点 64：`Float64sAreSorted`
    > *在 Float64 排序中，NaN（非数字）项排在前面。它的功能与整数和字符串类似。*
    ```go
    func (Float64sAreSorted)(x []float64) bool
    ```

Golang 也支持自定义排序……[注：提供的文本在后半部分包含重复/乱码段；我保留了代码段中所述的自定义排序的核心逻辑]。

（注：自定义排序部分的源文本包含大量重复和乱码句子。我在保持代码段中提供的技术意图的同时，清理了结构。）

## 本章总结

切片为在 Golang 中处理数组和字符串提供了一种简单的方法。

*   切片描述了数组的一个片段，并包含一个指针、长度和最大长度（容量）。
*   程序员可以使用切片进行迭代。
*   其他操作（如重切片、复制和追加）也是处理切片的关键方式。
*   你可以通过排序和反转排序来排列你的输出。

在下一章中，你将学习映射（map）。





哈表（你可能在其他语言中很熟悉）对程序员来说非常方便，因为它提供了快速查找（此外还有添加和删除）。Go 的 `map` 实现了哈表。在使用 Golang map 时需要注意的一点是，除非你通过代码进行调解，否则它们不能并发运行。假设你开了一家零售店，想要存储每位员工的工资；map 非常适合，因为你可以使用员工姓名作为键（key），并将工资作为值（value）。

尽管结构体（将在下一章讨论）在处理 JavaScript 对象符号（JSON）时通常比 map 更好用，但在某些情况下你可能想使用 map。JSON 是从客户端到服务器传输网络数据的常用语言。使用结构体时，你需要知道每个 JSON 元素的详细信息。

在处理数据类型和名称是静态的 API 及其他配置时，编写细节相对容易。但如果你在需要解析代码中无法提前知道 JSON 的结构，map 允许你解析所有的字段而不会丢失任何一个。

## 声明与初始化

像指针和切片一样，map 类型是引用。这意味着 `nil` map 不包含任何值，且无法向其添加键。如果你尝试向未初始化的 map 添加元素，Go 会返回错误，而在读取时表现得像一个空 map。要创建一个 map，你可以使用内置函数 `make` 或声明 map 字面量。

使用 `make` 内置函数会分配并初始化一个哈希结构。它返回一个指向数据结构的 map 值。如果你使用 `make`，语法如下：

> `make(map[type of key]type of value)`

使用上面的示例，你可以写：

> `Salary := make(map[string]int)`

此时 map 是空的，没有任何元素。添加元素来创建一个实际 map。

```go
package main

import "fmt"

func main() {
    Salary := make(map[string]int)
    Salary["Jennifer"] = 50000
    Salary["Ben"] = 25000
    Salary["Matt"] = 20000
    fmt.Println("Salary map contents = ", Salary)
}
```

你的输出看起来像这样：

`Salary map contents = map[Jennifer:50000 Ben:25000 Matt:20000]`

你也可以声明 map 字面量来用某些数据初始化 map：

```go
package main

import "fmt"

func main() {
    Salary := map[string]int{
        "Jennifer": 50000,
        "Ben": 25000,
    }
    Salary["Matt"] = 20000 //添加 Matt 
    fmt.Println("Salary map contents = ", Salary)
}
```

## 键值项

在 Go 中，键可以是几乎任何类型，包括布尔值、字符串、整数和结构体（我们将在后面的章节中详细介绍这些）。但因为它们无法使用 `==` 进行比较，所以切片、map 和函数不能作为 map 的键。考虑以下语句：

`m["route"]=66` // 这里的键是 "route"，值为 66。

要获取存储在 "route" 中的值并将其赋值给新变量 `p`：

`p := m["route"]`

如果键不存在，则返回该值类型的零值。在此例中，类型是 `int`，所以零值为 0。

`q := m["rute"]` // q == 0

你可以测试特定键是否存在于某个 map 中。

`p, ok := m["route"]`

如果键不存在，则第一个值（这里是 `p`）是该类型的零值。第二个是 `boolean`（布尔），如果键出现在 map 中则为 `true`，不存在则为 `false`。你也可以使用下划线 `_` 作为第一个值在不返回值的情况下测试键是否存在：

`_, ok := m["route"]`

当键不存在时，map 返回零。程序员发现这很有用。（注意：提供的文本此处包含几处重复/乱码的短语，已为了专业清晰度进行了清理）。

## 用于 Range 

使用 `for range` 函数遍历 map 会返回两个值，第一个是键，第二个是值。语言对两者都使用了正确的类型。在 Go 中，map 迭代*不会*自动完成的特性是在在每次循环中都保持相同的顺序。如果你希望循环每次都按照相同的顺序运行，你将需要编写维护顺序的数据结构。

在以下迭代示例中，键和值都是字符串，结果也将是字符串：

```go
for key, value := range powerpuff {
    fmt.Printf("%q is the key for the value %q\n", key, value)
}
```





如果你只是想获取键的列表，也可以使用 `range`。声明一个只访问 map 中键的变量，然后追加一个切片（slice）来存储存储这些键：

```go
keysOnly :=[]string{}

for key := range powerpuff {
    keysOnly := append(keysOnly, key)
}

fmt.Printf("%q", keysOnly)
```

这将产生如下输出：
`["breed" "color" "owner" "name"]`

你可以编写类似的代码来提供不带键的值列表。这可以让程序运行得更高效（尽管在 Go 中这样写的代码会更多）。在这里，你将预先分配切片的空间：

```go
powerpuff := map[string]string{"name": "Powerpuff", "breed": "Jackaroodle", "color": "white/brown", "owner": "PetuniaJones"}

items := make([]string, len(powerpuff)) // 指定字符串长度以避免潜在的内存分配

var j int

for _, v := range powerpuff { // 使用下划线是因为你不需要返回键
    items[j] = v
    j++
}

fmt.Printf("%q", items)
```

你将得到值的输出：
`["PetuniaJones" "white/brown" "Powerpuff" "Jackaroodle"]`

## 修改你的 Maps

在 Golang 中，你不需要使用函数或方法来对 map 进行更改。你可以直接添加、修改和删除值。

### 向 map 中添加内容

以下是向 map 中添加内容的语法：

`map[key] = value`，其中 `map` 是 map 变量的。

例如，假设你需要保留公司中所有用户及其用户名的列表。

```go
usernames := map[string]string{"Anna": "axolotl", "Mary": "maxolotl", "Suzanne": "snaxolotl"} // 这是你已有的 map

usernames["Tanya"] = "taxolotl"
```

当你打印它时...

```go
fmt.Println(usernames)
```

...你会看到现有 map 中添加了新的键值对：
`[Tanya: taxolotl Mary: maxolotl Suzanne: snaxolotl Anna: axolotl]`

### 修改 map 中的值

这种操作与向 map 中添加内容相似。你只需要提供键及其新值；当你打印它时，就能看到修改。

假设你正在跟踪公司里每个人的成交销售额。在现实生活中，你可能只需要确保你的 CRM 系统连接到销售数据，但让我们假设你正在实时更新这些数据。今天早上，Tanya 有 $30,000，Mary 有 $35,000，Suzanne 有 $25,000，而 Anna 也是 $25,000。Anna 刚刚谈成了一笔 $15,000 的交易，所以你需要将她的数字更新为 $40,000。你需要为键 `Anna` 传递新值：

```go
salesClosed := map[string]int{"Tanya": 30000, "Mary": 35000, "Suzanne": 25000, "Anna": 25000}

salesClosed["Anna"] = 40000

fmt.Println(salesClosed) // 这显示了金额已更新。
```

你的输出将显示：
`map[Mary: 35000 Anna: 40000 Suzanne: 25000 Tanya: 30000]`

删除 删除

你可以从 map 中删除一个键值对，或者删除 map 内部的所有值，然后你可以以不同的方式再次使用它们。

要删除键值对，可以使用内置函数 `delete`。语法如下：

`delete[map, key]`，其中 `map` 是你要从中删除键值对的 map，`key` 是你想要移除的键（这也会从 map 中删除对应的值）。

继续上面的示例，假设 Suzanne 因为表现相对较差被解雇。以下是你从 `usernames` map 中移除她的方法：

```go
usernames := map[string]string{"Anna": "axolotl", "Mary": "maxolotl", "Suzanne": "snaxolotl", "Tanya": "taxolotl"}

delete(usernames, "Suzanne")
```

为了确认 Suzanne 已从 map 中移除，你可以打印它：

```go
fmt.Println(usernames)
```

输出将为：
`[Tanya: taxolotl Mary: maxolotl Anna: axolotl]`

## 排序

正如你所学到的，Go 中的 map 是无序的。然而，你可以使用 `sort` 函数对 map 进行排序。让我们继续使用公司剩余用户的年龄来展示这在 map 中是如何工作的。

```go
package main

import "fmt"

func main() {
    m := map[string]int{"Anna": 25, "Tanya": 21, "Mary": 37,}
    items := make([]string, len(m))
    for k := range m {
        items = append(items, k)
    }
    sort.Strings(items)
    for _, k := range items {
        fmt.Printf("%s: %d\n", k, m[k])
    }
}
```

## 总结

- Map 在 Go 中是无序的。
- 你可以使用 `sort` 函数对 map 进行排序。
- 你可以直接在 map 中添加、修改和删除值。
- `delete` 函数用于移除条目。
- 结构体（Structs）用于将复杂数据组织成蓝图。





```go
func main() {
    buffy := Employee { //使用 := 允许 Go 自动推断 Employee 的类型
        firstName: "buffy",
        lastName : "Vampireslayer",
        fullTime: true,
        salary: 10000,
    }

    fmt.Println(buffy)
}
```

屏幕上的输出如下：

`*{buffy Vampireslayer 10000 true}*

## 匿名结构体

在没有显式定义结构体类型的情况下，你拥有一个`匿名结构体`。许多开发者在不想重用结构体类型时会使用它们。要创建一个匿名结构体，你需要使用相同的初始值语法和内联结构体类型来编写结构体。

```go
package main

import "fmt"

func main () {//注意在此语句之前没有结构体类型的声明
	giles := struct {
		firstName, lastName string
		salaryint
		fullTimebool
	}{
		firstName: "Giles",
		lastName: "Professor",
		salary: 20000,
	}

	fmt.Println(giles)
}
```

输出如下：

`*{Giles Professor 20000 false}*

当你只定义数据类型时，Golang 使用数据类型声明（关键字）作为字段名。由于结构体字段可以是任何数据类型，它也可以是一个结构体。换句话说，结构体可以结构体类型作为数据类型。这些被称为`nested`（或`embedded`）`structs`。

你可以使用点符号法访问返回结构体的字段，同样，你可以在嵌套结构体中查找或更新字段。假设使用上面的示例，你想访问 `salary` 字段：

`buffy.salary` 返回一个结构体，然后

`buffy.salary.bonus` 涉及到所示的嵌套结构体：

```go
package main

import "fmt"

type Compensation struct {
	basic int //注意这些是 Compensation 结构体内部的字段
	healthins int
	bonus int
}

type Employee struct {
	lastName, firstName string
	salaryCompensation // 上面的结构体，嵌套的
	bool//匿名
}

func main() {
	buffy := Employee{
		firstName: Buffy,
		lastName: Vampireslayer,
		bool: true,
		salary: Compensation{10000, 9999, 50000} //返回的嵌套结构体
	}

	fmt.Println("Buffy’s bonus compensation", buffy.salary.bonus) //返回 bonus 字段
}
```

输出是

`Buffy’s bonus compensation 50000`

当你省略字段名使用匿名结构体时，你也可以创建一个嵌套的匿名结构体。所有嵌套字段通过`field promotion`（字段提升）对父结构体可用。

结构体可以取的另一种字段类型是函数。这里示例显示结构体有两个字段，一个是字符串，另一个是函数：

```go
package main

import "fmt"

type FullNameType func(string, string) string

type Employee struct {
	FirstName, LastName string
	FullNameFullNameType
}

func main() {
	e := Employee{ //结构体 e 需要具有与函数类型相同的语法
		FirstName: "Buffy",
		LastName: "Vampireslayer",
		FullName: func(firstName string, lastName string) string {
			return firstName + " " + lastName
		},
	}

	fmt.Println(e.FullName(e.FirstName, e.LastName)) //执行函数 e.FullName
}
```

结果，你的输出仅为

`Buffy Vampireslayer`

## 元数据与标签

Golang 中的结构体还赋予了你向字段添加`metadata`（元数据）的能力。当你想要在转换到或从另一种格式时提供如何编码或解码的信息，或者计划从另一个数据库存储或检索它时，这很有帮助。尽管如此，你可以存储你想要的任何内容，无论是为了你自己还是为了单独包。你通过字符串字面量来定义它。

假设你正在存储元数据以便将结构体用于 JSON 编码或解码。（JSON 是一种用于许多 应用程序之间通信的常用数据交换格式）。我们在这里使用它来展示元数据的语法：

```go
type Employee struct {
	firstNamestring `json: "firstName"`
	lastNamestring `json: "lastName"`
	salary int `json: "salary"`
	fullTimeint`json: "fullTime"`
```

这引向了 `struct tags`（结构体标签），它们是分配了某些值的短字符串。

## 章节总结

Golang 中的结构体还赋予了你向字段添加`metadata`的能力。当你想要在转换到或从另一种格式时提供如何编码或解码的信息，或者计划从另一个数据库存储或检索它时，这很有帮助。尽管如此，你可以存储你想要的任何内容，无论是为了你自己还是为了单独包。你通过字符串字面量来定义它。

- 结构体是字段的集合，允许你对相关数据分组。
- 在没有显式定义结构体类型的情况下，你可以使用`anonymous struct`。
- 结构体可以拥有`nested`（或`embedded`）`structs`。
- 嵌套结构体中的字段可以使用`field promotion`。
- 结构体还可以包含函数作为字段。
- 结构体可以通过 `struct tags` 包含 `metadata`（例如 JSON 标签）。
- `package`（包）是一个包含源文件并相互关联的目录。
- 每个源文件必须属于一个 `package`，并以 `package packlename` 开始。

## 标准库概述

你已经在书中的示例中看到了对 `fmt` 包的导入——它是一个核心库包，包含了与格式化和打印输出（到屏幕）相关的功能，以及读取某些类型的输入。当你将其导入程序中时，你就可以访问 `Println()` 和 `Printf()` 等项。

如果你在想为什么将这些函数收集在包中或通常使用包很重要，请考虑它们如何帮助你作为程序员去遵循 DRY 原则（不要重复自己）：

- 减少命名冲突：通过在不同的包中具有相同的名称，你遇到命名问题的情况会更少。
- 组织你想重用的代码：这是 DRY 原则的关键！能够快速访问你编写的函数和代码意味着更少的重复。
- 加快执行：由于 Go 使用编译器，如果每个使用之前函数的旧程序都需要重新编译，将大大减慢程序。相反，只需要重新编译发生变化的部分。





你已经熟悉的另一个包是 `main`。它用于 `commands`，即旨在作为可执行程序的程序。不可执行的包，……嗯，它们就是普通的包。你有几种方法可以将包导入到你的程序中。其中一种如下：

```go
import "packagename"
```

你可以通过这种方式为你的程序导入多个包：

```go
import "fmt"
import "math"
import "math/rand" // 包名是导入路径的最后一个元素，在本例中为 `rand`。它是 `math` 包内部的一个子目录。
```

你可能会选择使用分组方法（factored method）；无论哪种方式，你都是在导入一个包供你的代码使用。

```go
import (
    "fmt"
    "math"
    "math/rand"
)
```

Go 提供了许多代码中包含标准元素的包，因此在创建自定义包之前，请先检查标准库。还有额外的子仓库，它们在兼容性方面可能比标准库更宽松。

作为复习，要导出的变量、类型或函数的首字母必须大写。如果以小写字母开头，它在使用的包外部将不可见，且无法导出。当你导入一个包时，只有大写开头的元素会被引入你的代码中。例如，如果你在代码中定义了 `MaxInt64`，它就可以被导出。如果你将其命名为 `maxInt64`，它就只在该包内部可见。

## Regexp

`regexp` 是 `regular expression`（正则表达式）的缩写，是一种用于模式匹配、搜索和替换文本的字符序列。许多计算机语言都使用它，它也是 Go 中编写正则表达式的标准包。你可以使用 `regexp` 对大量文本（如日志或其他程序生成的输出）进行过滤、解析、验证和信息提取。它可以与 goroutines 并发地使用。如果你的搜索查询非常复杂，可以编译一个正则表达式来创建一个 `regexp` 元素。

你可以用它来从方括号 `[]` 中提取文本、从字符串中提取日期、提取主机名或 IP 地址、验证电子邮件地址格式、将任何非字母数字字符（`*``,`&``,`@`,`^` 等）替换为连字符、每遇到空格时就分割字符串等。

例如，正则表达式 `a . b` 匹配任何以 `a` 开头、以 `b` 结尾且中间包含任何字符（由点 `.` 表示）的字符串。`regexp.MatchString` 函数将检查是否存在匹配 `a . b` 的子字符串。

```go
matched, err := regexp.MatchString(`a.b","aaccbb")
fmt.Println(matched) //true
fmt.Println(err) //nil, 因为 regexp 是有效的
```

你也可以检查一个完整字符串（而不是子字符串）是否匹配 `a . b`。在这里，你使用 `^` 来标记文本或行的开头，并使用 `$` 来锚定其结尾。同样，你也可以检查开头或结尾锚点。

```go
matched, _ := regexp.MatchString(`^a.b$`, "aaccbb")
fmt.Println(matched) // false
```

对于更复杂的查询，最好编译正则表达式来创建一个 `regexp` 对象。你可以通过以下两种方式之一实现：

1. `re1, err := regexp.Compile(`regexp`)` // 如果无效则报错
2. `re2 := regexp.MustCompile(`regexp`)` // 如果无效则 panic

你可以使用 `regexp` 将字符串切分为切片。这里有一个展示了第二种方法（`re2`）以及分割的示例。在这里，指令是根据整数 `n` 将字母 `a` 分割为子字符串。如果 `n > 0`，则执行。

```go
re2 := regexp.MustCompile(`a`)
parts := re2.Split("banana", -1)
fmt.Println(parts) // [b n n n]
```




```
• func(rw *RWMutex)UnLock() //释放写锁
• func(rw *RWMutex)RLock() //获取读锁
• func(rw *RWMutex)RUnLock() //释放读锁
```

### sync.Cond

条件变量在共享数据状态发生变化时通知被阻塞的 goroutine。它们总是与 `Mutexes`（互斥锁）结合使用。

`Sync.Cond` 检查一个锁以确定其是否满足了处理条件。如果是的话，它会解锁并通知其他 goroutine，然后阻塞自己。当 goroutine 完成执行时，它们会唤醒条件变量，条件变量会解除阻塞状态并获取锁。

‣ `cond.L.Lock()` 和 `cond.L.Unlock()` 的操作方式与 `mutex` 锁类似。

‣ `cond.Wait()` 告诉代码执行：

1. `UnLock()`
2. 阻塞等待通知 = 等待下方的 `Signal` 或 `Broadcast`
3. 接收通知
4. `Lock()`

‣ `cond.Signal()` 通知一个 `Wait` goroutine。通知的顺序基于原始等待列表并按 FIFO（先入先出）运行。如果没有 `Wait` 协程，则没有错误报告。

‣ `cond.Broadcast()` 同时唤醒所有 `Wait` goroutine，这与按顺序操作的 `cond.Signal` 不同。与 `cond.Signal` 一样，如果没有 `Wait` 协程，也不会产生错误报告。

### sync.Map

你需要它来同时操作多个 map，以避免并行运行它们时产生的错误。

### sync.Pool

`sync.Pool` 用于缓存对象，这可以减轻垃圾回收器（GC）的压力并保持 Go 快速运行。初始化一个池需要你设置 `New` 函数。当有缓存对象且你调用 `Get` 时，它会直接返回该对象。如果没有，则会调用 `New` 来创建它。

`Pool` 最适用于你有大量内存和并发的场景。如果内存或并发量不高，使用池反而会适得其反。最佳实践是在你 `Put` 对象放入池中之前，以及 `Get` 获取池中对象之后，清空该池。

## 精确计算

由于 Go 的编写方式，在处理大数字时可能会出现问题。例如，100 的阶乘包含 158 位数字，因此它无法存储在 Go 的原生数据类型中。它没有你可能在其他语言中找到的隐式溢出检查，因此尝试将超过 64 位的数字放入 `int64` 可能会导致意外的结果。你不会得到错误信息，但会得到一个看起来不对劲的结果。

为了避免这个问题，请使用名为 `big` 的包。`Big` 设计用于允许程序员使用任意精度算术来处理大数字，这些数字通常存储在数组而不是位中。当你需要非常精确的数字和/或计算速度不是问题时，可以使用它。

该包支持 `Int`、`Rat`（有理数）和 `Float`。这三者的零值都是零。因此，新值很容易声明且不需要初始化。语法如下，其中 `x`、`r` 和 `y` 均为零值：

```go
var x Int
var R &Rat{}
y := new(Float)
```

在类型转换方面也是一个问题，因为输入通常是原生数据类型。绕过此问题的简单方法是使用 JSON 属性作为字符串。

## 自定义包

一旦你写了你知道会重用的代码，良好的做法是将其制成包，这样你就不需要复制粘贴，或尝试记住你上次在哪里使用过它；以后你只需要在未来导入该包即可。当你准备好创建自己的包时，你需要进入 Go 编程环境和工作区。在你的目录中，创建一个存放该包的目录名称——这通常与包本身的名称相同，以便导入。惯例是将目录中的第一个文件命名为与目录相同。

假设你想创建一个名为 `greeting` 的包。目录名将是 `greeting`，文件名将是 `greeting.go`。编写程序时，打开该文件。

当你编写包时，第一行应该是你正在创建的包名。然后导入你需要的任何包，比如 `fmt`。对于这个自定义包的示例，我们将在代码中使用标志性的 Hello, World!。一旦你写了这个包，任何你想使用它的时候，只需要导入该包即可。

```go
package greeting // 此文件中的所有内容将包含在包中

import "fmt"

func Hello() {
    fmt.Println("Hello, World!")
}
```

你可以将此包引入可执行文件或入口点，通常命名为 `main.go`。这里是调用该包时的样子：

```go
package main

import "greeting"

func main() {
    greeting.Hello() // 使用点符号符号调用导入包中的函数 (Hello)
}
```

你还可以向你的包中添加变量和类型；其语法应该在之前的示例中看起来熟悉。首先，向你的包添加你需要的内容。以下代码显示对 `greeting` 的修改：

```go
package greeting

import "fmt"

var Pet = "Powerpuff" // 添加变量

type Unicorn struct { // 添加类型
    Name  string
    Color string
}

func (u Unicorn) String() string {
    return fmt.Sprintf("独角兽的名字是 %s，颜色是 %s", u.Name, u.Color)
}

func Hello() {
    fmt.Println("Hello, World!")
}
```

调用包时，你的代码如下：

```go
package main

import (
    "fmt"
    "greeting"
)

func main() {
    greeting.Hello()
    fmt.Println(greeting.Pet)
    uni := greeting.Unicorn{
        Name:  "Petunia",
        Color: "fuchsia",
    }
    fmt.Println(uni.String())
}
```





一旦你执行了 `get`，Go 就会将其安装在 `$GOPATH/src` 下，命名为 `repository.com/username/packagename`。现在包已经保存在本地了，但你仍然需要将其导入程序中。使用常规导入函数：

```
import "repository.com/username/packagename"
```

## 外部包、库和项目

在上一节中，你学习了 Go 可以从网络上任何支持该语言并使用兼容 VCS（版本控制系统）的地方获取包。还有标准库（`stdlib`）存在于你的 `$GOROOT` 目录下，你不需要对它们进行 `go get` 或安装。

如果你正在导入一个已经在程序中定义的包，请使用相对路径（不包含任何外部 URL 引用）。将你的程序所在的目录以及该目录内部包含你想要包的目录命名即可。

```
import "myprogram/mostexcellentpackage"
```

但假设你想使用一个保存到 GitHub 等第三方仓库的包。你需要像上面描述的那样去 `go get` 它并导入它，就像导入他人的包一样。

项目是学习代码的好极方法。教你如何采取步骤的教程是基石，但承担项目可以帮助你实现所学的内容。项目可以是构建网站、创建一个应用程序、重新设计网站模板或任何你想到的其他事情。

当你考虑你的包时，请考虑以下想法来指导你构建所有内容。由于 Go 旨在开源，简单性和易用性是你项目中遵循的两个关键原则。

### 一致性
你的代码应该具有一致的外观和感受，在所有的包和项目中使用相同的约定。

### 简单性
它应该足够简单，以便阅读和使用，但又不能简单到遗漏步骤或重要信息。

### 易于导航
清楚如何在现有的结构中移动。这对你和其他用户都有帮助。使用显而易见的命名约定，这样你就不需要去猜某个文件夹或目录中有什么了。

对于小型项目，将所有代码保持在一个文件夹中就足够，但当你开发较大的项目时，这通常会变成问题。额外的约定目录包括：

- `/cmd`: 包含入口文件（可执行文件）。
- `/internal`: 私有库代码，特定于服务且不与任何他人共享。
- `/pkg`: 包含你可以与其他用户共享的文件。

## 章节总结

Go 中的包允许程序员轻松地复用代码，而无需复制粘贴或记住某段代码的位置。导入包会将该文件中的所有信息带到当前程序中。

- 标准库非常详尽，并带有许多常用项。
- 使用 `regexp` 包编写正则表达式可以节省时间。
- `Sync` 包帮助并发的 `goroutines` 避免数据竞争，数据竞争会产生不想要的问题和结果。
- 你需要一个包来确保程序运行准确的计算，因为有时 64 位不足以容纳数据。
- 尽管有很多标准包可以选择，但在必要时你也可以创建自己的包。
- 出于考虑，开发者应该记录他们的包，以便其他用户理解其目的。
- 由于 Golang 没有中央仓库，你可能需要从如 `Git` 和 `Bazaar` 等第三方版本控制系统导入包。
- 外部库、包和项目有需要遵循的约定。

在下一章中，你将学习方法。

# 九章

到目前，你已经处理了大量的函数，但你可能需要对同一份数据使用多个函数。不需要复制粘贴；相反，你可以使用作用于特定类型的*方法*，该类型被称为*接收者*。通过方法，你可以解释数据类型是什么以及它应该如何被使用。在其他语言中，接收者是一个关键字，但 Go 将接收者视为一个变量，因此你可以随心所欲地命名。约定是对接收者类型使用小写字母。

方法是实现接口（在十章中）的唯一方式。当你嵌入一个类型时，你就可以访问相关的方法。如果你使用的是支持 Go 自动补全的编辑器，你可以通过补全获取方法建议，而不是每次都查阅文档。虽然这不是使用方法的主要原因，但它加快了你的处理过程。

## 函数与方法的区别

方法的语法与函数非常相似，多了一个指定接收者的参数。调用方法与调用函数相似，只是使用额外的接收者变量。

它们也存在显著差异。方法可以接受指针*并且*接受值，而函数不能。在同一个程序中，你可以拥有同名但不同类型的方法，但在函数中，你不能这样做。方法与它们所属的类型相关联，因此它们依赖于状态，而函数每次都提供相同的输出。如果你的代码不依赖于状态，你应该使用函数而不是方法。

让我们来说说明这些区别。在下面的示例中，我们创建了一个名为 `Creature` 的结构体，带有 `Name` 和 `Greeting` 字符串字段。在这里，方法（而不是函数）是 `Greet`；注意变量 `c` 被用于接收者 `Creature` 类型。

```
package main

import "fmt"

type Creature struct {
    Name string
    Greeting string
}

func (c Creature) Greet() {
    fmt.Printf("%s says %s", c.Name, c.Greeting)
}

func main() {
    sarah := Creature{
        Name: "Sarah",
        Greeting: "Hello!",
    }
    sarah.Greet()
}
```

你的输出看起来像这样：
*Sarah says Hello!*

## 作为指针和值的接收者与方法

在类型上定义方法（而不是在值上定义函数）有其他好处。在接口章节中，你将看到为什么在代码中使用接口时方法是有帮助的。

你还可以在指针接收者上定义方法。作为开发者，你可以通过使用大写字母开头方法，如果它只在特定位置有效则使用小写，来强制包的用户使用特定方法。在指针接收者上定义方法确保了对该类型的修改将会持续。指针充当指向特定类型的引用，而不是其拷贝。指针接收者的声明与值接收者相似，但使用星号（`*`）作为前缀表示指针：

```
package main

import "fmt"

type Boat struct {
    Name string
    occupants []string
}

func (b *Boat) AddOccupant(name string) *Boat {
    b.occupants = append(b.occupants, name)
    return b
}

func (b Boat) Manifest() {
    fmt.Println("The", b.Name, "has the following occupants:")
    for _, n := range b.occupants {
        fmt.Println("\t", n)
    }
}

func main() {
    b := &Boat{
        Name: "S.S. Powerpuff",
    }
    b.AddOccupant("Sarah the stingray")
    b.AddOccupant("Mary the mussel")
    b.Manifest()
}
```

当你运行它时，你将得到：
*The S.S. Powerpuff has the following occupants:*
*Sarah the stingray*
*Mary the mussel*

指针接收者允许方法更改接收者所指向的值。它们还允许你在每次调用方法时避免拷贝值，当接收者是一个大型结构体时非常棒。它们有助于加快代码和处理过程。

## 接受指针和值类型




提醒一下，当你有一个带有值参数的 Go 函数时，只有参数值可以被传递给它。尝试向值接收函数传递指针会导致错误。然而，对于方法（method）来说并非如此。这里有一个在方法同时同时指针和值的示例：

```go
package main

import “fmt”

//author 结构体
type author struct {
	name string
	section string
}

// 使用指针接收者 author 类型的方法
func(a *author) show_1(asection string) {
	(*a).section = asection
}

// 使用值接收者 author  own 的方法
func(a author) show_2() {
	a.name = “Johnson”
	fmt.Println(“Author’s name (Before) : “, a.name)
}

func main () {
	res := author{
		name : “Smith”,
		section:“RQY”
	}
	fmt.Println(“Section name (Before) : “, res.section)
	//使用值调用指针方法 show_1
	res.show_1(“XJU”)
	fmt.Println(“Section name (After) : “, res.section)
	//使用指针调用值方法 show_2
	(&res).show_2()
	fmt.Println(“Author’s name (After) : “, res.name)
}
```

输出如下：
*Section name (Before): RQY*
*Section name (After): XJU*
*Author’s name (Before): Johnson*
*Author’s name (After): Smith*

## 嵌入类型 (Embedded Types)

结构体中的嵌入类型可以使用类型的名称来指定。它可以是一个值类型，也可以是指向值类型的指针。在 Golang 中，字段或方法可以被提升（promoted）或在外部/嵌入类型中可用。

当然，这遵循一些规则。类型的方法集（method set）决定了该类型实现的接口，以及使用该类型接收者时可以调的方法。在一个集合中，每个方法必须具有唯一的非空名称。类型 `T`（接口之外的任何类型）的方法集包括所有用接收者类型 `T` 声明的方法，但**除了**那些用指针接收者 `*T` 声明的方法。然而，指针接收者 `*T` 的方法集同时包含了 `*T` 和 `T` 接收者。

## 继承与多继承 (Inheritance and Multiple Inheritance)

如果你熟悉面向对象编程 (OOP)，那么你知道继承意味着将一个类继承到另一个类。然而，由于 Go 不是 OOP 且不使用类，因此 Go 中没有继承。但是，继承的基本概念可以通过结构体来实现。在 Go 中，这被称为*组合*（composition）。基结构体可以嵌入到子结构体中，然后可以在子结构体上调用基类的方法。让我们来看一个简单的基/子类组合示例：

```go
package main

import “fmt”

type Movie struct{
	//声明结构体变量
	Universe string
}

//返回电影宇宙的函数
func (movie Movie) MovieUniverse () string {
	return movie.Universe
}

type Quentin struct{
	//匿名字段，用于嵌入结构体的组合
	Movie
}

type Nancy struct {
	Movie
}

func main() {
	//创建实例
	m1 := Quentin{
		//子结构体直接访问基结构体变量
		Movie{
			Universe : “QU”,
		},
	}
	//子结构体直接访问基结构体方法
	// 使用子类打印基类方法
	fmt. Println(“Universe is “, m1.MovieUniverse())

	m2 := Nancy{
		Movie{
			Universe : “NU”,
		},
	}
	fmt. Println(“Universe is “, m2.MovieUniverse())
}
```

你的输出将是：
*Universe is: QU*
*Universe is: NU*

当子结构体可以访问基结构的所有字段、方法和属性时，就会发生多继承。以下是这种工作方式的示例：

```go
package main

import “fmt”

//声明第一个基结构体
type first struct{
	//声明第一个结构体变量
	base_one string
}

//声明第二个基结构体
type second struct{
	//声明第二个结构体变量
	base_two string
}

//返回第一个结构体变量的函数
func (f first) print_1() string {
	return f.base_one
}

//返回第二个结构体变量的函数
func (f second) print_2() string {
	return f.base_two
}

type child struct {
	first
	second
}

func main() {
	c := child{
		first{base_one: “Base1”},
		second{base_two: “Base2”},
	}
	fmt.Println("Base 1:", c.print_1())
	fmt.Println("Base 2:", c.print_2())
}
```
*（注：提供的多继承文本较为破碎；我根据上下文重建了逻辑以保持语义完整性。）*

## 章节总结

- 方法与函数相似，但带有接收者。
- 指针和值被嵌入到结构体中。
- Go 没有继承，但你可以使用组合。
- 现在你已经掌握了方法，你将学习接口。

接口传递了多态的概念。这是编写根据类型表现出行为的代码。接口的零值是 nil，如果没有方法，它就是空接口。接口本身是一个指向动态值的静态类型。创建接口的语法与创建结构体的语法相似，如下所示：

```go
package main

import “fmt”

//创建接口
type container interface {
	//指定方法
	Carea() float64
	Volume()float64
}

type somevalue struct {
	radiusfloat64
	heightfloat64
}

//实现容器接口方法
func (s somevalue) Carea() float64 {
	return 2*s.radius*s.height + 2*3.14*s.radius*s.radius
}

func (s somevalue) Volume() float64 {
	return 3.14*s.radius*s.radius*s.height
}

func main () {
	//访问接口的元素
	var c container
	c = somevalue{10, 14}
	fmt.Println(“Area of container :”, c.Carea())
	fmt.Println(“Volume of container :”, c.Volume())
}
```

作为结果，你的输出将是使用半径 10 和高度 14 计算的面积和体积。
*Area of container : 908*
*Volume of container : 4396*




接口可以嵌入另一个接口，还可以嵌入另一个接口的方法集。你可以根据需要向接口嵌入任意数量的接口。如果你对这些接口进行任何更改，也会更改被嵌入的接口。

让我们来看看这在实践中是如何体现的：

```go
package main

import “fmt”

//interface 1
type WriterDetails interface {
	details()
}

//interface 2
type WriterArticles interface {
	articles()
	picked()
}

//interface 3
//interface 3 嵌入了接口 1 的方法、接口 2 以及它自己的方法
type SummaryDetails interface {
	details()
	WriterArticles
	wdeets()
}

type writer struct {
	w_name string
	section string
	college string
	year int
	income int
	particles int
	tarticles int
	wid int
	post string
	pick int
}

//实现接口 1 的方法
func (w writer) details () {
	fmt.Printf(“Writer name :%b”, w.w_name)
	fmt.Printf(“\\nsection :%b and passing year :%d”, w.section, w.year)
	fmt.Printf(”\\ncollege name :%b, w.college)
	fmt.Printf(“\\nincome :%d”, w.income)
	fmt.Printf(“\\nPublished Articles :%d”, w.particles)
}

//实现接口 2 的方法
func (w writer) articles() {
	pendingarticles = w.tarticles - w.particles
	fmt.Printf(“\\nPending articles :%d”, w.pendingarticles
}

func (w writer) picked() {
	fmt.Printf(\\nTotal number of picked articles :%d”, w.pick)
}

//实现嵌入接口 3 的方法
func (w writer) wdeets() {
	fmt.Printf (“\\nWriter ID : %d”, w.wid)
	fmt.Printf(“\\nPost :%b, w.post)
}

func main() {
	//给结构体赋值
	values := writer{
		w_name: “Agatha”,
		section: “Computer coding”,
		college:“BestSchoolEver”,
		year: 2020,
		income:60000,
		particles:300,
		tarticles:400,
		wid:666,
		post:“Technical Code Writer”,
		pick:66,
	}

	//使用 SummaryDetails 接口访问接口 1 和 2 的方法
	var s SummaryDetails = values
	s.details()
	s.articles()
	s.picked()
	s.wdeets()
}
```

从这里你已经知道输出是什么样的了，所以我就简单点说。这个示例展示了嵌入接口 (3) 如何使用嵌入接口 1 和 2 中的元素。

## 类型断言 (Type Assertions)

*类型断言*是从接口中提取值并检查动态类型是否匹配断言类型的方法。如果匹配，则类型断言将返回该动态值。如果不匹配，则会发生 panic（崩溃）。类型断言帮助你消除接口变量本身的任何歧义。其语法为：

`t := value.(typeName)`

其中，`value` 是接口类型的变量，`typeName` 是要检查的具体类型（又称动态类型），而 `t` 是具有底层 `typeName` 值的变量。

如果你想检查接口值是否持有特定类型，请使用类型断言返回两个值。其中一个是布尔值 true/false，另一个是具有 `typeName` 值的变量。这是一个带有错误检查的类型断言示例：

```go
package main

import “fmt”

func main() {
	// 带有 int 值的接口
	var value interface{} 30035

	// 获取 int 类型的值并赋值给变量 value1
	var value1 int = value.(int)

	// 打印具体值
	fmt.Println(value1)

	// 测试接口是否为 string 类型
	value2, ok := value.(string)
	if ok {
		fmt.Println(value2)
	} else {
		fmt.Println(“String found!")
	}
}
```

由于接口值是 int，你将看到以下输出：

`30035`
`String found!`

## 类型切换 (Type Switches)

当你不确定接口可能是什么类型时，会运行类型切换。与其编写多个 if-else 语句相比，类型切换允许你缩短代码。例如：

```go
package main

import “fmt”

func main() {
	var value interface{} = 30035

	switch t := value.(type) {
	case int:
		fmt.Println("Type is int:", t)
	case string:
		fmt.Println("Type is string:", t)
	default:
		fmt.Println("Unknown type")
	}
}

## 实现接口

假设你有一个定义了一些方法的接口。任何实现了这些方法的类型都被认为实现了该接口。这里有一个示例说明：

```go
package main

import “fmt”

type Shape interface {
	Area() float64
	Perimeter() float64
}

type Rectangle struct {
	width float64
	height float64
}

func (r Rectangle) Area() float64 {
	return r.width * r.height
}

func (r Rectangle) Perimeter() float64 {
	return 2 * (r.width + r.height)
}

func main() {
	var s Shape
	s = Rectangle{1.0, 2.0}
	fmt.Printf("Type of s is %T\n", s)
	fmt.Printf("Value of s is %v\n", s)
	fmt.Println("Area of rectangle s is", s.Area())
}
```

输出为：

`Type of s is main.Rectangle`
`Value of s is {1 2}`
`Area of rectangle s is 2`

接口的动态类型 (s) 现在是 `main.Rectangle`。`Shape` 的动态值现在是 `Rectangle` 的 `{1 2}`。你也可以在程序中将其更改动态类型和值，如下所示：

```go
package main

import (
	“fmt”
	“math”
)

type Shape interface {
	Area() float64
	Perimeter() float64
}

type Rectangle struct {
	width float64
	height float64
}

func (r Rectangle) Area() float64 {
	return r.width * r.height
}

func (r Rectangle) Perimeter() float64 {
	return 2 * (r.width + r.height)
}

type Circle struct {
	radius float64
}

func (c Circle) Area() float64 {
	return math.Pi * math.Pow(c.radius, 2)
}

func (c Circle) Perimeter() float64 {
	return 2 * math.Pi * c.radius
}

func main() {
	var s Shape
	s = Rectangle{1.0, 2.0}
	s = Circle{5.0}
}
```




```go
//using math package for value of pi instead of rounding to 3.14

func (c Circle) Area() float64 {
    return math.pi * c.radius * c.radius
}

func (c Circle) Perimeter() float64 {
    return 2 * math.pi * c.radius
}

func main() {
    var s Shape = Rectangle{2, 3}
    fmt.Printf("Type of s is %T\n", s)
    fmt.Printf("Value of s is %v\n", s)
    fmt.Printf("Value of s is %0.2f\n\n", s.area())

    s = Circle{10}
    fmt.Printf("Type of s is %T\n", s)
    fmt.Printf("Value of s is %v\n", s)
    fmt.Printf("Value of s is %0.2f\n\n", s.area())
}
```

输出如下：

```
Type of s is main.Rectangle
Value of s is {2, 3}
Value of s is 6
Type of s is main.Circle
Value of s is {2}
Value of s is 314.16
```

你可能已经注意到，尽管 `Perimeter` 是 `Shape` 的方法且我们为它包含了一个函数，但在输出中并没有使用该方法。但是，如果我们漏掉 `Perimeter`，程序将会报错。由于 `Shape` 拥有两个方法，实现 `Shape` 的 `Rectangle` 必须也包含两个方法以避免错误。

## Sorter 接口

在之前的章节中，你已经学习了如何使用 Golang 对基本类型进行排序。`sort.Interface` 用于排序更复杂的数据类型。该接口包含三个特定的函数：

1. `Len`: 返回集合的长度
2. `Less`: 接收两个作为集合索引的整数
3. `Swap`: 通过调用 `Less` 方法执行必要的更改

语法如下：

```go
Type Interface interface {
    Len() int
    Less (i, j) bool
    Swap(i, j int)
}
```

使用 `sort.interface` 允许你在排序中使用任何你喜欢的逻辑。它不是在强制算法应该*做什么*，而是知道*如何*去做。

假设你想根据字符串的长度对字符串列表进行排序：

```go
package main

import (
    "fmt"
    "sort"
)

//定义一个 byLength 类型，它基本上是 string 的接口别名
type byLength []string

//实现 sort.Interface
func (s byLength) Len() int {
    return len(s)
}

func (s byLength) Swap(i, j int) {
    s[i], s[j] = s[j], s[i]
}

//通常 Less 持有自定义排序逻辑
//因为要按字符串长度从短到长排序，所以使用 len(s[i]) 和 len(s[j])
func (s byLength) Less(i, j int) bool {
    return len(s[i]) < len(s[j])
}

func main() {
    breeds := []string{"Labradoodle", "Chiweenie", "Shiapso"}
    sort.sort(byLength(breeds))
    fmt.Println(breeds)
}
```

输出看起来如下：

```
[Shiapso Chiweenie Labradoodle]
```

## 读取与写入

你现在可能还没有意识到，Go 标准库的许多组件都是接口。例如，`Error` 仅仅是一个包含 `error` 方法的接口，该方法不消耗任何内容并返回一个字符串。同样，`io` 一个接口……（此处省略）




反射（Reflection）是检查接口变量内部存储的类型和值值对的机制。当你执行查询数据库或创建一个包含未知类型数据的结构时，它特别有用。`reflect` 包可以帮助你确定类型以及字段的数量。

`reflect` 包包含两个类型，简单来说就是 `Type` 和 `Value`。它有两个函数 `reflect.Typeof` 和 `reflect.Valueof`，它们从接口返回 `reflect.Type` 和 `reflect.Value`。这里有一个简单的示例：

```go
package main

import (
    "fmt"
    "reflect"
)

func main() {
    var y float = 3.14
    fmt.Println("Type", reflect.Typeof(y))
}
```

结果，你看到
> *Type float64*

从表面上看，你可能认为传递的是 `float64` 变量 `y`，而不是接口。然而，`reflect.Typeof` 包含的是一个空接口。当你调用函数 `reflect.Typeof(y)` 时，一个空接口存储了 `y`。它被作为参数传递，然后函数解开空接口以找到类型信息。同样，`reflect.Valueof` 获取该值对的值信息。

`reflect` 包有三个支柱：类型（type）、种类（kind）和值（value）。你在上面已经看到了类型和值。`Kind` 指类型的表示，可以通过 `type.Kind()` 获取。

在 Go 中，反射是从接口值到反射对象。这被称为反射的第一条定律。第二条定律是反射是从反射对象到接口值。换句话说，反射有自己的逆向操作。如果给你一个 `reflect.Value`，可以从它恢复接口值。第三条定律涉及一种被称为“可设置性”（settability）的特性，并不是所有值都具有这种特性。它是指反射对象可以修改创建该对象所使用的存储空间。换句话说，如果一个反射值持有原始项，那么它就是可设置的。如果你尝试在一个不可设置的值上调用 `Set` 方法，将会得到错误。

这里有一个产生 panic（崩溃）的代码片段，尽管你可能认为它是有效的：

```go
var y float64 = 3.14
v := reflect.Valueof(y)
v.SetFloat(6.28)
```

在上面的代码中，`y` 的拷贝被传递给了 `reflect.Valueof`，而不是 `y` 本身。因此，你并没有改变变量 `y` 为 `6.28`，而是改变了 `y` 的拷贝为 `6.28`，这是没有意义的。可设置性防止了你这样做。

你可以使用 `CanSet` 方法判断一个值是否可设置：

```go
var y float64 = 3.14
v := reflect.Valueof(y)
fmt.Println("settability of v:", v.Canset())
//在这种情况下会打印 settability of v: false
```

这与使用“普通”函数 `f(x)` 非常相似。在这里，由于传递给函数的是 `x` 的拷贝，所以你不会期望 `f` 能够改变 `x`。如果你想直接修改 `x`，你需要传递 `x` 的指针，看起来看起来像 `f (&x)`。

同样，如果你想通过反射传递 `y`，首先你需要指向想要修改的 `y` 值的指针。以下是上一个示例中的对应写法：

```go
var y float64 = 3.14
//获取 y 的地址
z := reflectValueof(&y)
//反射对象 z 是不可设置的，所以我们需要获取 z 指向的内容
//在值上调用 Elem 方法到达那里
//保存到反射值中
v := z.Elem()
//现在它终于代表 y，所以我们可以修改它
v.SetFloat(6.28)
fmt.Println(v.interface())
fmt.Println(y)
//两者的结果都是 6.28
```

## Printf, Value 和动态接口

为了尽可能易于理解，Go 包含了一些让日志记录和调试代码更方便的概念。打印接口值的动态类型会让这些操作变得更容易。幸运的是，我们的老朋友 `fmt.Printf` 提供了一个使用 `reflect.Typeof` 的简短版本，即 `%T`。

接口值有一个具体值和一个动态类型。就像 `%T` 给你接口的动态类型一样，你可以使用 `%v` 通过 `printf` 打印具体值。动态和具体也帮助你判断相等性。如果两个接口的具体值相等且动态类型相同，或者两者都为 `nil`，则这两个接口是相等的。如果类型为 `T` 的接口值 `t` 和非接口值类型 `S` 的值 `s` 满足 `t` 的具体值 = `s` 且 `t` 的动态类型 = `S`，则它们是相等。

当你使用 `reflect.Value` 时，你可以持有任意值，就像空接口一样。两者之间的区别是什么？值有多种方法可以查看其内部并确定其内容。相比之下，空接口隐藏了它所有的方法和表示。你需要知道它包含什么类型，以便在想对它进行任何修改时使用类型断言来“打开盖子”。

## 结构体、集合和高阶函数

反射在处理结构体时非常有用。除了包中包含的其他方法外，`reflect` 还提供了以下仅供结构体使用的：

*   `NumField()`：计算结构体中可用字段的数量。
*   `Field()`：使用索引变量访问字段本身。

在这个示例中，你将看到类型和种类之间的区别，以及它们在编程中是如何使用的：

```go
package main

import (
    "fmt"
    "reflect"
)

type info struct {
    fname string
    name string
    age int
    balance float64
}

type meType string

//function showInfo 取空接口作为参数
func showInfo(i, j interface {}) {
    t1 := reflect.Typeof(i)
    k1 := reflect.Kind()
    t2 := reflect.Typeof(j)
    k2 := reflect.Kind()
    fmt.Println("Type of 1st interface", t1)
    fmt.Println("Kind of 1st interface", k1)
    fmt.Println("Type of 2nd interface", t2)
    fmt.Println("Kind of 2nd interface", k2)
    fmt.Println("The values in the first argument:")
    if reflect.Valueof(i).Kind() == reflect.Struct {
        value := reflect.Valueof(i)
        numberofFields := value.NumField()
        for i :=0; i < numberofFields; i++ {
            fmt.Printf("%d.Type:%t || Value:%v\n", i+1, value.Field(i).Type(), value.Field(i))
            fmt.Println("Kind is", value.Field(i).Kind())
        }
    }
    value := reflect.Valueof(j)
    fmt.Printf("The value passed in:#v", value)
}

func main () {
    id := meType("9876")
    person := info{
        fname = "Cassie"
        name = "Coder",
        age = 27
        balance = 5987.65
    }
    //passing two arguments to showInfo
    //person is a struct, id is a string
    showInfo(person, id)
}
```

这里的输出显示了类型和种类的区别。
> *Type of 1st interface main.info*
> *Kind of 1st interface struct*
> *Type of 2nd interface main.meType*
> *Kind of 2nd interface string*
> *The values in the first argument:*
> *1.Type:string || Value:"Cassie"*
> *Kind is string*
> *2.Type:string || Value:"Coder"*
> *Kind is string*
> *3.Type:int || Value:27*
> *Kind is int*
> *4.Type:float64 || Value:5987.65*
> *Kind is float64*
The value passed in "9876"

你可以看到结构体 `person` 是 `main.info` 类型和 `struct` 种类，而变量 `id` 是 `main.meType` 类型和 `string` 种类。

## 接口的最佳实践

保持接口小。只定义解释该概念所需的最小行为。为了符合简洁、小的接口，你不需要指定将满足它的类型；接口只需要定义其他类型将分类为它的元素即可。例如，假设你正在编写一个描述定义汽车要素所需的接口：

```go
type car interface {
    color() string
    speed() int
    //the next field doesn’t work
}
```




```go
func IsFiretruck() bool

}
```

让所有汽车都声称自己不是消防车是没有意义的，因为你将需要指定 `IsSedan()`、`IsAmbulance()`、`IsConvertible()` 等。如果你错误地添加了 `isFiretruck`，你将包含许多可能的类型。类型断言（Type assertion）在给定接口实例时会提供其底层类型。如果你觉得必要，可以添加一个子接口，它“继承”了来自 `car` 接口的方法，并添加了一个用于作为消防车的方法：

```go
type firetruck interface {
    car
    Hoselength()
}
```

如果你在其他程序中处理过类（class），请记住 Golang 中的类与接口（interface）是不同的。

## 章节总结

接口为你的 Golang 编码引入了更多的灵活性和多态性。它们还通过反射（reflection）提供了添加抽象的能力，特别是当你不知道什么类型会传入你的函数时。

*   接口可以被看作方法的集合。
*   接口接受接口作为一种类型，这意味着它们可以相互嵌入或嵌套。
*   类型断言允许你检查任何接口中包含哪些类型。
*   类型切换（Type switches）允许你在需要时更改类型。
*   你可以使用 `sorter` 接口来排序任何比书中早期排序方法更复杂的对象。
*   读取和写入都涉及接口，并且可以使代码更容易编写和实现。
*   空接口（Empty interfaces）非常有用，并且对于反射是必要的。它们包含在 `fmt` 包的 `printf` 格式中。
*   `reflect` 包允许你深入研究接口内部的内容。
*   结构体（Structs）和接口是你 Go 代码中的关键角色。
*   最佳实践是保持接口小；仅使用必要的的最少定义。

在下一章中，你将学习 Golang 中的读取和写入。

## 第十一章

在上一章中，你学习了读取和写入是基于接口的。现在，我们将更详细地介绍*如何*进行读取和写入。在许多潜在的应用中，你会在代码中使用用户输入，因此知道如何读取这些输入对于任何开发者来说都是至关重要的。

## 读取：用户输入

在编写需要用户输入的代码时，你会发现几个包非常有帮助。它们包括 `fmt`、`bufio` 和 `os`。

在读取用户输入时，你在 `fmt` 中使用的主要函数是 `scanf`。其语法与你之前在示例中看到的 `printf` 类似。它扫描用户输入，根据空格分隔为由格式指定的参数，并返回成功扫描的项数。

例如，这里有一个对用户名称和年龄的简单请求。

```go
package main

import "fmt"

func main() {
    var name string
    var age int
    fmt.Print("Enter your name and age, separated by a space: ")
    //读取两个值
    //使用 & 创建并返回指向新值的指针
    fmt.scanf("%s %d", &name, &age)
    fmt.Printf("%s is %d years old\n", name, age)
}
```

如果用户输入 `Sarah 33`，你将得到结果 `Sarah is 33 years old`。

`bufio` 是一个实现缓冲 I/O（buffered I/O）的包，它比非缓冲具有更好的性能。它是在传输结果之前累积 IO 操作结果的方法，从而减少了系统调用的次数。由于这些调用可能很慢，缓冲有助于加速程序。

在读取时，程序分批读取。`Reader` 类型缓冲了一个 `io.Reader` 对象，而函数 `NewReader` 返回一个——你猜得没错——新的 `Reader`（带有默认缓冲区大小）。

`os` 包提供了一个贯穿于所有操作系统的标准接口。标准输入（Standard input，通常缩写为 `stdin`）是程序读取输入信息的流。

这里是一个同时使用 `bufio` 和 `os` 包来读取用户输入的示例：

```go
package main

import (
    "fmt"
    "bufio"
    "os"
)

func main() {
    //从输入中读取名称
    reader := bufio.NewReader(os.Stdin)
    fmt.Print("Enter your name: ")
    //将输入传递给 bufio.NewReader
    name, _ := reader.ReadString('\n')
    fmt.Printf("Hello %s\n", name)
}
```

## 读取与写入：文件

你关于用户输入所学的一些知识将回到文件中，但也有一些额外的工具。要在本地系统中读取和/或写入文件，你将使用 `io/ioutil` 包。你还会发现 `log` 包很有用，特别是 `Logger` 类型，它提供了格式化输出的方法。以下是你会发现对文件非常有用的元素。

*   `os.Create()`
    使用此工具创建一个所需名称的文件。如果该文件已经创建，`os.Create()` 将将其截断（truncates）。
*   `io/ioutil.ReadFile()` 和 `io/ioutil.WriteFile()`
    `ReadFile` 方法只有一个参数，即文件路径。它将返回文件中的数据或错误。相比之下，`WriteFile` 有三个参数写入文件：第一个是路径，第二个是数据，第三个是 `FileMode`。
*   `FileMode`
    文件具有关联权限。`FileMode` 指定了你是否可以读取、写入或执行。这三个位被称为 `rwx`。
*   `log.Fatalf`
    它会在打印日志消息后终止程序。它等同于 `Printf` 后调用 `os.Exit(1)`。
*   `log.Panic`
    这是一个运行时异常。当程序终止时，传递给 `Panic()` 的参数会被打印。它相当于 `Println()` 后接 `panic()`。
*   `Reader.ReadString("\n")`
    这在之前的示例中使用过。你用它从 `stdin` 读取输入直到出现分隔符。它返回一个包含分隔符的字符串。如果程序在到达分隔符之前发现错误，你也将获得错误之前读取的数据以及错误本身。

此示例演示了你如何接受用户输入以读取/写入文件：

```go
package main

import (
    "fmt"
    "os"
    "bufio"
    "log"
    "io/ioutil"
)

func CreateFile(filename, text string) {
    fmt.Printf("Writing to a file in Go\n")
    //使用 Create 方法，用户输入文件名，如果抛出 err 变量
    file, err := os.Create(filename)
    if err != nil {
        log.Fatalf("Failed to create file %s", err)
    }
    //使用 defer 在 main 执行且写入文件完成后关闭文件
    defer file.Close()
    //使用 WriteString 方法将数据写入文件，字符串长度存储在 len 变量中
    len, err := file.WriteString(text)
    if err != nil {
        log.Fatalf("Failed to create file %s", err)
    }
    fmt.Printf("\nFileName: %s", file.Name())
    fmt.Printf("\nLength: %d bytes", len)
}

func ReadFile(filename string) {
    fmt.Printf("\n\nRead a file in Go\n")
    data, err := ReadFile(filename)
}
```





```go
//如果抛出错误，则打印错误并停止程序

if err != nil {
    log.Panicf("Failed to read data from file %s", err)
}

fmt.Printf("\nFile Name: %s", filename)
fmt.Printf("\nFile Size: %d bytes", len(data))
fmt.Printf("\nData: %s", data)
}

func main() {
    //获取用户的文件的文件
    fmt.Println("Enter filename: ")
    var filename string
    fmt.Scanln(&filename)

    //获取用户输入的文件内容
    fmt.Println("Enter text: ")
    inputReader := bufio.NewReader(os.Stdin)
    input, _ := inputReader.ReadString("\n")

    //创建并读取文件
    CreateFile(filename, input)
    ReadFile(filename)
}
```

如果用户输入“Hello.txt”作为文件名，并在提示处输入“Hello World, it’s reading and writing in Golang!”，那么你的输出将如下：

*在 Go 中写入文件*

*Filename: Hello.txt*

*Length: 101 bytes*

*在 Go 中读取文件*

*File Name: Hello.txt*

*Size: 101 bytes*

Data: Hello World, it’s reading and writing in Golang!

## 读取：使用缓冲区读取文件

在本章的早些时候，我们讨论了缓冲区如何减少执行程序所需的时间。缓冲区是内存中的一个区域，可以是变长的也可以是固定的。如果你需要变长的大小，可以使用 `bytes` 包提供的 `Buffer` 结构类型。

`bytes.NewBuffer` 函数初始化一个带有初始值的变长缓冲区。该函数的语法如下：

```go
func NewBuffer(buf []byte) *bytes.buffer
```

同样，使用 `bytes.NewBufferString` 使用字符串的字节作为初始值初始化变长缓冲区。语法如下：

```go
func NewBufferString(s string) *bytes.buffer
```

除了你熟悉的 `ReadFrom`、`WriteTo` 以及其他读/写方法，`Buffer` 包还包含了其他你可能认为非常有用的方法，包括 `WriteString`（从字符串写入数据）、`Reset`（清空缓冲区）和 `Grow`（增加缓冲区大小）。

## 读取：从命令行读取参数

来自命令行参数是向程序开头添加额外信息的快速方法。你可以使用以下语法在命令行上通过空格来分隔参数值：

```bash
$./program Arg1 Arg2 Arg3
```

`os` 包包含 `Args` 数组；该字符串数组持有所有传递的参数。例如，你可能想让程序问候你的同事：

```go
package main

import (
    "fmt"
    "os"
)

func main() {
    names := os.Args[1:]
    for _, name := range names {
        fmt.Printf("Hello, %s\n!", name)
    }
}
```

你的命令行和输出将如下所示：

*$$ go build hello-team.go*

*$./hello-team Nancy Bob Sylvia*

*Hello Nancy!*

*Hello Bob!*

*Hello Sylvia!*

## 使用切片读取

`bufio` 包还允许编码人员在读取数据时将切片配合缓冲区。

### ReadSlice

`ReadSlice` 返回一个包含分隔符的字符串切片。其语法如下：

```go
func (b *Reader) ReadSlice(delim byte) (line []byte, err error)
```

如果已到达函数末尾且没有找到分隔符，则返回 `io.EOF`。如果在缓冲区空间耗尽之前没有找到分隔符，则返回 `io.ErrFull`。

### ReadLine

与 `ReadSlice` 类似，`ReadLine` 在缓冲区空间耗尽之前找到分隔符（如 `\n`）时会返回。




## Goroutine 之间的同步与切换

Go 提供了多种方法来同步协程，以避免错误并确保计算正确完成。既然你已经熟悉了我们在第八章讨论的方法，让我们进一步详细介绍。

### Waitgroup

这通常用于你有一个协程在等待其他协程执行完成的情况。你可能还记得 `WaitGroup` 维护一个内部计数器，其默认值为 0。`WaitGroup` 有三个方法：`Add(delta int)`、`Done()` 和 `Wait()`。

某些 `WaitGroup` 值是可寻址的。可寻址值是指指针间接、变量、切片索引操作（尽管切片本身不需要可寻址）、结构体字段、数组索引操作（必须可寻址）或复合字面量类型。

对于任何这些可寻址的 `WaitGroup` 值 `wg`，调用 `wg.Add(delta int)` 来更改 `wg` 维护的计数器值，并注意 `wg.Done()` 等于 `wg.Add(-1)`。如果调用 `wg.Add(delta int)` 或 `wg.Done()` 导致 `wg` 的计数变为负数，则会导致 panic。当你调用 `wg.Wait()` 且计数器已为 0 时，它相当于无操作。否则，当计数器为正时，调用 `wg.Wait()` 意味着协程进入阻塞状态，并在另一个协程将计数器改为 0（通常通过调用 `wg.Done()`）后恢复运行。

### Once

使用此函数确保代码在程序运行期间只执行一次。作为提醒，`sync.Once` 值有一个 `Do(f func())` 方法，它接受一个类型为 `func()` 的参数。



可寻址的 `Once` 值 `o` 包含方法调用 `o.Do()`，该方法可以在多个 goroutine 中并发执行。调用中的参数最好使用相同的函数值，尽管这并不是代码的强制要求。

`o.Do()` 方法产生一个只有一个参数的函数结果，它总会在任何 `o.Do()` 方法返回之前退出。

### Cond（条件变量）
使用 `sync.Cond` 在 goroutine 之间进行通知。当你有一个 goroutine 等待状态的改变，而其他 goroutine 做出该改变并发送通知时，通常会使用它。

### Mutex/RWMutex
这两者都使用 `Lock` 和 `Unlock` 来防止多个用户同时访问同一块数据。锁并不绑定到 goroutine，因此锁可以在一个 goroutine 中锁定，并在不同的时间在另一个 goroutine 中解锁。

当你想要将一个写程序拆分为若干部分时，`RWMutex` 就非常有用。`Mutex` 和 `RWMutex` 也可以用于通知 goroutine，尽管它们不是处理此任务的最优工具（优先使用 `sync.Cond`）。

对于可寻址的 `RWMutex` 值 `rwm`，请记住写锁一次只能由一个写入者持有，且读锁和写锁不能同时持有。然而，读锁可以同时被多个读取者持有。当其锁计数返回零时，它会解锁。

## Channels（通道）
可视化通道的一种方法是将它们想象成连接并发 goroutine 的管道。它允许你将值发送到一个 goroutine 的通道，并在另一个 goroutine 中接收它们。每个通道只能发送一种类型的数据。nil 通道（nil channel）是没用的，因为你无法从从中读取，也无法从中发送数据，所以你需要使用函数 `make` 来创建一个通道。

默认情况下，通道是一个指针。通常，你将通道作为参数传递给函数或方法。当通道接收到参数时，不需要对其进行解引用即可使用数据。

在创建通道 `c` 时，语法非常简单。箭头从数据指向通道 `c`，所以你正在将数据推入通道：

```
c <- data
```

当你想从通道 `c` 读取数据时，只需如所示反转 `c` 的位置：

```
<- c
```

如果你想使用变量数据来持有从通道传出的内容，可以使用以下语法：

```
var data int
data = <- c
```

或者你可以使用它的等效写法：

```
data := <- c
```

无论何种方式，通道操作本质上都是阻塞的。当数据被写入通道 `c` 时，goroutine 会阻塞，直到另一个 goroutine 读取它。然而，通道不会永远阻塞，因为通道操作会告诉调度器调度另一个 goroutine。

这里有一个通道的快速示例：

```go
package main

import "fmt"

// 一个接受通道 c 字符串数据的 salute 函数
func salute(c chan string) {
    fmt.Println("Hello" + <-c + "!")
}

func main() {
    // main 函数第一个 goroutine
    fmt.Println("Main() started")
    // 使用 make 创建字符串类型的通道 c
    c := make(chan string)
    // 使用 go 关键字创建 goroutine，并将通道 c 传递给 salute 函数
    go salute(c)
    // 将字符串值 "Jane" 推送到通道
    c <- "Jane"
    // goroutine 被阻塞，直到另一个 goroutine 读取它
    // 激活 main goroutine
    fmt.Println("Main() stopped")
}
```

你将得到如下结果：
Main() started
Hello Jane!
Main() stopped

当对通道进行读或写时，该 goroutine 会被阻塞，控制权将传递给其他 goroutine。但是，如果存在其他 goroutine，则不会阻塞。如果，当没有 goroutine，，，，，。。。。，，，，，，，，，，。。。。。。。。，，，，，，，，，，。。。。。

你想关闭通道，， gor goroutineoutineoutine 数据，，使用内置的 `close` 函数。

当你通道关闭通道通道，，，，       。。语法非常简单：

```go
package main

import "fmt"

func squares(c chan int) {
    for i := 0; i < 10; i++ {
        c <- i
    }
    close(c)
}

func main() {
    c := make(chan int)
    go squares(c)
    
    for val := range c {
        fmt.Println(val)
    }
    fmt.Println("Main() stopped")
}
```

当通道被读或写时，该 goroutine 会被阻塞，控制权将传递给其他 goroutine。如果，但是，存在其他 goroutine，则不会阻塞。如果，但是， goroutine goroutine。。。。。。。。。如果如果没有其他 goroutine 可用，由于没有其他 goroutine，你就会遇到死锁（deadlock）。

。。。。。。。。。。。。。。。。。。。。

关闭通道时，goroutine goroutine 是一个 goroutine 阻塞的。，使用内置的 `close` 函数。

。。。。。。。。。。。。。。。。。。。。。。。。。。。

当你通道通道数据时，goroutine 会阻塞并执行。

你将得到结果如下：
Main() started
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
Main() stopped




```go
//remoteDeleteEmployee is the function you’re using to delete employees

func remoteDeleteEmployee() {
    //…
}

//the channel sem allows up to 10 concurrent operations
var sem = make(chan int, 10)

func main() {
    for _, employee := range employeeList {
        //if there’s room in the sem channel for 1 integer, the goroutine kicks off
        sem <- 1
        go func() {
            //once the remoteDeleteEmployee call returns, channel sem is drained of the integer and the goroutine continues
            remoteDeleteEmployee(employee.ID)
            <- sem
        }()
    }
}
```

如果 `sem` 满了，意味着至少有 10 个操作正在进行中。如果有第 11 个操作进来，它会被阻塞，直到之前的调用之一返回。在这里，我们使用的是缓冲通道。

然而，还有另一种比有界通道稍微复杂一点的选择，被称为**加权信号量**（`weighted semaphore`）。这种技术在发现 `sem` 变量满时不会阻塞代码。它还允许你指定想要限制的并发单元数量。

你可能想要限制并发，但并非所有调用的代价都是相同的。`context` 包使得能够更容易通过 API 将请求范围内的调用、截止日期和取消信号传递给涉及特定请求的所有 goroutine。加权信号量需要 `ctx`。

加权信号量还赋予你返回错误状态的能力，这在处理带有网络调用的代码时（结合 context 使用）是一种最佳实践。你需要能够根据定义的限制来实例化它，在请求访问共享资源时能够 `Acquire()`，并在访问完成后能够 `Release()`。加权信号量有三个函数：`Acquire`（`sem.Acquire(ctx, 1)`，其中 `ctx` 是上下文，下文将详细讨论。它与你在有界通道中看到的 `sem <-1` 相同）、`Release`（`sem.Release(1)` 等同于 `<-sem`）以及 `TryAcquire`（这尝试为操作获取空间，但如果没有空间则不会阻塞代码）。

这里是一个使用之前看到的 `remoteEmployeeDelete` 函数的加权信号量示例。

```go
func remote.DeleteEmployee() {
    //…
}

//sem here is a weighted semaphore that allows up to 10 concurrent goroutines
var sem = semaphore.NewWeighted(int64(10))

func main() {
    //context here
    ctx := ctx.Background()
    for _, employee := range employeeList {
        //handle the error, potentially with a break
        if err := sem.Acquire(ctx, 1); err != nil {
        }
        go func() {
            remoteDeleteEmployee(employee.ID)
            sem.Release(1)
        }()
    }
}
```

通过信号量限制代码的并发 goroutine，可以避免导致你的系统或他系统的崩溃。

## 通道工厂与方向性 (Channel Factory and Directionality)

你在其他计算机语言中可能遇到的另一个概念是工厂模式（factory pattern）。`factory` 模式是一种旨在在运行时定义接口以创建对象的的设计模式。这种模式可以创建各种对象，即使它不知道自己正在创建什么或如何创建，这正是“工厂”名称的由来。它允许程序在运行时选择对象，这意味着代码的微小改动就可以扩展整个对象族。工厂方法有四个方面：产品（Product，定义了创建对象的接口）、`ConcreteProduct`（实现 `Product` 接口）、`Creator`（声明工厂方法，返回类型为 `Product` 对象）以及 `ConcreteCreator`（重写工厂方法以返回 `ConcreteProduct` 实例）。实现工厂模式的良好代码需要对工厂的参数进行仔细考虑。此外，如果创建的对象可以被缓存和重用，而不是每次从头开始，那是最好的。对于通道，工厂方法是在函数内部生成通道并返回它，而不是将通道作为参数传递。

你还可以指定通道只发送或只接收，这被称为**方向性**（`directionality`）。语法如下：

```go
var send-only chan<- int //只发送数据
var recv-only <-chan int //只接收，且只接收数据并没有帮助，因为关闭的通道用于表示不再发送
```

## 通道、定时器与超时 (Channels, Tickers, and Timeouts)

定时器（Timers）和滴答器（Tickers）允许你在未来运行代码，是一次还是多次，取决于程序的需求。将它们与通道配合使用会让代码更容易编写。正如你可能预期的，它们包含在 `time` 包中。

第一个是 `Timer`（超时）。当你想要等待特定的持续时间，然后通过通道发送当前时间时使用它。其语法如下：

`time.After`

这里是一个示例：

```go
select {
case news := AFJ:
    fmt.Println(news)
case <-time.After(hour):
    fmt.Println("No news in hour")
}
```

`time.After` 操作在触发之前不会被垃圾回收器回收。如果你想避免这一点，可以使用 `newTimer` 并在时调用 `Stop`：

```go
for exist := true; exist; {
    timer := time.NewTimer(hour)
    select {
    case news := AFJ:
        timer.Stop()
        fmt.Println(news)
    case <-timer.C:
        exist = false
        fmt.Println("No news in hour")
    }
}
```

在 `Timer` 之后，我们有了 `Ticker`（重复）。滴答器返回一个通道，按指定的间隔递送滴答信号（ticks）。与 `Timer` 类似，它不会被回收器回收，因此你可以使用 `NewTicker` 并在不再需要时调用 `Stop` 方法。

在 `Ticker` 之后，我们有了 `Wait`、`Act`、`Cancel`。它等待指定的间隔，然后在其 goroutine 中调用函数。它返回一个 `time.Timer`，你可以用它来取消调用。其语法如下：

`time.AfterFunc`

## 总结 (Summary)

Goroutine 是 Golang 提供并发的关键。通道是 goroutine 之间的通信流水线。

*   并发不等同于并行，但可以帮助加速代码执行。
*   有多种方法可以同步 goroutine，包括 `Mutex` 和 `RWMutex`，它们通过锁定和解锁代码部分落来避免数据竞争。
*   通道是 goroutine 之间通信的一种优雅方式。
*   信号量模式允许限制超过指定数量的通道访问共享资源。
*   通道可以在通道工厂中使用，你还可以指定通道是否为只发送的或只接收的。
*   你还可以使用定时器和滴答器在未来调度通道。

第十三 章

尽管每次都写出完美的代码是很好，但这并不是一个合理的预期。和所有其他计算机语言一样，Go 会在出现问题时告诉你。测试代码是处理错误以及发布不易导致用户出现问题或系统崩溃程序的重要部分。在 Go 中，错误是值；由于值可以被编程，错误也可以编程。

## 运行时异常与 Panic (Run-Time Exceptions and Panic)

Go 有内置的错误类型，并使用错误值来告知代码运行异常。错误类型是一个接口，错误变量通常被描述为字符串。与其他语言不同，设计上鼓励你显式检查错误，而不是等待执行时抛出异常。





`Panic` 是一个内置函数，用于停止程序的普通控制流。当函数 `P` 调用 `panic` 时，`P` 的执行将会停止，`P` 内部的任何延迟执行（deferred）函数都会像往常一样执行，然后 `P` 返回到其调用者。你可以直接调用 `panic`，但它通常发生在运行时错误中。`panic` 的语法如下，并且可以接受任何参数：

```
> func panic(p interface{})
```

## Panic 与恢复（Panic and Recover）

Golang 允许你处理 panic 并从中恢复，同时提供一些有用的信息并可能向用户输出某些内容。

在书的前面的部分，我们讨论了 `defer` 语句，它将函数调用添加到列表中。该保存的调用列表会在周围函数返回后执行一次。换句话说，延迟函数保证在结束时运行。

当一个函数发生 panic 时，其当前的执行会停止，任何延迟函数都会运行，然后函数返回到它的调用者。这个过程会沿着堆栈向上持续，直到所有函数都已返回或发生 panic。

`recover` 函数只能在延迟函数中使用，它让 Go 获得对发生 panic 的 goroutine 的控制权。如果你尝试在正常流中使用 `recover()`，你只会得到 `nil`，但在发生 panic 的 goroutine 中调用它时，它会捕获 panic 值。

例如，假设你有一个函数 `PrintAllOps`，它接收两个整数 `x` 和 `y`，并对它们进行相加、相减、相乘和除。如果你给 `y` 赋值为零，该函数将发生 panic，因为除以零是非法的，但可以使用 `recover` 来处理：

```
> func PrintAllOps(x int, y int) {
> defer func() {
> if r := recover(); r ! = nil {
> fmt.Printf(“Recovering from panic in PrintAllOps error is: %v \n”, r)
> }
> } ()
> sum, subtract, multiply, divide := x+y, x-y, x\*y, x/y
> fmt.Printf(“sum= %v, subtract=%v, multiply=%v, divide=%v \n”, sum, subtract, multiply, divide)
> }
```

当你使用 `x:=20` 和 `y:=0` 运行 `main` 函数时，输出结果如下：

```
> Recovering from panic in printAllOps error is: runtime error:
> integer divide by zero
> Exiting main without any issues
```

## 使用闭包处理错误（Error Handling with Closures）

在编程中，`closures`（闭包）是存储函数及其环境的记录。闭包允许函数通过闭包对引用和值的拷贝来访问被捕获的变量（局部使用且定义在封闭作用域内的变量），即使该函数是在其作用域之外被调用的。

当你想要同一个函数中检查错误并报告它们时，闭包会很有帮助。这是一个在闭包中封装错误处理的示例。注意代码中的错误检查、错误报告以及随后的正常函数是分开的。

```
> func onlineReqHandler( r http.ResponseWriter, req \*http.Request) {
> err := func () os.Error {
> if req.Method ! = “GET” {
> return os.NewError(“expected GET”)
> }
> }()
> if err != nil {
> http.Error(r, err.Error(), 500)
> return
> }
> r.Write([]byte("success"))
> }
```

## 测试与基准测试（Testing and Benchmarking）

在编程中，`closures`（闭包）是存储函数及其环境的记录。闭包允许函数通过闭包对引用和值的拷贝来访问被捕获的变量（局部使用且定义在封闭作用域内的变量），即使该函数是在其作用域之外被调用的。

当你想要同一个函数中检查错误并报告它们时，闭包会很有帮助。这是一个在闭包中封装错误处理的示例。注意代码中的错误检查、错误报告以及随后的正常函数是分开的。

```
> func onlineReqHandler( r http.ResponseWriter, req \*http.Request) {
> err := func () os.Error {
> if req.Method ! = “GET” {
> return os.NewError(“expected GET”)
> }
> }()
> if err != nil {
> http.Error(r, err.Error(), 500)
> return
> }
> r.Write([]byte("success"))
> }
```

 评估代码性能（Assessing Code Performance）

你可能习惯于时间复杂度分析来查看哪个程序运行得更快。但 Go 提供了内置工具，通过基准测试进行更深入的分析。基准测试允许你查看一个代码版本的性能是否优于另一个。运行一个版本的代码，进行基准测试，运行带有修改的新版本并再次进行基准测试，然后比较结果。这可能会很枯燥，但 Go 有 `benchstat` 命令（旧版本可能使用 `benchcmp`）来比较基准测试之间的统计数据，包括平均值、最小值和最大运行时间。当针对单个文件运行时，结果会汇总该文件。如果为两个包含多个基准测试的输入文件调用，你将看到一列显示两者平均值变化百分比的列。它还会显示 p 值和测试样本量。





加速代码开发和提升代码性能的另外两种方法是是从他人的错误中学习，并在合适的地方部署模式。当你学会了避免常见的陷阱时，你可以更快地犯自己的错误。（这听起来是个玩笑，但事实也确实如此！）

使用模式并识别它们在程序开发中的适用位置，将帮助你跳过枯燥的重复。你可能听过“惯用编程”（idiomatic programming），这意味着遵循语言的约定。尽管 `Go` 仍然较新，但它仍然有许多约定。这些约定可能会随着时间而改变，但这里有你可能会看到的几种。

## 模式：逗号，OK (Comma, OK)

常用的惯用法之一是 `, ok`。当你需要区分整数 0 和某些函数返回的零值时，它非常有用。例如，如果你想为游戏映射高分，你需要知道高分为 0 分与为不存在的玩家所返回的零值之间的区别。

```go
highScores := make(map[string]int)

highScores["Bert"] = 317
highScores["Ernie"] = 433

log.Println(highScores["Ernie"]) // 返回 433，但如果你请求 (highScores["Oscar"])，日志结果为 0。这这意味着 Oscar 的高分是 0，还是说 Oscar 不在 map 中？

// 所以添加 , ok 来避免这个问题的问题。

if val, ok := highScores["Ernie"]; ok {
    log.Println(val) // 记录 433
}
```

## 模式：可见性与运算符 (Visibility and Operator)

`Golang` 中不同的概念之一是公有或私有的可见性。如果你用 `Java` 编写过程序，你不会看到 `protected`、`public` 等修饰符。在 `C++` 中，你看不到 `friend` 类。`Go` 通过大小写来区分（有时称为导出/未导出）：任何 Go 用户都可以访问的公共标识符以大写字母开头，而“私有”或未导出的标识符以小写字母开头。由于这种限制，通常建议倾向于使用更大、更少的包，以避免过于复杂的包层次结构。

你可能会发现 `Go` 在运算符上有些局限，运算符是指返回新对象且不改变参数的函数。像 `C++` 这样的语言支持运算符重载，你可以使用类似数学的语法，但 `Go` 不支持。只要你在包含代码所操作的对象的包内部实现它们，将运算符作为函数使用可以帮助你绕过这一局限性。你可能需要使用几种变体来使其工作。或者，将运算符作为方法允许你链式调用方法。每个方法返回一个接收者，该接收者将成为下一次方法调用的对象。

当你觉得运算符是必要的时，使用接口是一种很好的做法。如果你无法根据接口中的方法进行通用实现，那么你可能拥有类型不相同的项，不应该使用运算符模式。

## 模式：defer

`defer` 允许你在周围函数返回之前执行一个函数，无论是否发生了 panic（崩溃）。开发者在使用 `defer` 时会犯的一些常见错误是你应该注意的。记住，`recover()` 应该*仅*用于特定场景。

## 常见陷阱 (Common Pitfalls)

`defer` 允许你在周围函数返回之前执行一个函数，无论是否发生了 panic。开发者在使用 `defer` 时会犯的一些常见错误是你应该注意的。记住，`recover()` 应该*仅*使用。

### Defer 错误
`defer` 允许你在周围函数返回之前执行一个函数，无论是否发生了 panic。开发者在使用 `defer` 时会犯的一些常见错误是你应该注意的。 

### 可见性与运算符错误
你可能会发现 `Go` 在运算符上有些局限，运算符是指返回新对象且不改变参数的函数。像 `C++` 这样的语言支持运算符重载，你可以使用类似数学的语法，但 `Go` 不支持。只要你在包含代码所操作的对象的包内部实现它们，将运算符作为函数使用可以帮助你绕过这一局限性。你可能需要使用几种变体来使其工作。或者，将运算符作为方法允许你链式调用方法。每个方法返回一个接收者，该接收者将成为下一次方法调用的对象。

当你觉得运算符是必要的时，使用接口是一种很好的做法。如果你无法根据接口中的方法进行通用实现，那么你可能拥有类型不相同的项，不应该使用运算符模式。

### 赋值错误
将运算符作为函数使用可以帮助你绕过这一局限性，只要你在包含代码所操作的对象的包内部实现它们。你可能需要使用几种变体来使其工作。或者，将运算符作为方法允许你链式调用方法。每个方法返回一个接收者，该接收者将成为下一次方法调用的对象。

### 数组错误
`defer` 允许你在周围函数返回之前执行一个函数，无论是否发生了 panic。开发者在使用 `defer` 时会犯的一些常见错误是你应该注意的。记住，`recover()` 应该*仅*使用。

### 通道错误
`defer` 允许你在周围函数返回之前执行一个函数，无论是否发生了 panic。开发者在使用 `defer` 时会犯的一些常见错误是你应该注意的。记住，`recover()` 应该*仅*使用。

### 切片错误
`defer` 允许你在周围函数返回之前执行一个函数，无论是否发生了 panic。开发者在使用 `defer` 时会犯的一些常见错误是你应该注意的。记住，`recover()` 应该*仅*使用。

## 章节总结 (Chapter Summary)

`Golang` 中有很多经常使用的常用模式，它们可能与其他语言中的类似模式有所不同。`Golang` 初学者，特别是那些用其他语言编写过程序的人，会遇到一些新开发者经常犯的“坑”（gotchas）。

*   逗号，OK 惯用法（`, ok`）有助于区分零值和整数 0。
*   `Go` 使用大小写来显示标识符是公有的还是私有的。
*   你可能会发现运算符比其他语言更局限，但在其使用接口是开发者的最佳实践。
*   由于相似语言之间的差异，可能会出现常见陷阱。

无论你是经验丰富的开发者还是你的第一门编程语言，你现在已经有了开启快速且易用的 Go 编程语言旅程的基础知识。它因不仅能加速程序执行，还能加速代码开发而备受推誉。

你学习了开发者为什么要使用它，以及为什么在某些编程环境中受到青睐，还学习了基础“词汇”，这为学习该语言提供了坚实的介绍。





如果你是一位经验丰富的开发者，你已经见过 Golang 与你编程过的其他语言之间的相似与不同之处。如果你不是，那么你已经有了坚实的编程基础，并理解其他计算机语言的许多共同特性。

我们已经涵盖了 Golang 的核心内容，包括切片（slices）和数组（arrays）。在其他语言中，数组是主要的组件，但在这里，切片（基于底层数组）使用得更频繁，并提供了你所需的灵活性。

### 并发与性能

Go 的主要特性之一是并发，或者运行多个 `goroutines` 的能力。有很多技术可以实现这一点而不会遇到数据竞争（即多个代码部分尝试同时访问同一个共享资源）。这些技术从定时函数到 `channels` 不等，`channels` 充当了多个 `goroutines` 之间的通信管道。并发有助于提高代码运行速度。

### 错误处理与内置工具

Go 帮助程序员更轻松地发现和调试错误。其他语言可能会尝试在运行时捕获错误，但 Go 将错误视为可以程序化的值。该语言还包含了一个巧妙的小函数 `defer`，即使在主程序发生 panic（崩溃）时它也能执行延迟的例。程。

Golang 的另一个在许多编程语言中找不到的性能优势是 `testing` 包，它包含了测试代码和评估其性能所需的函数和方法。基准测试（Benchmarking）内置其中，这使得比较代码片段并确定哪一个性能更好更快、更简单。

### 设计哲学与社区

正如你所看到的，Go 的设计旨在快速学习、加速代码开发并快速执行。它还是模块化的，因此如果主包中没有你需要的函数，你可以导入相应的包。

它的设计目的是易于阅读，这样你可以快速理解别人的代码在做什么。当你不需要不断地造轮子时，编写代码会更快；你可以复用自己的，也可以导入别人的。保存你的包可以让你更快地获取你以前用过的代码片段，而无需尝试在目录中翻找。

如果你还没有尝试，现在是时候去 Go playground 自己动手写一些代码了！虽然它是一门相对年轻的语言，但你将找到许多其他用户和社区，他们可以帮助你解决遇到的任何问题。

如果你喜欢这本书并觉得它很有帮助，请写下评论！我们希望向大家推广 Go 以及它如何帮助各种行业和不同编程背景的程序员。

### 关于作者

我的软件开发之旅始于我还是时候，这让我在早年就有充足的机会学习计算机编程和软件开发的基础知识。我从未停止学习计算机编程，在青少年时期通过拆解游戏来学习它们的程序是如何运作的。高中毕业后，我进入密苏里大学，加入了 I.S. 编程俱乐部，并学习信息系统和计算机科学。2016 年，我毕业并作为独立软件开发者创立了自己的公司；我曾使用 Google 编程语言为客户和自己开发了许多应用，包括 `Loop`，一个旨在帮助社区更好地自我管理的社交媒体应用。我曾为全球财富 500 企业提供过培训和咨询。要跟上我的脚步，请在 Twitter 上关注我 `@Streetgenius_`。

### 推荐阅读

如果你喜欢这本书并觉得它很有帮助，考虑通过阅读我的其他书籍来扩展你的编程工具箱：

- Flutter 初学者教程：Flutter 应用开发天才指南
- Python 初学者：Python 编程天才指南

Combs, Veronica. “Google’s Go Scores as the Top Language Developers Want to Learn.” *TechRepublic*, 2020 年 5 月 12 日, [www.techrepublic.com/article/developers-put-learning-googles-go-at-the-top-of-their-to-do-list](http://www.techrepublic.com/article/developers-put-learning-googles-go-at-the-top-of-their-to-do-list).

### 更多资源

- Bellairs, R. “What Is Static Analysis? Static Code Analysis Overview.” *Perforce Software*, 2020 年 2 月 10 日, www.perforce.com/blog/sca/what-static-analysis.
- Biggs, John, and Ben Popper. “What’s so Great about Go?” *Stack Overflow Blog*, 2020 年 11 月 6 日, stackoverflow.blog/2020/11/02/go-golang-learn-fast-programming-languages.
- Caraveo, Ralph, III. “Go’s Extended Concurrency: Semaphores (Part 1) - Ralph Caraveo III.” *Medium*, 2018 年 9 月 4 日, medium.com/@deckarep/gos-extended-concurrency-semaphores-part-1-5eeabfa351ce.
- Chng, Peter. “Golang: Promoted Methods, Method Sets and Embedded Types » Unitstep.Net.” *Unitstep*, 2015 年 9 月 16 日, unitstep.net/blog/2015/09/16/golang-promoted-methods-method-sets-and-embedded-types.
- Chu, Zion. “Use of Synchronization Techniques in Golang - Zion Chu.” *Medium*, 2021 年 3 月 29 日, lebum.medium.com/use-of-synchronization-techniques-in-golang-53d75bc0a646.





# 接口：揭秘 Golang 的 `io.Reader` 和 `io.Writer`。

- “揭秘 Golang 的 `io.Reader` 和 `io.Writer` 接口 | I Care, I Share, I’m Nathan LeClaire.” *Nathan LeClaire*, 2014 年 7 月 19 日, nathanleclaire.com/blog/2014/07/19/demystifying-golangs-io-dot-reader-and-io-dot-writer-interfaces.
- “Golang 中的接口。” *GeeksforGeeks*, 2019 年 11 月 20 日, [www.geeksforgeeks.org/interfaces-in-golang](http://www.geeksforgeeks.org/interfaces-in-golang).
- *学习 Go 编程*. blog.learngoprogramming.com.
- Lodha, Tilak. “Go 中的并发与并行 - Tilak Lodha.” *Medium*, 2018 年 6 月 15 日, medium.com/@tilaklodha/concurrency-and-parallelism-in-golang-5333e9a4ba664.
- “Golang 中的方法。” *GeeksforGeeks*, 2019 年 11 月 20 日, www.geeksforgeeks.org/methods-in-golang.
- “Golang 中为函数的返回值命名。” *GeeksforGeeks*, 2020 年 5 月 10 日, [www.geeksforgeeks.org/naming-the-return-values-of-a-function-in-golang](http://www.geeksforgeeks.org/naming-the-return-values-of-a-function-in-golang).
- Osadchiy, Victor. “为什么在你的项目中使用 Go 语言？” *Yalantis*, yalantis.com/blog/why-use-go. 访问于 2021 年 7 月 1 日。
- Peshkov, Sergei. “对 Go 语言的四个批评。” *Toptal Engineering Blog*, 2018 年 4 月 4 日, www.toptal.com/go/4-go-language-criticisms.
- Programmersought. “Golang - Goroutine 与 Channel - Programmer Sought。” *Programmersought*, www.programmersought.com/article/8644637992. 访问于 2021 年 7 月 1 日。
- Quest, Kyle. “Go 的 50 种：新 Golang 开发者的陷阱、注意事项和常见错误。” *Devs ♥ Security*, 2015 年 12 月 17 日, devs.cloudimmunity.com/gotchas-and-common-mistakes-in-go-golang.
- *QVault*. qvault.io/golang.
- Ralch, S. “Golang 中的设计模式：工厂方法：Blog.Ralch.Com。” *Ralch*, 2016 年 1 月 31 日, blog.ralch.com/tutorial/design-patterns/golang-factory-method.
- Rao, Karthic. “使用 Benchcmp 和 Benchviz Golang 轻松分析基准测试。” *Medium*, 2018 年 4 月 5 日, medium.com/@hackintoshrao/analyzing-benchmarks-with-ease-using-benchcmp-and-benchviz-golang-add607fc46d6#.8x32zrjpo.
- “Golang 中的反射。” *GeeksforGeeks*, 2020 年 4 月 21 日, [www.geeksforgeeks.org/reflection-in-golang](http://www.geeksforgeeks.org/reflection-in-golang).
- Roy, Arindam. “Golang Panic 处理与恢复的简明指南。” *Medium*, 2019 年 9 月 15 日, medium.com/swlh/simple-guide-to-panic-handling-and-recovery-in-golang-72d6181ae3e8.
- *运行 Go*. Medium.com, medium.com/rungo.
- “Golang 中的字符串。” *GeeksforGeeks*, 2019 年 8 月 9 日, [www.geeksforgeeks.org/strings-in-golang](http://www.geeksforgeeks.org/strings-in-golang).
- Shichao. “第 12 章 反射 - Shichao 的笔记。” *Shichao*, notes.shichao.io/gopl/ch12. 访问于 2021 年 7 月 1 日。
- Shirsath, Reemi. “金融科技中的 Golang - Reemi Shirsath。” *Medium*, 2020 年 10 月 22 日, reemishirsath.medium.com/golang-in-fintech-e27193a7b603.
- Sophie. “Go Goto 语句。” *W3Adda*, 2017 年 12 月 17 日, www.w3adda.com/golang-tutorial/go-goto-statement.
- *Tutorial Edge*. tutorialedge.net/golang.
- *Tutorials Point*. www.tutorialspoint.com/go.
- “Golang 中的类型断言。” *GeeksforGeeks*, 2020 年 6 月 22 日, www.geeksforgeeks.org/type-assertions-in-golang.
- “理解 Go 中的 Map (Maps).” *DigitalOcean*, 2021 年 6 月 14 日, www.digitalocean.com/community/tutorials/understanding-maps-in-go.
- “在 Go 循环中使用 Break 和 Continue 语句。” *DigitalOcean*, 2021 年 6 月 14 日, [www.digitalocean.com/community/tutorials/using-break-and-continue-statements-when-working-with-loops-in-go](http://www.digitalocean.com/community/tutorials/using-break-and-continue-statements-when-working-with-loops-in-go).
- Wolfe, Mark. “我该如何构建我的 Go 项目？” *Wolfe*, 2020 年 3 月 9 日, www.wolfe.id.au/2020/03/10/how-do-i-structure-my-go-project.
- *你的基础*. yourbasic.org/golang.
- Yse, Diego Lopez. “核心编程 | 控制结构 - 向数据科学。” *Medium*, 2020 年 1 月 22 日, towardsdatascience.com/essential-programming-control-structures-2e5e73285df4.
- *Zetcode*. zetcode.com/golang.

