# 
Go 入门指南


![](img/go-from-the-beginning-generated.png)



#### Chris Noring

This book is for sale at [`leanpub.com/go-from-the-beginning`](http://leanpub.com/go-from-the-beginning)

![publisher's logo](img/leanpub-logo.png)

\*   \*   \*   \*   \*

This is a [Leanpub](https://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](https://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*


To the brave people of Ukraine for which I’m writing this book


if (condVar > someVal) {console.log("xxx")}
```
[/content]

译文：

[content]
-   [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**理查德·费曼**。

1.  运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
if (condVar > someVal) {console.log("xxx")}
```
[/content]

Now, let's translate the given text.

## <unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> [content]



      5  "os"
      6  "strconv"
      7 )
      8 
      9 func add(no int, secondNumber int) int {
      10  return no + secondNumber
      11 }
      12 
      13 func main() {
      14  no1, _ := strconv.Atoi(os.Args[1])
      15  no2, _ := strconv.Atoi(os.Args[2])
      16  var sum = add(no1, no2)
      17  fmt.Println(sum)
      18 }
    ```

-   [🚀 挑战]

    如果运行程序如下：

    ```
    1 go run main.go one two
    ```

    处理任何转换错误，并在发生转换错误时调用 `panic()`。

-   [Working with loops]

    这一章节介绍 Go 中使用循环的方法。循环用于在你的代码中重复语句。

-   [Introduction]

    本章节将涵盖：

    *   使用 `for` 进行循环语句。

    *   根据条件使用 `break` 退出循环。

    *   使用 `range` 遍历数组。

    *   使用 `continue` 和 `break` 控制循环。

-   [The case for looping statements]

    你很可能需要重复一组指令。例如，你可能有一个订单列表需要处理每个订单，或者你有一个文件需要逐行读取，或者其他计算。无论你的情况如何，你很可能需要循环构造，那么在 Go 中有哪些选项？

    你使用 `for` 循环。有三种主要用法：

    *   **increment steps**。通过变量，你定义一个起始点、停止条件和增量步骤。这是你的“经典” for-loop。以下是示例：

        ```
        1  for i := 0; i < 10; i++ {
        2    // 运行这些语句
        3  } 
        ```

    *   **while**。在许多编程语言中，你有 `while` 关键字。Go 没有这个，但你可以使用 for-loop 类似地使用。你省略初始化步骤和增量步骤，得到以下代码：

        ```
        1 for <condition> {
        2   // 运行这些语句
        3 }
        ```

    *   **for each**。最后，你有一个类似 `for-each` 的构造，它作用于数组或已知序列。它使用 `range` 关键字来工作：

        ```
        1  for i,s := range array {
        2    // 运行这些语句
        3  }
        ```

-   [The `for` loop]

    传统的 for-loop 有三个不同的部分：

    *   **initialization**，这里你想创建一个变量并赋予初始值，例如：

        ```
        1  for i:= 0;
        ```

        注意使用 `;`，通常你会使用分号，但在这种构造中，你需要它。

    *   **condition**。下一步是评估是否应该继续增加还是停止。你在这里定义一个布尔表达式，如果为 `true`，则继续循环：

        ```
        1  for i := 0; i< 10     
        ```

        `i < 10`，只要值在 0 到 10 之间（达到 10 后，循环终止），则返回 true，循环继续。

    *   **increment**，在这一步，循环变量 `i` 被更新，通常将其增加 1，但也可以使用任何增量，正或负。

        ```
        1  for i := 0; i< 10; i++ {
        2 
        3  }
        ```

        这里，`i` 增加 1。此循环将运行十次。

-   [Repeat until the condition is met with `while`]

    一个简化的循环可以省略初始化和增量步骤。你只剩下条件步骤。该步骤测试变量是 `true` 还是 `false`，当表达式为 false 时，循环退出。以下是一个示例：

    ```
    1 i := 1
    2 for i < 10 {
    3   i++
    4   // 执行某些操作
    5 }
    ```

    在这种情况下，我们在循环之外声明 `i`。在循环内部，我们需要修改值，使得循环表达式为 false，否则将无限循环。

    以下是另一个示例，使用相同的思想，但这次我们从用户那里获取输入：

    ```
      1 var keepGoing = true
      2 answer := ""
      3 for keepGoing {
      4   fmt.Println("Type command: ")
      5   fmt.Scan(&answer)
      6   if answer == "quit" {
      7     keepGoing = false
      8   }
      9 }
    10 fmt.Println("program exit")
    ```

    程序的运行示例可能如下：

    ```
    1 Type command: test
    2 Type command: something
    3 Type command: quit
    4 program exit
    ```

-   [Using for-each over a range]

    对于下一个循环构造，目标是对数组或已知序列进行操作。对于每次迭代，你可以获得索引和下一个项。以下是示例代码：

    ```
    1 arr := []string{"arg1", "arg2", "arg3"}
    2  for i, s := range arr {
    3   fmt.Printf("index: %d, item: %s \n", i, s)
    4  }
    ```

    `arr` 被定义为数组，然后使用 `range` 构造来遍历数组。对于每次迭代，当前索引被赋值给 `i`，数组项被赋值给 `s`。以上代码的输出将如下所示：

    ```
    1 index: 0, item: arg1
    2 index: 1, item: arg2
    3 index: 2, item: arg3
    ```

-   [Controlling the loop with `continue` and `break`]

    迄今为止，你已经了解了三种使用 `for` 构造的方法。还有控制循环的方法。你可以使用以下关键字控制循环：

    *   `break`，这将退出循环构造

        ```
        1  arr = []int{-1,2}
        2  for i := 0; i< 2; i++ {
        3    fmt.Println(arr[i])
        4    if arr[i] < 0 {
        5      break;
        6    }
        7  }     
        ```

        输出将是：

        ```
        1  -1
        ```

        它不会输出 `2`，因为循环在第一次迭代后退出。




## 读取用户输入

你将学习如何读取用户输入，包括一种简单的技术和使用格式化器的更高级技术。

## Introduction

本章将涵盖：

*   使用 `Scan()` 方法读取用户输入。

*   读取单个输入。

*   读取多个输入。

*   使用格式化器的工作。

## 用户输入

能够从控制台读取用户输入是很重要的，它给用户与程序互动的机会。需要考虑的是你是如何请求用户输入的，是一个词还是多个输入。用户是否通过空格或换行分隔输入？无论你采用什么方法，都要向用户传达所选的方法。

## 使用 `fmt` 管理用户输入

迄今为止，你已经看到如何使用 `fmt` 包打印到控制台。它也可以用于读取用户输入。

`fmt` 库内置了 `Scan()` 方法，我们将使用它来捕获用户输入。

## 读取单个输入

你可能一开始就想读取用户的一个输入。默认情况下，`Scan()` 方法就是用来做这件事的。

下面是一段示例代码，展示如何收集用户输入：

```
1 package main
2 
3 import "fmt"
4 
5 func main() {
6     var response string
7     fmt.Scan(&response)
8     fmt.Println("User typed: ", response)
9 }
```

注意，你将字符串 `response` 作为参考传递，使用 `&` 运算符。这样做是因为 `Scan()` 方法会修改你传入的变量。

运行这段代码后，你会看到以下输出：

```
1 hello
2 User typed: hello
```

## 读取多个输入

你可以向 `Scan()` 方法提供多个参数。通过提供多个参数，你可以收集多个用户输入，并在 `Scan()` 函数中用逗号分隔每个输入。以下是如何应用此技术：

```
1 var a1, a2 string
2 // 多个输入
3 fmt.Scan(&a1, &a2)
4 
5 // 使用格式化字符串打印用户输入
6 str := fmt.Sprintf("a1: %s a2: %s", a1, a2)
```

注意 `a1` 和 `a2` 传递给 `Scan()`，并且用逗号分隔。那么这些代码会如何运行？

当你运行这段代码时，用户有两种输入方式。用户可以通过空格分隔值，例如：

```
1 hi you
2 a1: hi a2: you
```

或者通过换行分隔：

```
1 hi 
2 you
3 a1: hi a2: you
```

## `Scanf()`，使用格式化器扫描输入

迄今为止，你已经看到如何使用空格和换行作为分隔符来收集输入。你也可以指定如何收集输入。想象用户想输入发票号，例如“INV200”或“INV114”，而你感兴趣的是数字部分，或者你也想保留前缀呢？

解决这个问题的方法是 `Scanf()` 函数。它使用格式化器。通过格式化器，你可以选择从用户输入中感兴趣的部分，并将其放入你想要的变量中。

在上面提到的案例中，你可以编写如下代码：

```
1 var prefix string
2 var no int
3 // in110
4 fmt.Scanf("%3s%d", &prefix, &no)
5 fmt.Printf("prefix: %s, invoice no: %d", prefix, no)
```

`Scanf()` 的第一个参数 `3s%d` 的含义是，取前 3 个字符，`%3s` 将其解释为字符串。然后解释并把剩余部分作为数字，`%d`。

运行此程序，你将得到以下输出：

```
1 inv200
2 prefix: inv, invoice no: 200
```

“inv” 被放入 `prefix`，而 200 被放入 `no` 变量。

## 了解更多

要了解更多关于此领域的信息，请查看以下链接 [`pkg.go.dev/fmt#Scanf`](https://pkg.go.dev/fmt#Scanf)

## 练习 - 读取用户输入

在这次练习中，你将读取用于卡牌游戏的用户输入。目标是捕获玩家的名称。

1.  创建一个名为 *main.go* 的文件，包含以下内容：

    ```
    1 package main
    2 
    3 import "fmt"
    4 
    5 func main() {
    6 
    7 }
    ```

2.  将以下代码添加到 `main()` 方法中：

    ```
    1 fmt.Println("Enter player names (separated by space or newline):")
    2 var player1, player2 string
    3 fmt.Scan(&player1, &player2)
    4 fmt.Println("Players are: ", player1, player2)
    ```

3.  使用 `go run main.go` 运行程序：

    ```
    1 go run main.go
    ```

    你应该看到以下输出：

    ```
    1 Enter player names (separated by space or newline):
    2 Alice Bob
    3 Players are:  Alice Bob
    ```

## 🚀 挑战

尝试修改程序，使其首先输入玩家数量，然后确保所有玩家都有名称。以下是该程序的示例输出：

```
1 Enter number of players: 
2 3
3 Enter Player 1 name: 
4 Alice
5 Enter Player 2 name:
6 Bob
7 Enter Player 3 name:
8 Jean
9 Players are: Alice Bob Jean
```

## 解决方案

```
 1 package main
 2 
 3 import "fmt"
 4 
 5 func main() {
 6  fmt.Println("Enter player names (separated by space):")
 7  var player1, player2 string
 8  fmt.Scan(&player1, &player2)
 9  fmt.Println("Players are: ", player1, player2)
10 }
```

## 使用函数

在本章中，我们将讨论如何定义和使用函数。当你在多个地方使用相同类型的代码时，函数是很有用的。通过使用函数，你可以减少重复代码。

## Introduction

本章将涵盖：

*   函数是什么以及为什么使用它。

*   如何定义和调用函数。

*   返回多个值。

## 为什么使用函数

等 soon 你就有一组在多个地方重复的语句集合，创建函数是一个好用例。通常在函数中，你会进行日志记录到文件、执行计算或与数据源通信。

## 你的第一个函数 `main()`

迄今为止，你已经看到函数 `main()`，它定义如下：

```
1 func main(){
2 }
```

这是唯一的函数，它是入口点，代表程序的开始。然而，你可以定义其他函数。

## 函数的解剖结构

一个函数由各种部分组成。通过包含所有这些部分，你确保拥有可在许多地方重用的可复用代码片段。

以下是需要关注的部分：

*   `func`，关键字 `func`。




# 处理错误

在本章中，我们将介绍错误处理。

## 介绍

本章将介绍：

* 使用 `panic` 和 `recover` 触发并处理错误。

* 使用错误模式以更符合 Go 语言惯例的方式管理错误。

## 错误

我们的应用并不完美，它们会抛出错误。无论是因为我们编写的代码，还是我们使用的包中的代码，都可能导致错误。有时，这正是我们在提供不良输入时期望的行为。

无论如何，我们的用户期望我们能够处理这些错误。此外，为了我们自己的利益，我们需要以一种方式记录这些错误，以便在出现意外错误时能够修复它们。

在 Go 中，有两种主要的错误处理方式：

* **panic/recover**。`panic` 和 `recover` 是语言构造。如果你了解其他编程语言，它们类似于 `throw` 和 `catch`。但这意味着什么呢？这意味着有一个错误，包含错误消息和堆栈跟踪，我们可以捕获并恢复它，或者让程序崩溃。

* **error pattern**。这被称为 Go 语言的惯用方式。其思想是从函数调用中返回一个值和一个错误对象。如果发生错误，返回的错误对象不为 `nil`；如果没有错误，则返回 `nil`。

## 使用 `panic()` 使程序崩溃

让我们以函数 `Divide()` 为例：

```
1 func Divide(nominator int, divider int) float32 {
2   if divider == 0 {
3     panic("can't divide by 0")
4   }
5   return float32(nominator) / float32(divider)
6 }
```

它包含一个 `if` 检查。如果 `divider` 为 `0`，则调用 `panic()`。那么会发生什么呢？你会看到类似以下内容：

```
1 panic: can't divide by 0
2 
3 goroutine 1 [running]:
4 main.Divide(...)
5         /<path>/panic.go:20
6 main.main()
7         /<path>/panic.go:33 +0x96
8 exit status 2
```

顶部是你传递给 `panic()` 的错误字符串，即“can’t divide by 0”。然后是堆栈跟踪，指示错误发生的位置。从下往上看，错误始于第 33 行，然后是第 20 行，即：

```
1 panic("can't divide by 0")
```

因此，我们有了一个方法来保护自己免受不想要的输入值的影响。但崩溃程序是否必要？在某些情况下是，在其他情况下则不是。对于后者，我们有 `recover()`。

### 使用 `recover()` 捕获错误

使用 `recover()` 是为了捕获错误，使我们的程序能够继续运行。在继续之前，我们需要先了解一个概念，即 `defer`。`defer` 是一种语言构造，用于延迟函数的执行，直到最近的函数返回。以下是一个示例：

```
1 defer fmt.Println("second")
2 fmt.Println("first")
```

运行此程序，你应该看到：

```
1 first
2 second
```

> 将 `defer` 视为最后发生的操作。

在捕获错误的上下文中，捕获错误（如果你想捕获它）应该是最后发生的操作。让我们再看 `Divide()` 函数：

```
1 func Divide(nominator int, divider int) float32 {
2   defer errorHandler()
3   if divider == 0 {
4     panic("can't divide by 0")
5   }
6   return float32(nominator) / float32(divider)
7 }
```

可以看到，它现在有一行 `defer errorHandler()`，这将是最后执行的操作。根据 `divider` 的值，它会调用 `panic()` 或 `return` 语句作为最后一步。

那么 `errorHandler()` 是什么样子呢？

```
1 func errorHandler() {
2   if r := recover(); r != nil {
3     fmt.Println("Recovered ", r)
4   }
5 }
```

在 `errorHandler()` 中，我们调用 `recover()` 并将其赋值给变量 `r`，然后检查它是否为 `nil`。如果不为 `nil`，说明发生了错误，我们打印出来。如果为 `nil`，则用户不会察觉到任何异常。



## 数组和切片

在本章中，我们将介绍数组和切片。

## 介绍

本章将涵盖：

*   声明和检查数组。

*   访问数组中的元素。

*   使用切片。

## 数组

数组是一组连接的元素。当你有一组类似的事物时，比如许多订单、汽车和文件中的行，你会使用数组。

数组的思想是将所有这些数据集中在一个结构中。你还想能够遍历它，并对它作为一个整体执行操作。

## 声明数组

要声明一个数组，你需要指定以下属性：

*   **capacity**，它包含的元素数量。




type Address struct {
    city   string
    street string
    postal string
}

type Person struct {
    name    string
    address Address
}

person := Person{
    name: "chris",
    address: Address{
        city: "Stockholm",
    },
}



## 接口

本章节介绍什么是接口以及如何使用它。

## 介绍




package main

type Point struct {
    x float32
    y float32
}

type Vehicle struct {
    velocity float32
    Point
}

func (v *Vehicle) fly() {
    v.velocity = 10
}

func (v *Vehicle) land() {
    v.velocity = 0
}

func (v *Vehicle) position() Point {
    return v.Point
}

func main() {
    v := Vehicle{
        velocity: 0,
        Point: Point{
            x: 0,
            y: 0,
        },
    }
    v.fly()
    fmt.Println(v.velocity) // 10
    v.land()
    fmt.Println(v.velocity) // 0
}



1 包 main
2 
3 导入 "fmt"
4 
5 类型 Point 结构体 {
6  x float32
7  y float32
8 }
9 
10 类型 Vehicle 结构体 {
11  velocity float32
12  Point
13 }
14 
15 类型 Spaceship 接口 {
16  fly()
17  land()
18  position() Point
19 }
20 
21 方法 (v *Vehicle) fly() {
22  v.velocity = 10
23 }
24 
25 方法 (v *Vehicle) land() {
26  v.velocity = 0
27 }
28 
29 方法 (v Vehicle) position() Point {
30  返回 v.Point
31 }
32 
33 func main() {
We are now able to invoke the `Help()` function from *main.go* like so:
34 
35 ```
36 if (condVar > someVal) {console.log("xxx")}
37 ```



## 测试你的 Go 代码

## 介绍

本章节将涵盖：

*   为何你应该测试你的代码。

*   Go 中的测试库。

*   编写和运行测试。

*   控制如何运行你的测试。

*   生成覆盖率报告。

## 为何我们进行测试

测试你的代码可以确保它按预期工作。本章节我们专注于单元测试。

## Go 提供的内容

Go 有一个 `testing` 包，为我们提供了以下两点：

*   测试的参数。`testing` 库暴露了一个 `t *testing.T` 参数。通过将其作为函数的参数，该函数即成为测试。

    ```
    1  func TestAdd(t *testing.T) {}
    ```

*   断言结果的方法。`testing` 还暴露了 `t.Errorf()`。通过以字符串形式调用它，测试即视为失败。要通过测试，你什么都不需要做：

    ```
    1  t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
    ```

下面是一个测试函数的示例：

```
1 func TestAdd(t *testing.T) {
2   total := Add(2, 2)
3   if total != 4 {
4    t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
5  }
6  t.Log("running TestAdd")
7 }
```

*   首先，调用要测试的代码：

    ```
    1  total := Add(2, 2)
    ```

*   其次，进行断言，以查看是否成功或失败：

    ```
    1  if total != 4 {
    2    t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
    3  }
    ```

    如果结果不是预期的，则调用 `t.Errorf()` 来指出出错的地方。

## 你的第一个测试

确保你已创建了一个使用 `go mod init` 的项目，然后创建类似下面的文件结构：

```
1 main.go
2 math/
3   math.go
4   math_test.go
```

接下来要做的是创建测试文件。你希望将测试文件尽可能贴近你要测试的代码。因为你要测试 *math.go*，所以在 math/ 目录下创建 `math_test.go` 文件，如下所示：

```
1 main.go
2 math/
3   math.go
4   math_test.go
```

### 编写并运行你的第一个测试

现在你已经拥有上述文件结构，确保 *math_test.go* 文件包含以下内容：

```
 1 package math
 2 
 3 import (
 4   "testing"
 5 )
 6 
 7 func TestAdd(t *testing.T) {
 8   total := Add(2, 2)
 9   if total != 4 {
10     t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
11   }
12   t.Log("running TestAdd")
13 }
```

运行测试时，你需要调用 `go test` 命令。以下是不同运行测试的方式：

*   `go test`，运行当前工作目录中的测试。示例输出：

    ```
    1  ok      test-example/math       0.258s
    ```

*   `go test -v`，运行详细版本。可能的输出如下：

    ```
    1  === RUN   TestAdd
    2   math_test.go:12: running TestAdd
    3 
    4  --- PASS: TestAdd (0.00s)
    5  PASS
    6  ok      test-example/math       0.422s
    ```

    在详细版本中，你可以看到测试的名称以及是否失败。

*   `go test ./..`，递归运行。如果你以此方式运行命令，它会运行子文件夹中的所有测试。

## 控制测试运行

有几种方式可以控制测试的运行数量。以下是一些方法：

- **通过模式运行测试**。你可以提供一个模式，让 Go 运行部分测试，该模式通过子串匹配或甚至在特定深度进行匹配。例如：

    ```
    1     go test -run <pattern>
    ```

- **跳过测试**。在测试中调用 `t.Skip()`，该测试将被跳过。

*   **运行单个测试**。你可以通过运行指定包和测试名称的模式来运行单个测试，例如：

    ```
    1     go test -run TestAdd
    ```



1 go test -run TestAdd ./math

Here’s the package is called math and the name of the test is `TestAdd()`.

## Coverage

There’s a built-in tool for dealing with coverage. To learn more about the tool, you can type:

```
go tool cover -help
```

it will list a set of commands.

The tool is centred on the concept of having an out file. The out file contains instructions on where your code is covered by tests and where it isn’t. An out file can look something like this:

```
mode: set
test-example/math/math.go:3.32,5.2 1 1
test-example/math/math.go:7.37,9.2 1 1
test-example/math/math.go:11.47,13.2 1 0
```

This is a format readable by the tool.

It’s a prerequisite to generate said “out file” before you can view your code’s coverage. Place yourself in the directory you mean to measure coverage on and run this command:

```
go test -coverprofile=c.out
```

Now you are ready to run a command that shows the result in a browser:

```
go tool cover -html=c.out
```

The above command spins up a browser and the output look something like so:

![coverage](img/missing.png)

coverage

The coverage report tells us that the green portions are covered by tests whereas the red portions should have tests covering it.

## Learn more

There’s a lot more to learn on testing with Go, have a look at package documentation, [docs](https://pkg.go.dev/testing)

## Challenge

Create a test for a piece of code you wrote. Run the test. See if you can produce a coverage report and implement any gaps pointed out by the report.

## Working with JSON

In this chapter, you will work with the JSON data format.

## Introduction

In this chapter, you will learn the following:

*   The JSON data format.

*   How to read JSON data and map it to existing structures in Go.

*   How to create JSON and persist it in files.

## JSON

JSON is a lightweight data format for storing and transporting data. The acronym stands for **J**ava**S**cript **O**bject **n**otation.

The format is commonly used in Web services. Usually, data is encoded as JSON and sent via HTTP. A client, for example, a web browser, consumes the JSON data and uses it to render a frontend with the help of HTML and CSS. It’s also common for JSON to be used to communicate between services.

Here’s an example of what the format looks like:

```
{
  "products": [{
    "id": 1,
    "name": "a product"
  },
  {
    "id": 2,
    "name": "another product"
  }]
}
```

The above depicts a list of products. Each key needs to be encased with quotes and values can be everything from primitives like numbers, strings, Booleans etc to more complex types like an array or an object.

what is this format, and what contexts is it used in.

## Reading JSON

To work with JSON, you need to use the `encoding/json` library. It allows you to both read and write JSON data.

To read JSON data you need to first have a structure in your Go code read to map to the JSON data. Imagine having the following JSON data:

```
{
  "products" : [
    {
      "id": 1,
      "name": "some product"
    }
  ]
}
```

To map this in Go, you need a struct that matches its structure like so:

```
type Product struct {
  Id int
  Name string
}

type Response struct {
  Products []Product
}
```

### Notation

The first step is to create the structures needed to match your JSON data. But you also need to do one more thing, add notations. The problem we are looking to solve is how the `Product` property is called `Id` and not `id` as it’s called in the JSON data.

> Won’t that just work?

Unfortunately, not

> Why don’t you just name the struct property `id`

The library `encoding/json`, is a separate package from the main package, meaning we need to make a field name, defined in the main package, uppercase for the `encoding/json` package to find it.

So that means, we need to add the following annotations to our above created structs:

```
type Product struct {
  Id int `json: "id"`
  Name string `json: "name"`
}

type Response struct {
  Products []Product `json: "products"`
}
```

What these annotations do is to say, in the JSON data, look for properties with these names and map them to the following property. Like in this example from above:

```
type Product struct {
  Id int `json: "id"`
}
```

### Reading the data

Ok, so we’ve defined the structures in Go that we will map our JSON data to. So how do we read from a JSON source? Well, JSON is usually stored in one of two ways:

*   a string literal, like so `{ "name": "my product", "id": 1 }`

*   in a JSON file:

```
{
  "id": 1,
  "name": "my product"
}
```

Let’s show how to work with both approaches:

**Reading from a string literal**

We will use the `Unmarshal()` function and provide it with the string literal as the first parameter and the data to write the result to as the second parameter.

```
package main

import (
  "fmt"
  "encoding/json"
)

func main() {
  str := `{ "name": "my product", "id": 1 }`
  product := Product{}
  json.Unmarshal([]byte(str), &person)
  fmt.Println(person) // prints the object
}
```

Note how we also convert the response to a byte array `[]byte(str)` and how the data is written in the second parameter to the `person` instance as a reference, `&person`.

**read from a file**

To read from a file, we will use the `io/ioutil` library and its `ReadFile()` function. Like with the string literal, the `Unmarshal()` function will be used to write the data to a struct instance.

```
package main

import (
  "encoding/json"
  "fmt"
  "io/ioutil"
  "iohelper/dir"
  "iohelper/file"
  "log"
)

type Products struct {
  Products []Product `json: products`
}

type Product struct {
  Id   int    `json: "id"`
  Name string `json: "name"`
}

func main(){
  file, _ := ioutil.ReadFile("products.json")

  data := Products{}
  _ = json.Unmarshal([]byte(file), &data)

  for i := 0; i < len(data.Products); i++ {
    fmt.Println("Product Id: ", data.Products[i].Id)
    fmt.Println("Name: ", data.Products[i].Name)
  }
}
```

## Writing JSON

We’ve seen so far how we can read JSON data either from a string literal or from a file, but what about writing data?

Two cases are important for us:

*   Writing data to a structure. We are working with structs so any changes we do on the structs need to be converted back to JSON.

*   Generate JSON from data. In the second case, we might be working with a raw string literal or even with pure primitives, how would we do that?

Let’s address both these cases. What these cases have in common is the `Marshal()` function. The `Marshal()` method can take a primitive or a struct and taking that into JSON:

```
package main

import (
  "fmt"
  "encoding/json"
)

type Person struct {
  Id int `json: "id"`
  Name string`json: "name"`
}

func main() {
  aBoolean, _ := json.Marshal(true)
  aString, _ := json.Marshal("a string")
  person := Person{
    Id: 1
    Name: "a person"
  }
  aPerson, _ := json.Marshal(&person)
  fmt.Println(string(aBoolean)) // true
  fmt.Println(string(aString))  // a string
  fmt.Println(string(person))  // { "id": 1, "name": "a person" }
}
```

## Assignment

Given the following file *response.json*, find a way to read the data and display it on the screen:

```
{
  "orders": [
    {
      "id": 1,
      "items": [
        { "id": 1, "quantity": 3, "total": 34.3 },
        { "id": 2, "quantity": 2, "total": 17.8 }
      ] 
    },
    {
      "id": 2, 
      "items": [
        { "id": 3, "quantity": 3, "total": 10.0 },
        { "id": 4, "quantity": 2, "total": 100.5 }
      ] 
    } 
  ]
}
```

## Solution




-   [构建 Web API](https://example.org) 通常是我们与服务或客户端交互以提供数据的方式。客户端可能是网页或像 curl 这样的工具。本章我们将学习如何构建一个 Web API，它通过 HTTP 处理请求。

## Introduction

在本章中，你将学习以下内容：

*   什么是 Web API。

*   `net/http` 库及其在高层面上的功能。

*   响应请求。

*   处理请求数据，包括路由和查询参数，以及请求体。

*   使用 ServeMux，以及为什么它可能是首选选择。

## Web API

Web 服务的常见责任是响应请求：

*   **请求数据** 并返回数据，如 JSON、XML、图片、CSS、HTML

*   **请求修改资源** ，包括创建、更新或删除

## The `net/http` library

`net/http` 是一个库，它将帮助我们构建 Web 服务器。使用该库构建 Web 服务器涉及以下步骤：

*   创建服务器实例。

*   定义路由请求并指定如何响应它们。

*   启动服务器实例，确保它在特定地址和端口上可访问。

### 创建服务器实例

在 `net/http` 中，`http` 代表你的服务实例。

```
1 import (
2   "fmt"
3   "net/http"
4 )
5 
6 func main() {
7     // do something with `http`
8 }
```

### 定义路由

路由是你在应用中定义逻辑分离的方式，例如 `products`、`orders` 或其他合理的区域。

要定义路由，你需要定义一个路由模式和一个函数，当路由被访问时，该函数会被调用：

```
1 func hello(w http.ResponseWriter, req *http.Request) {
2   fmt.Fprintf(w, "hello\n")
3 }
4 
5 func main(){
6   http.HandleFunc("/hello", hello)
7 }
```

在上面的代码中，“/hello”是路由模式，表示所有访问“/hello”的 web 请求都应由 `hello()` 函数处理。

### 响应和请求

`hello()` 函数显示它接受 `ResponseWriter` 和 `Request`：

```
1 func hello(w http.ResponseWriter, req *http.Request) {
2   fmt.c(w, "hello\n")
3 }
```

预期你会检查 `req` 对象，根据请求中的数据决定返回什么内容。然后你需要使用 `w` 来生成响应。在这个例子中，你通过将 `w` 传递给 `Fprintf()` 来返回字符串。`FPrintf()` 接受一个写入器。写入器可以是任何 IO，因此它可以写入文件，也可以像这里一样写入 HTTP 响应流。

### 启动服务器

我们已经介绍了路由、生成响应，现在该启动服务器以便它能响应请求了。

你使用 `ListenAndServe()` 函数启动服务器，该函数接受端口，例如：

```
1 http.ListenAndServe(":8090", nil)
```

## 响应请求

 incoming request 可能是请求特定路由（例如 /products 或 /orders），也可能是请求特定静态文件（如图片、文本文件或 CSS）。请求本身提供了提示，不仅表明它想要的逻辑域（如 orders 或 products），还可能表明它想要的数据类型，或者甚至提供用于身份验证的凭证。这种提示被称为 **header**。

### Header

Header 是传递信息的概念，它可以指示内容类型、内容大小，或者作为验证令牌（例如用于身份验证）。

Header 既可以出现在 incoming request（ incoming request）中，也可以出现在 response 中。

### 服务不同类型的内容

服务不同类型的内容意味着我们在处理响应。为了服务各种内容类型，我们需要在响应上指示其内容类型，这样消费客户端就知道如何解析它（在某些情况下，像浏览器这样的客户端可以通过内容嗅探（content sniffing）自行判断）。

要服务特定类型的内容，你需要做两件事：

*   **设置内容类型**，通过调用：

    ```
    1  w.Header().Set("Content-Type", "image/jpeg")
    ```

    这里的内容类型是 JPEG 子类型的图像。你可以设置的内容类型有 plain text、CSS、JSON、XML 等多种。

*   **生成响应**。生成响应意味着向响应流写入数据。这可以通过调用 `ResponseWriter` 实例的 `Write()` 方法来完成。还有其他可以写入该流的方法。

### 服务图片数据

要服务图片，你需要将其加载到内存中，设置内容类型，然后将其写入响应流，如下所示：

```
 1 func GetImage(w http.ResponseWriter, r *http.Request) {
 2     f, _ := os.Open("/image.jpg")
 3     
 4     // 将整个 JPG 文件读取到内存中。
 5     reader := bufio.NewReader(f)
 6     content, _ := ioutil.ReadAll(reader)
 7     
 8     // 设置 Content-Type 头。
 9     w.Header().Set("Content-Type", "image/jpeg")
10     
11     // 将图片写入响应。
12     w.Write(content)
13 }
```

*   首先，我们打开图片：

    ```
    1  f, _ := os.Open("/image.jpg")
    ```

*   其次，我们将文件读取到内存中：

    ```
    1  reader := bufio.NewReader(f)
    2  content, _ := ioutil.ReadAll(reader)
    ```

*   第三步，设置 `Content-Type` 头，指示它是 JPEG 图像，值为 “image/jpeg”：

    ```
    1  w.Header().Set("Content-Type", "image/jpeg")
    ```

*   最后，我们将内容写入响应：

    ```
    1  w.Write(content)
    ```

### 服务 JSON 数据

与服务图片类似，我们需要遵循相同的步骤：配置正确的 content-type 头，然后构建响应。以下是代码示例：

```
 1 package main
 2 
 3 import (
 4   "encoding/json"
 5 )
 6 
 7 type Person struct {
 8   Id int
 9   Name string
10 }
11 
12 func ReturnJson(w http.ResponseWriter, r *http.Request) {
13   w.Header().Set("Content-Type", "application/json")
14 
15   p := Person {
16     Id: 1
17     Name: "a person"
18   }
19 
20   json.NewEncoder(w).Encode(p)
21 }
22 
23 func main() {
24   http.HandleFunc("/json", ReturnJson)
25 }
```

*   首先，通过设置值 “application/json” 来设置内容类型：

    ```
    1  w.Header().Set("Content-Type", "application/json")
    ```

*   其次，构建我们要发送的数据：

    ```
    1  p := Person {
    2   Id: 1
    3   Name: "a person"
    4 }
    ```

*   最后，使用 `json.NewEncoder()` 编码数据并写入响应流：

    ```
    1  json.NewEncoder(w).Encode(p)
    ```

也可以使用 `Marshal()` 函数，例如：

```
1 package main
2 
3 import (
4   "encoding/json"
5 )
6 
7 func ReturnJson(w http.ResponseWriter, r *http.Request) {
8     w.Header().Set("Content-Type", "application/json")
9 
10    p := Person {
11      Id: 1
12      Name: "a person"
13    }
14 
15    data, _ := json.Marshal(p)
16    w.Write(data)
17 }
18 
19 func main() {
20    http.HandleFunc("/json", ReturnJson)
21 }
```




## Working with the request

存在多种方式，除了标题，还可以指示服务器程序执行什么操作：

- **HTTP verb**，HTTP verb 表达意图。POST verb 表示创建资源，GET verb 表示只读取数据等。本章后面会介绍更多 HTTP verbs。下面这两个请求含义不同：

```
1    GET /products # 获取产品列表
2    POST /products # 创建新产品资源
```

- **body**，body 可以包含负载，即我们可以用来创建或更新资源的数据。以下是一个示例：

```
1    {
2      "name" : "a new product" 
3    }
```

*   **router parameters**。在路由请求中，可以有携带意义的参数。如果客户端请求 `/products/5`，则 5 可能代表唯一标识的产品 ID 5。

*   **query parameter**。在路由末尾可以有查询部分，用于进一步指示请求，例如缩小返回数据的大小。查询部分是否以问号开头，并由键值对用 ampersands（&）分隔，例如：`/products?page=1&pageSize=20`。

### 解析 body

请求包含 `Body` 属性。根据 body 内容，可能需要进行解码。以下代码演示了解码 JSON 并将其写入响应流：

```
 1 package main
 2 
 3 import (
 4   "fmt"
 5   "encoding/json"
 6 )
 7 
 8 type Person struct {
 9   Id int
10   Name string
11 }
12 
13 func handleRequest(w http.ResponseWriter, r *http.Request) {
14   var p Person
15 
16   json.NewDecoder(r.Body).Decode(&p)
17   // save person to storage
18 
19   fmt.Fprintf(w)
20 }
21 
22 func main() {
23   mux := http.NewServeMux()
24   mux.HandleFunc("/person/", handleRequest)
25 
26   err := http.ListenAndServe(":4000", mux)
27 }
```

### 读取路由参数

没有内置方法来访问路由参数，需要手动解析，例如：

```
1 tokens := strings.Split(r.URL.Path, "/")
2 // 检查每个部分
```

或者使用正则表达式解析，或者使用如下库：

*   [httprouter](https://github.com/julienschmidt/httprouter)

*   [Gorilla Mux](http://www.gorillatoolkit.org/pkg/mux)

以下是使用 `httprouter` 的示例：

```
 1 func Hello(w http.ResponseWriter, r *http.Request, ps httprouter.Params) {
 2     fmt.Fprintf(w, "The id us, %s!\n", ps.ByName("id"))
 3 }
 4 
 5 func main() {
 6     router := httprouter.New()
 7     router.GET("/products/:id", Hello)
 8 
 9     log.Fatal(http.ListenAndServe(":8080", router))
10 }
```

### 读取查询参数

查询部分可通过请求实例的 `URL` 属性的 `Query()` 函数访问：

```
1 r.URL // /products?page=3&pageSize=20
2 r.URL.Query() // ?page=3&pageSize=20
```

访问特定参数时，`Query()` 函数返回 `Values` map：

```
1 r.URL.Query()["page"] // 3
```

也可以使用 `Get()` 函数，但仅在只有一个参数时有效：

```
1 r.URL.Query().Get("page")
```

### HTTP 方法

方法含义不同，应按不同方式处理。访问请求方法，使用 `Method` 属性 `r`：

```
1 r.Method
```

HTTP 包中定义了 `MethodGet`、`MethodPost` 等常量，可这样使用：

```
1 func handleRoute(w http.ResponseWriter, r *http.Request) {
2   if r.Method == http.MethodGet {
3     fmt.Println("It's a GET request") 
4   }
5 }
```

## ServeMux，更好的方式

此前通过 `ListenAndServe()` 传入端口参数和 `nil` 创建 HTTP 服务器。另一种方式是使用 `ServeMux`。`ServeMux` 也称为路由器，与直接使用 `http` 添加路由不同，它通过 `ServeMux` 添加路由。

以下示例展示了使用 `ServeMux`：

```
1 mux := http.NewServeMux()
2 mux.Handle("/hello", handleHello)
3 http.ListenAndServe(":8090", mux)
```

在上述代码中，通过 `NewServeMux()` 创建 `ServeMux` 实例，使用 `Handle()` 设置路由和处理函数，最后调用 `ListenAndServe()` 并传入 `mux` 而非 `nil`。

相比之前的方式，使用 `ServeMux` 更好，因为：

- 避免使用 `DefaultServeMux` 可能暴露探测端点，这是不安全的。
- 直接将路由与 `http` 绑定会改变全局状态，这在 Go 中通常被视为不佳实践。

## 任务 - 构建第一个 Web 应用

你的 Web 应用至少需要一个路由。该路由应向响应流写入内容。Web 应用应在特定端口启动，例如 5500。

## 解决方案

```
 1 package main
 2 
 3 import (
 4   "fmt"
 5   "net/http"
 6 )
 7 
 8 func handleRequest(w http.ResponseWrite, r *http.Request) {
 9   fmt.Fprintf(w, "Hi there")
10 }
11 
12 func main() {
13   http.HandleFunc("/hello", handleRequest) 
14   http.ListenAndServe(":8090", nil)
15 }
```

## 挑战

*   列出请求详情，如路由、使用的 HTTP 方法和查询参数。
*   尝试服务不同类型的数据，如 JSON 或图片。

## 使用日志库进行更好的日志记录

编写代码后，你会发现早期需要将内容打印到屏幕，有时还需要写入文件或日志服务。通常需要记录的是什么类型的日志。

## 介绍

本章将学习以下内容：

*   为什么以及如何记录日志。

*   使用 `log` 库。

## 记录日志的原因

有很多记录日志的原因，以下是一些：

*   **信息**，可能需要记录一些对使用程序的人有用的信息。

*   **成功**。成功消息比普通信息更具意义，表明操作成功。

*   **警告**。警告表示发生了值得注意的事件，通常不严重到停止程序，但应引起警惕，例如内存即将耗尽。

*   **错误**。出现错误时，程序可能进入无法继续的状态。

*   **性能**。记录操作耗时有助于优化性能。

*   **其他**。还有其他记录原因，通常与业务相关。

## 记录内容

一般规则是记录得越多越好，尤其是错误信息，需要记录：

*   发生时间
*   发生了什么
*   具体错误信息

对于每种情况，应明确日志用途，是否团队通过这些日志工作，以及日志内容对团队有何帮助。可以尝试与相关团队成员沟通。

## 使用 `log`

通常在可能出错的地方记录日志，如发起网络请求、处理 I/O 操作等。

记录日志的通用指南：

*   **无效输入**。如果程序可能返回错误响应，例如在转换/强制类型时遇到问题，或接收到意外输入。

*   **错误状态**。当程序进入无法恢复的状态，例如无法从数据源获取数据批次时。

不必在每行代码中记录日志。

### 标准日志 `Println()`

使用 `log` 包的 `Println()` 函数生成标准日志消息。它接受字符串并生成包含日期、时间和错误信息的日志消息。




## 使用字符串

我们需要以不同方式处理字符串的原因有很多。下面列出了一些你可能会遇到的情况，而 `strings` 库为这些情况提供了解决方案：

*   **用户输入**，或其他存储类型可能包含特殊字符，需要进行处理。

*   **检查**，字符串是否包含我们业务逻辑所需的内容？

*   **解析**，将文件拆分直到我们得到所需的内容，例如数字或日期。

*   **呈现**，有时我们需要以特定方式在 UI 中展示文本，例如突出显示某些信息。

## 处理特殊字符

假设我们读取用户输入，并且希望将其解释为数字。为了让我们的程序更健壮，我们接受用户输入可能包含空格或换行字符。下面的输入应该被允许：

```
1 114
2    114
3 114\n
```

为此，我们有三种感兴趣的方法可以帮助我们处理这种情况，分别是 `Trim()`、`TrimLeft()` 和 `TrimRight()`。

*   `Trim()`，它的作用是删除两端的空白字符。

*   `TrimLeft()`。它只删除左侧的空白字符，如果指定特殊字符，也能处理。

*   `TrimRight()`。它只删除右侧的空白字符，同样可以指定特殊字符。



使用正则表达式来解析文本

在本章中，你将学习如何使用正则表达式（RegEx）来搜索和替换文本。

## 什么是 RegEx 以及用途

正则表达式（RegEx）也称为正则，用于查找和替换文本。技术上，RegEx 是一系列字符，表示搜索模式。

## 为什么使用 RegEx

RegEx 的主要用途是查找文本、替换文本以及提取文本。虽然存在一些字符串库可以实现部分 RegEx 功能，但在某些情况下，使用 RegEx 可能更为合适。不过，RegEx 很难掌握，建议多学习其工作原理，因为它功能强大。

## 使用场景

RegEx 在许多不同的场景中被使用：

*   **文本编辑器、任何带有搜索功能的程序**。例如，Visual Studio Code 允许你在文件和文件夹中使用 RegEx 进行搜索。

*   **代码**，许多编程语言和运行时环境都提供 RegEx 库以帮助你使用正则表达式。

## 你的第一个 RegEx

让我们构建一个简单的 RegEx 来感受它的用法。以下是示例：

```
1 an
```

如果将搜索模式 `an` 应用于以下文本：

```
1 highlands is a part of Scotland
```

它会匹配如下：

> highl**an**ds is a part of Scotl**an**d

对于简单的情况，即查找特定单词在句子中的一或多个位置，像上面的模式足够。

### RegEx 在 Go

在 Go 中使用 RegEx 的第一步是使用 `regexp` 包。有两种方法：

*   直接使用 `regexp`，示例如下：

    ```
    1  matched, err := regexp.FindString("an", "highlands is a part of Scotland")
    ```

    这里会返回一个布尔值，表示是否存在匹配。

*   **编译**，即先编译正则表达式，然后调用其方法，例如：

    ```
    1  r, _ := regexp.Compile("an")
    2  matches := r.FindAllString("highlands is a part of Scotland", -1)
    ```

    上述代码会返回一个字符串数组，包含所有匹配项，这里是 `["an", "an"]`。

    使用编译方式，你可以调用更多函数。

## 字符类

字符类能够区分不同类型的字符，例如换行符、数字、字母等。

以下是一些常见字符类及其描述：

| 类型 | 描述 |

| --- | --- |

| . | 匹配除换行符外的任意字符 |

| \\ | 转义后面的字符 |

| \\w | 匹配拉丁字母表中的字符，包括下划线 `_` |

| \\d | 匹配任何数字 |

| D | 与 \\d 相反，匹配非数字字符 |

| \\s | 匹配空白字符，如空格、制表符、换行符等 |

示例：

```
1 matched, err := regexp.FindString("\d", "abc123")
```

上述代码会因 "123" 而匹配成功，但对 "abc" 不会匹配，因为其中没有数字。

## 重复

如果想表达重复，有两个特殊字符：

*   `+`，匹配 1 到多个字符。

    ```
    1  \w+
    ```

    给定字符串 "aaaa bab"，它会匹配：

    **aaaaab** **bab** （匹配字符，不包括空格）

    ```
    1  r, _ := regexp.Compile("\\w+")
    2  matches := r.FindAllString("aaaa bab", -1)
    ```

    注意需要额外的 `\`，因为在构建正则表达式时需要转义。

*   `*`，匹配 0 到多个字符。例如，要匹配以 "PA" 开头，后面可包含 0 或多个数字的邮政地址，可以使用 `*` 如下：




1 package main
 2 
 3 import (
 4  "fmt"
 5  "log"
 6  "regexp"
 7 )
 8 
 9 func main() {
10  var url string
11  fmt.Println("Type URL: ")
12  fmt.Scan(&url)
13 
14  r, err := regexp.Compile(`^(?P<protocol>\w+):\/\/(?P<domain>\w+\.\w+)\/(?P<route>\w+
15 +)\/?`)
16  if err != nil {
17   log.Fatal("Error compiling: ", err)
18  }
19  m := r.FindStringSubmatch(url)
20  if m == nil {
21   panic("mo match")
22  }
23  result := make(map[string]string)
24  for i, name := range r.SubexpNames() {
25   if i != 0 && name != "" {
26    result[name] = m[i]
27   }
28  }
29  fmt.Println("The URL consist of:")
30  fmt.Println(result["protocol"])
31  fmt.Println(result["domain"])
32  fmt.Println(result["route"])
33 }
 4




-   [将 *books.xml* 文件中的 author 替换为 name](https://wiki.example.org/books_xml_author_replace) 和 [将 cost 替换为 price](https://wiki.example.org/books_xml_cost_replace)。

TIP: 你可能需要执行两次替换。

``` 
 1 package main 
 2 
 3 import ( 
 4  "fmt" 
 5  "regexp" 
 6 ) 
 7 
 8 func main() { 
 9  file := `<books>
10     <book>
11       <author>Shakespeare</author>
12       <title>Romeo and Juliet</title>
13       <pages>400</pages>
14       <type>paperback</type>
15       <cost>17</cost>
16     </book>
17     <book>
18       <author>Shakespeare</author>
19       <title>Hamlet</title>
20       <pages>270</pages>
21       <type>paperback</type>
22       <cost>15</cost>
23     </book>
24 </books>`
25 
26  r := regexp.MustCompile(`(\<\/?)(title)(\>)`)
27  s := r.ReplaceAllString(file, "${1}name${3}")
28  fmt.Println(s) 
29 
30  r = regexp.MustCompile(`(\<\/?)(cost)(\>)`)
31  s = r.ReplaceAllString(s, "${1}price${3}")
32  fmt.Println(s) 
33 } 
```

## Goroutines and channels

A goroutine is a lightweight thread managed by the Go runtime.

Channels is how you communicate between routines.

## Introduction

In this chapter you will:

*   Understand the difference between concurrency and parallelism

*   Use Goroutines to run your functions

*   Create and use channels to communicate between your Goroutines

*   Apply Goroutines to an app that searches files for faster execution.

## Concurrency, what’s the benefit

Concurrency is the task of running and managing the multiple computations at the same time. While *parallelism* is the task of running multiple computations simultaneously.

So what are some benefits:

*   **Faster processing**. The benefit is getting tasks done faster. Imagine that you are searching a computer for files, or processing data, if it’s possible to work on these workloads in parallel, you end up getting the response back faster.

*   **Responsive apps** Another benefit is getting more responsive apps. If you have an app with a UI, imagine it would be great if you can perform some background work without interrupting the responsiveness of the UI.

## Goroutines

A goroutine is a lightweight thread managed by the Go runtime. What you do is to add the keyword `go` in front of a function. Here’s an example:

```
 1 go myFunction()
```

Imagine the following code running, what would happen?

```
 1 package main 
 2 
 3 import "fmt" 
 4 
 5 func myFunction() { 
 6  for i := 0; i < 3; i++ { 
 7   fmt.Println("my function: ", i) 
 8  } 
 9 } 
10 func anotherFunction() { 
11  for i := 4; i <7; i++ { 
12   fmt.Println("another function: ", i) 
13  } 
14 } 
15 
16 func main() { 
17  go myFunction() 
18  anotherFunction() 
19 } 
```

It would only print the result from `anotherFunction()` as it takes a short while for the go routine to start up. You can have the go routine execute as well by adding a little delay, like so:

```
 1 func main() { 
2  go myFunction() 
3  anotherFunction() 
4  time.Sleep(1 * time.Second) 
5 } 
```

The result is now the following:

```
1 another function:  4
2 another function:  5
3 another function:  6
4 my function:  0
5 my function:  1
6 my function:  2
```

The function with the go routine finishes last. Lets modify the code slightly and have the two functions use a delay, so we simulate workloads taking different time to finish:

```
 1 func myFunction() { 
2  time.Sleep(1500 * time.Millisecond) 
3  for i := 0; i < 3; i++ { 
4   fmt.Println("my function: ", i) 
5  } 
6 } 
7 func anotherFunction() { 
8  time.Sleep(500 * time.Millisecond) 
9  for i := 4; i < 7; i++ { 
10   fmt.Println("another function: ", i) 
11  } 
12 } 
13 
14 func main() { 
15  go myFunction() 
16  go anotherFunction() 
17  time.Sleep(2 * time.Second) 
18 } 
```

at this point, `anotherFunction()` finishes first as it has the shortest delay, which is to be expected. Here’s what the output looks like now:

```
1 another function:  4
2 another function:  5
3 another function:  6
4 my function:  0
5 my function:  1
6 my function:  2
```

### Use case - a file search

Imagine you have case where you need to find a file on disk. If you write a function like so, it will search a directory and report back the result if the file is found:

```
 1 func SearchFiles(dir string, lookFor string) string { 
 2  log.Println("[SEARCHING] ", dir) 
 3  files, err := ioutil.ReadDir(dir) 
 4  if err != nil { 
 5   log.Fatal(err) 
 6  } 
 7 
 8  for _, file := range files { 
 9   log.Println(dir+file.Name(), file.IsDir()) 
10   if file.Name() == lookFor { 
11    return "[FOUND] " + filepath.Join(dir, file.Name()) 
12   } 
13  } 
14  return "[NOT FOUND] " + dir 
15 } 
```

Imagine you now run this code like so, to search many directories:

```
 1 result := make([]string, 0) 
2 append(result, SearchFile("./tmp", "myfile.txt")) 
3 append(result, SearchFile("./tmp2", "myfile.txt")) 
4 append(result, SearchFile("./tmp3", "myfile.txt")) 
5 append(result, SearchFile("./tmp4", "myfile.txt")) 
6 
7 for i := 0 i< len(result); i++ { 
8   fmt.Println(result[i]) 
9 } 
```

If found, you will get an output similar to the below, depending on whether *myfile.txt* is found in any of the searched directories:

```
1 [FOUND] ./tmp/myfile.txt
2 [NOT FOUND] ./tmp2/myfile.txt
3 [NOT FOUND] ./tmp3/myfile.txt
4 [NOT FOUND] ./tmp4/myfile.txt
```

Now to speed up this process, it would be great if you are able to search many directories at once, so you could type something like so:

```
 1 go SearchFile("./tmp", "myfile.txt")
2 go SearchFile("./tmp2", "myfile.txt")
3 go SearchFile("./tmp3", "myfile.txt")
4 go SearchFile("./tmp4", "myfile.txt")
```

This works, it now searches all directories, in parallel. However, now we don’t have a way to get the response back as we can’t write like so:

```
 1 result := make([]string, 0)
2 go append(result,SearchFile("./tmp", "myfile.txt")) // won't compile, says "go disca\
3 rds results"
```

So how can we get the result from a go routine, the answer is by using channels, so lets discuss those next.

## Channels

A channel is how we can communicate cross go routines but also between go routines and the part of our code not using a go routine.

The idea is to send a value to a channel, and have part of our code listen to values from a channel.

### Creating a channel

To create a channel, you need the keyword `chan` and the data type of the messages you are about to send into it. Here’s an example:

```
 1 ch := make(chan int)
```

In the above example, a channel `ch` will be created that accepts messages of type `int`.

### Sending a value to a channel

To send to a channel, you need to use this operator `<-`, it look like a left pointing arrow and is meant to be read as the direction something is sent. Here’s an example of sending a message to a channel:

```
 1 ch <- 2
```

In the above code, the number 2 is sent into the channel `ch`.

### Listening to a channel

To listen to a channel, you again use the arrow `<-`, but this time you need a receiving variable on the left side and the channel on the right side, like so:

```
 1 value := <- ch
```

### Matching sending and receiving

Let’s say you have the following code:

```
 1 package main 
 2 
 3 import "fmt" 
 4 
 5 func produceResults(ch chan int) { 
 6  ch <- 1 
 7  ch <- 2 
 8 } 
 9 
10 func main() { 
11  ch := make(chan int) 
12  go produceResults(ch) 
13 
14  var result int 
15  result = <-ch 
16  fmt.Println(result) 
17  result = <-ch 
18  fmt.Println(result) 
19 } 
```

You are invoking `produceResults()` and it sends messages to the channel twice:

```
1 ch <- 1
2 ch <- 2
```

in `main()`, you receive the results:



## 使用数据库

## 介绍

在本章节中，你将：

*   创建数据库及其结构。

*   向数据库写入数据。

*   从数据库读取数据。

## 选择 sqlite 驱动

要连接 sqlite 数据库，我们有几个库可供选择。这些库将为你提供必要的 sqlite 驱动，以便成功连接到你的数据库。以下是一些常见的库：

*   SQLite (使用 cgo)：[`github.com/mattn/go-sqlite3`](https://github.com/mattn/go-sqlite3) [*]
*   SQLite (使用 cgo)：[`github.com/gwenn/gosqlite`](https://github.com/gwenn/gosqlite) - 支持 SQLite 动态数据类型
*   SQLite (使用 cgo)：[`github.com/mxk/go-sqlite`](https://github.com/mxk/go-sqlite)
*   SQLite: (使用 cgo)：[`github.com/rsc/sqlite`](https://github.com/rsc/sqlite)
*   SQLite: (纯 go)：[`modernc.org/sqlite`](https://modernc.org/sqlite)

参考此链接查看其他数据库的库：

*   [`github.com/golang/go/wiki/SQLDrivers`](https://github.com/golang/go/wiki/SQLDrivers)

## 使用 sqlite3 从控制台

要使用控制台与你的数据库工作，使用 sqlite3 是有益的。请参阅官方 [下载页面](https://www.sqlite.org/download.html) 获取 sqlite，并确保选择适用于你操作系统的可执行文件。安装 sqlite 将提供一个可执行文件。

使用可执行文件，你可以：

*   创建数据库。

*   运行 SQL 命令。

*   运行其他由可执行文件支持的命令。

### 创建数据库

要创建数据库，你需要指定数据库名称，例如：

```
1 sqlite3 activities.db
```

前面的命令将在名为“activities.db”的文件中创建一个数据库。

> 同时，这也会启动一个 shell，你可以在其中执行 SQL 命令和 sqlite3 支持的其他命令。

### 运行 SQL 命令

在 shell 中运行 SQL 命令时，输入 SQL 并以分号 `;` 结尾。

```
1 CREATE TABLE `person` (
2         `uid` INTEGER PRIMARY KEY AUTOINCREMENT,
3         `name` VARCHAR(64) NULL,
4         `lastname` VARCHAR(64) NULL,
5         `created` DATE NULL
6     );
```

### 退出 shell

完成工作后，你可以通过输入 `.exit` 来退出 shell：

```
1 .exit
```

## 通过 Go 与数据库通信

要通过 Go 与数据库通信，需要按以下步骤操作：

1.  **创建项目**。你需要创建一个项目，以便导入包含你 sqlite 驱动的 Go 包。通过运行 `go mod init` 创建项目。以下是一个示例：

    ```
    1 go mod init "example-project"
    ```

2.  **添加导入**。一旦你拥有所需的包，需要在导入部分引用它们：

    ```
    1 import (
    2   "database/sql"
    3   _ "github.com/mattn/go-sqlite3"
    4  )
    ```

    上面，我们使用了两个包，“database/sql”提供运行查询和语句的接口，“github.com/mattn/go-sqlite3”包含驱动，使我们能够连接到数据库。

3.  **建立连接**。要连接到数据库，你需要调用 `sql` 实例上的 `Open()` 函数，如下所示：

    ```
    1 db, err := sql.Open("sqlite3", "./mydb.db")
    ```

    在前面的命令中，我们首先指定数据库类型，然后在第二个参数中指定数据库名称及其位置。我们会得到一个 `*sql.DB` 类型的数据库实例。

4.  **运行查询**。此时，我们可以自由运行查询。你使用 `Query()` 函数，并给出一个 SQL 语句，例如：

    ```
    1 rows, err := db.Query("SELECT * FROM person")   
    ```

    要遍历结果，你可以使用类似下面的 for 循环：




-   [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**Richard Feynman**。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
if (condVar > someVal) {console.log("xxx")}
```

1 for rows.Next() {
    var uid int
    var name string
    var lastname string
    var created time.Time
    err = rows.Scan(&uid, &name, &lastname, &created)
}

Run prepared statements. Prepared statements are SQL statements where we can provide parameter values at a later point. You call the `Prepare()` function with `?` as placeholders where there will be data inserted:

stmt, err := db.Prepare("UPDATE person set lastname=? where uid=?")

To run the statement against the database, you can call `Exec()`:

res, err := stmt.Exec("smith", 1)

The `res` instance coming back has a function `RowsAffected()` that returns the number of affected rows:

affected, _ := res.RowsAffected()

Getting affected rows is a good indicator that you actually changed something.

Close the database connection. You should close the database when you’re done with it like so:

db.Close()

Create the database and populate it

We will create our database using the sqlite executable in the console.

1. Run `sqlite` to create the database and initialize the sqlite shell:

sqlite3 mydb.db
sqlite3SQLite version 3.32.3 2020-06-18 14:16:19
Enter ".help" for usage hints.

At this point, you have a database created. Next, we need some tables in there.

2. Run the following SQL command in the sqlite shell:

CREATE TABLE `person` (
        `uid` INTEGER PRIMARY KEY AUTOINCREMENT,
        `name` VARCHAR(64) NULL,
        `lastname` VARCHAR(64) NULL,
        `created` DATE NULL
    );

You know have the table “person” created. Next, we need some data in the table that we will interact with later in our Go code.

3. Run this SQL command to insert data into “person” table:

insert into person(name,lastname, created) values ("joe", "schmoo", '2021-01-01');

Great, we now have data in our table. Time to focus on the Go code next.

4. Run .exit to exit the database.

Create a project

Now we will create a Go project and some code able to access our database.

1. Create *db.go* and give it this content:

package main

import (
    "database/sql"
    "fmt"
    "log"
    _ "github.com/mattn/go-sqlite3"
)

func main() {
    db, err := sql.Open("sqlite3", "./mydb.db")
    if err != nil {
        log.Fatal(err)
    }
    fmt.Println("database open")

    fmt.Println("bye")

    fmt.Println("closing db")
    db.Close()
}

Next, lets initialize our Go project.

Run the following commands to create our project:

go mod init sql-demo

Run `go mo tidy`, to install the needed packages you specified in the import section of your program (this will download and add “github.com/mattn/go-sqlite3” to your project):

go mod tidy

Read data

Next, we will add a function capable of reading data.

Add a function `Read()` like so:

func Read(db *sql.DB) {
    rows, err := db.Query("SELECT * FROM person")

}

At this point, we have read the response into `rows`. Next, we need iterate on the response.

Add the following code, in `Read()` to iterate over the response:

for rows.Next() {
    var uid int
    var name string
    var lastname string
    var created time.Time
    err = rows.Scan(&uid, &name, &lastname, &created)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Println(uid)
    fmt.Println(name)
    fmt.Println(lastname)
    fmt.Println(created)
}

Create data

Now we will create code that will allow us to create data in our database.

Add a function `Create`:

func Create(db *sql.DB) {
    stmt, err := db.Prepare("INSERT INTO person(name, lastname, created) values(?,?,?)\
    ")

    if err != nil {
        log.Fatal(err)
    }
    res, err := stmt.Exec("Mrs", "Smith", "2022-01-01")
    if err != nil {
        log.Fatal(err)
    }
    affected, _ := res.RowsAffected()
    log.Printf("Affected rows %d", affected)
}

Update and delete data

Updating and deleting data takes on very similar approach to how to create data. You will use a statement that you prepare and then send in the real values. Below is the code for performing both these actions:

Update

func Update(db *sql.DB) {
    stmt, err := db.Prepare("UPDATE person set lastname=? where uid=?")
    if err != nil {
        log.Fatal(err)
    }
    res, err := stmt.Exec("smith", 1)
    if err != nil {
        log.Fatal(err)
    }
    affected, _ := res.RowsAffected()
    log.Printf("Affected rows %d", affected)
}

Delete

func Delete(db *sql.DB) {
    stmt, err := db.Prepare("delete from person where uid=?")
    if err != nil {
        log.Fatal(err)
    }
    res, err := stmt.Exec(1)
    if err != nil {
        log.Fatal(err)
    }
    affected, _ := res.RowsAffected()
    log.Printf("Affected rows %d", affected)
}




-   [使用 `ioutil` 库和其 `ReadFile()` 方法读取文本文件的内容](https://wiki.example.org/feynmans_learning_method) 如下：

```
 1   import (
 2     "io/ioutil"
 3     "log"
 4   )
 5   func main() {
 6     filebuffer, err := ioutil.ReadFile(path)
 7  
 8     if err != nil {
 9       log.Fatal(err)
10     }
11     var inputdata string = string(filebuffer) 
12   }
```

-   [使用 `os` 库创建文件并写入文本的方法](https://wiki.example.org/feynmans_learning_method) 如下：

```
 1  import (
 2   "os"
 3   "log"
 4  ) 
 5 
 6  f, err := os.Create(path)
 7  if err != nil {
 8   log.Fatal(err)
 9  }
10 
11  n, err := f.WriteString(content + "\n")
12  if err != nil {
13   log.Fatal(err)
14  }
15  fmt.Printf("wrote %d bytes\n", n)
16  f.Sync()
```

-   [使用 `os.OpenFile()` 追加内容到现有文件的方法](https://wiki.example.org/feynmans_learning_method) 如下：

```
1 f, err := os.OpenFile("text.log",
2  os.O_APPEND|os.O_CREATE|os.O_WRONLY, 0644)
3 if err != nil {
4  log.Println(err)
5 }
6 defer f.Close()
```

-   [在 `invoices.csv` 文件中逐行读取内容的方法](https://wiki.example.org/feynmans_learning_method) 如下：

```
 1 package main
 2 
 3 import (
 4  "fmt"
 5  "io/ioutil"
 6  "log"
 7  "strings"
 8 )
 9 
10 func main() {
11  var path = "invoices.csv"
12  filebuffer, err := ioutil.ReadFile(path)
13 
14  if err != nil {
15   log.Fatal(err)
16  }
17  var inputdata string = string(filebuffer)
18 
19  rows := strings.Split(inputdata, "\n")
20  for _, row := range rows {
21   fmt.Println("row:", row)
22  }
23 }
```

-   [在文件和目录操作章节中，分析文件元数据（如大小、修改时间、权限等）的方法](https://wiki.example.org/feynmans_learning_method) 如下：

```
1 fileStat, err := os.Stat(path)
2 fmt.Println("File Name:", fileStat.Name())        // Base name of the file
3 fmt.Println("Size:", fileStat.Size())             // Length in bytes for regular files
4 fmt.Println("Permissions:", fileStat.Mode())      // File mode bits
5 fmt.Println("Last Modified:", fileStat.ModTime()) // Last modification time
6 fmt.Println("Is Directory: ", fileStat.IsDir())   // Abbreviation for Mode().IsDir()
```

-   [复制文件的方法](https://wiki.example.org/feynmans_learning_method) 如下：

```
 1 // copies 'test.txt' and its content to 'copy.txt'
 2 src := "test.txt"
 3 dest := "copy.txt"
 4 
 5 srcFile, err := os.Open(src)
 6 if err != nil {
 7   log.Fatal(err)
 8 }
 9 defer srcFile.Close()
10 
11 newFile, err := os.Create(dest)
12 if err != nil {
13   log.Fatal(err)
14 }
15 defer newFile.Close()
16 
17 _, err = io.Copy(newFile, srcFile)
18 if err != nil {
19   log.Fatal(err)
20 }
```

-   [重命名文件的方法](https://wiki.example.org/feynmans_learning_method) 如下：




1 err := os.Rename(src, dest)

Remove file

To remove file, there’s a `Remove()` function you can use. Here’s how to use it:

```
1 err := os.Remove(path)
```

## Create dir

To create a directory, you can use the `MkdirAll()` function in the `os` library. However, you should check whether the directory exist first. The way to do that is to use the `IsNotExist()` function like so:

```
 1 _, err := os.Stat(dirName)
 2 
 3  if os.IsNotExist(err) {
 4   errDir := os.MkdirAll(dirName, 0755)
 5   if errDir != nil {
 6    log.Fatal(err)
 7   }
 8  } else if err != nil {
 9   log.Fatal("error creating dir")
10  } else {
11   log.Fatal("directory exist")
12  }
```

As you can see on the above code:

1.  you first use the `Stat()` function. The `Stat()` returns a `FileInfo` object or an error of type `PathError` if path doesn’t exist.

2.  `os.IsNotExist(err)`. This returns `true` if `err` is a `PathError`, i.e the path don’t exist, which is good, we want to create it.

3.  Finally, we call `os.MkdirAll(dirName, 0755)`. The 755 instruction is about permissions on the created directory, which gives the permissions, Read/Write/Execute, Read/Execute, Read/Execute. 755 is a common permission set on web servers. You essentially want to avoid anyone but you to modify the file.

## Read dir

Reading a directory is quite straight forward. You can use the `ReadDir()` function on the `io/ioutil` library. Here’s how you would read a directory:

```
1 files, err := ioutil.ReadDir(path)
```

`files` is an array of type `FileInfo`.

TODO, copy, rename, remove, check for existence

## Assignment

Create the following files and directories like so:

```
1 tmp/
2   a.txt
3   b.xt
4   subdir/
```

Your program should read the diretory *tmp* and for each entry list, if it’s a dir or a file, the size and when last modified.

The programs output should look something like:

```
1 Reading directory tmp:
2 Name, Type, Size, Modified
3 a.txt, file, 1kb, 2022-01-01
4 b.txt, file, 1kb, 2022-01-01
5 subdir, directory, 1kb, 2022-01-01
```

Solution

```
 1 package main
 2 
 3 import (
 4  "fmt"
 5  "io/ioutil"
 6  "log"
 7 )
 8 
 9 func GetType(isDir bool) string {
10  if isDir {
11   return "directory"
12  }
13  return "file"
14 }
15 
16 func main() {
17  var path string = "tmp"
18  files, err := ioutil.ReadDir(path)
19  if err != nil {
20   log.Fatal(err)
21  }
22  fmt.Println("Reading directory ", path)
23  fmt.Println("Name, Type, Size, Modified")
24  for _, file := range files {
25   if err != nil {
26    log.Fatal(err)
27   }
28   fmt.Printf("File Name: %s, ", file.Name())
29   fmt.Printf("Type: %s, ", GetType(file.IsDir()))
30   fmt.Printf("Size: %d, ", file.Size())             
31   fmt.Printf("Last Modified: %s, ", file.ModTime()) 
32   fmt.Print("\n")
33  }
34 }
```

