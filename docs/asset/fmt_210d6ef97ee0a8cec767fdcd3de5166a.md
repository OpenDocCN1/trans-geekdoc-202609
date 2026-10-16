
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

1.  创建一个名为 `main.go` 的文件，包含以下内容：

    ```
    package main

    import "fmt"

    func main() {

    }
    ```

2.  将以下代码添加到 `main()` 方法中：

    ```
    fmt.Println("Enter player names (separated by space or newline):")
    var player1, player2 string
    fmt.Scan(&player1, &player2)
    fmt.Println("Players are: ", player1, player2)
    ```

3.  使用 `go run main.go` 运行程序：

    ```
    go run main.go
    ```

    你应该看到以下输出：

    ```
    Enter player names (separated by space or newline):
    Alice Bob
    Players are:  Alice Bob
    ```

## 🚀 挑战

尝试修改程序，使其首先输入玩家数量，然后确保所有玩家都有名称。以下是该程序的示例输出：

```
Enter number of players: 
3
Enter Player 1 name: 
Alice
Enter Player 2 name:
Bob
Enter Player 3 name:
Jean
Players are: Alice Bob Jean
```

## 解决方案

```
package main

import "fmt"

func main() {
 fmt.Println("Enter player names (separated by space):")
 var player1, player2 string
 fmt.Scan(&player1, &player2)
 fmt.Println("Players are: ", player1, player2)
}
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
func main(){
}
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
func Divide(nominator int, divider int) float32 {
  if divider == 0 {
    panic("can't divide by 0")
  }
  return float32(nominator) / float32(divider)
}
```

它包含一个 `if` 检查。如果 `divider` 为 `0`，则调用 `panic()`。那么会发生什么呢？你会看到类似以下内容：

```
panic: can't divide by 0

goroutine 1 [running]:
main.Divide(...)
        /<path>/panic.go:20
main.main()
        /<path>/panic.go:33 +0x96
exit status 2
```

顶部是你传递给 `panic()` 的错误字符串，即“can’t divide by 0”。然后是堆栈跟踪，指示错误发生的位置。从下往上看，错误始于第 33 行，然后是第 20 行，即：

```
panic("can't divide by 0")
```

因此，我们有了一个方法来保护自己免受不想要的输入值的影响。但崩溃程序是否必要？在某些情况下是，在其他情况下则不是。对于后者，我们有 `recover()`。

### 使用 `recover()` 捕获错误

使用 `recover()` 是为了捕获错误，使我们的程序能够继续运行。在继续之前，我们需要先了解一个概念，即 `defer`。`defer` 是一种语言构造，用于延迟函数的执行，直到最近的函数返回。以下是一个示例：

```
defer fmt.Println("second")
fmt.Println("first")
```

运行此程序，你应该看到：

```
first
second
```

> 将 `defer` 视为最后发生的操作。

在捕获错误的上下文中，捕获错误（如果你想捕获它）应该是最后发生的操作。让我们再看 `Divide()` 函数：

```
func Divide(nominator int, divider int) float32 {
  defer errorHandler()
  if divider == 0 {
    panic("can't divide by 0")
  }
  return float32(nominator) / float32(divider)
}
```

可以看到，它现在有一行 `defer errorHandler()`，这将是最后执行的操作。根据 `divider` 的值，它会调用 `panic()` 或 `return` 语句作为最后一步。

那么 `errorHandler()` 是什么样子呢？

```
func errorHandler() {
  if r := recover(); r != nil {
    fmt.Println("Recovered ", r)
  }
}
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
if (condVar > someVal) {console.log("xxx")}
```

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
    func TestAdd(t *testing.T) {}
    ```

*   断言结果的方法。`testing` 还暴露了 `t.Errorf()`。通过以字符串形式调用它，测试即视为失败。要通过测试，你什么都不需要做：

    ```
    t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
    ```

下面是一个测试函数的示例：

```
func TestAdd(t *testing.T) {
  total := Add(2, 2)
  if total != 4 {
   t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
  }
  t.Log("running TestAdd")
}
```

*   首先，调用要测试的代码：

    ```
    total := Add(2, 2)
    ```

*   其次，进行断言，以查看是否成功或失败：

    ```
    if total != 4 {
      t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
    }
    ```

    如果结果不是预期的，则调用 `t.Errorf()` 来指出出错的地方。

## 你的第一个测试

确保你已创建了一个使用 `go mod init` 的项目，然后创建类似下面的文件结构：

```
main.go
math/
  math.go
  math_test.go
```

接下来要做的是创建测试文件。你希望将测试文件尽可能贴近你要测试的代码。因为你要测试 *math.go*，所以在 math/ 目录下创建 `math_test.go` 文件，如下所示：

```
main.go
math/
  math.go
  math_test.go
```

### 编写并运行你的第一个测试

现在你已经拥有上述文件结构，确保 *math_test.go* 文件包含以下内容：

```
package math

import (
  "testing"
)

func TestAdd(t *testing.T) {
  total := Add(2, 2)
  if total != 4 {
    t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
  }
  t.Log("running TestAdd")
}
```

运行测试时，你需要调用 `go test` 命令。以下是不同运行测试的方式：

*   `go test`，运行当前工作目录中的测试。示例输出：

    ```
    ok      test-example/math       0.258s
    ```

*   `go test -v`，运行详细版本。可能的输出如下：

    ```
    === RUN   TestAdd
    math_test.go:12: running TestAdd

    --- PASS: TestAdd (0.00s)
    PASS
    ok      test-example/math       0.422s
    ```

    在详细版本中，你可以看到测试的名称以及是否失败。

*   `go test ./..`，递归运行。如果你以此方式运行命令，它会运行子文件夹中的所有测试。

## 控制测试运行

有几种方式可以控制测试的运行数量。以下是一些方法：

- **通过模式运行测试**。你可以提供一个模式，让 Go 运行部分测试，该模式通过子串匹配或甚至在特定深度进行匹配。例如：

    ```
    go test -run <pattern>
    ```

- **跳过测试**。在测试中调用 `t.Skip()`，该测试将被跳过。

*   **运行单个测试**。你可以通过运行指定包和测试名称的模式来运行单个测试，例如：

    ```
    go test -run TestAdd
    ```

`go test -run TestAdd ./math`

Here’s the package is called math and the name of the test is `TestAdd()`。

## Coverage

There’s a built-in tool for dealing with coverage. To learn more about the tool, you can type:

```
go tool cover -help
```
