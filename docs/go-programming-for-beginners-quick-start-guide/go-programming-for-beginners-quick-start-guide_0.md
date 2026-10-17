
# GO 语言编程初学者快速启动指南

## 前言

“Go 语言编程”涵盖了 Go 语言的所有核心知识。你可以快速、轻松地学习 Go 编程的完整基础技能。

本书包含了 60 多个针对初学者的实用示例，并包含了大学考试、工程师认证考试以及工作面试的测试题与答案。

**注意：** 本书仅适用于 Go 初学者，不适合有经验的 Go 程序员。

### 源代码下载

本书提供了源代码下载；你可以下载源代码以更好地学习，或者将源代码复制到你喜喜欢的编辑器中测试程序。

源代码下载链接：[`forms.aweber.com/form/34/1805492434.htm`](https://forms.aweber.com/form/34/1805492434.htm)

## 什么是 Go?

Go 是一种由 Google 在 2009 年推出的开源、高效的编程语言。它具有强大的并发支持，并且易于学习。它具有许多现代特性。

## 安装 Go

你可以从以下链接下载安装包：[`golang.org/dl/`](https://golang.org/dl/)

1. 根据你的操作系统下载对应的安装程序。
2. 运行安装程序并按照提示完成安装。
3. 默认情况下，Go 将安装在 `C:\Go` 目录。
4. 安装完成后，点击“完成”。
5. 下载链接：[`forms.aweber.com/form/34/1805492434.htm`](https://forms.aweber.com/form/34/1805492434.htm)

## 环境变量

安装 Go 后，你需要将 `C:\Go\bin` 添加到环境变量的 `PATH` 中。请前往“控制面板” > “系统” > “高级系统” > “环境变量” > “Path” > “编辑” > “新建”。将 `C:\Go\bin` 添加到末尾。

注意：不同 Windows 版本的界面可能不同。请重启电脑使设置生效。

## Go 的第一个程序

请在 `C:\` 下创建一个名为 `myGo` 的工作文件夹，打开记事本并将以下代码写入编辑器。

示例 1.1

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

将文件保存为 `hello.go` 位于 `C:\myGo` 中。打开命令行（cmd），输入以下命令：

输出：`Hello World!`

解释：`package main` 定义包名为 `main`。每个 Go 应用程序必须包含名为 `main` 的包。导入的 `fmt` 包包含了 I/O 函数。`func main()` 是程序中执行的第一个函数。`fmt.Println("Hello, World!")` 输出文本 `Hello, World!`。`C:\Windows\system32>cd\` 返回 C: 根目录。`C:\cd myGo` 进入 `myGo` 文件夹。`go run` 是执行 Go 程序的命令。

## 注释

```go
//
/* ... */
```

`//` 是单行注释的符号。`/*` 和 `*/` 是多行注释的符号。注释不会被编译。Go 编译器会忽略所有注释。

示例 1.2

```go
package main // 包声明

import "fmt"

func main() {
    // 定义 main 函数
    fmt.Println("Hello, World!")
}
/* 上述代码的输出是：Hello, World! */
```

请使用 `go run` 命令运行此程序并检查结果。

# 标识符

标识符用于命名变量、函数、表达式等。标识符由一个或多个字母（A~Z 和 a~z）、数字（0~9）和下划线组成，但第一个字符必须是字母或下划线。标识符的第一个字符不能是数字。

以下标识符是有效的：`myVariable`、`_Variable`、`variable100`。

以下标识符是无效的：

- `continue` // “continue”是 Go 语言的关键字
- `100Variable` // 以数字开头

# 总结

`"package main"` 定义包名为 `main`。每个 Go 应用必须包含一个名为 `main` 的包。导入包 `"fmt"` 包含了 I/O 函数。`func main()` 是 Go 应用中执行的第一个函数。`fmt.Println("Hello, World! ")` 输出文本 `"Hello, World! "`。`//` 是单行注释的符号。`/*` 和 `*/` 是多行注释的符号。注释不会被编译。Go 编译器将忽略所有注释。

# 第 2 小时

## 分隔符

在 Go 语言中，每个语句不需要分号来结束行。例如：

```go
fmt.Println("Hi, My friend! ")
fmt.Println("Hi, Guy! ")
```

上述代码中有两行，其中一行代表一个语句的结束，每个语句都不需要分号来结束行。

## 关于 "{"

`{` 不能放在单行上，因此以下代码会在运行时产生错误。例如：

```go
func main() {
    // error
    fmt.Println("Hello, World! ")
}
```

以下代码是正确的：

```go
func main() {
    // { 放在这里，是正确的！
    fmt.Println("Hello, World! ")
}
```

## 关键字

Go 语言中有 25 个关键字。

| break | default |
| :--- | :--- |
| case | defer |
| chan | else |
| const | fallthrough |
| continue | for |

关键字不能作为变量、常量和函数等的名称。

## 数据类型

在 Go 语言中，当我们定义变量或函数时，需要使用数据类型。数据类型的使用有利于 Go 编程。主要有 Go 语言中的四种数据类型，它们在 Go 代码中非常常用。

### 1. 布尔类型

布尔类型由两个定义常量组成：例如：(1) `true` (2) `false`

### 2. 数值类型

数字类型包括整数 `int`、浮点数 `float32`、`float64` 和复数。例如：`100`、`200`、`88`、`168888`、`168`。

### 3. 字符串类型

字符串类型是固定长度字符序列。字符串通过单个字节连接。Go 语言字符串使用 `utf-8` 编码识别 Unicode 文本。例如：`"jQuery in 8 Hours"` 是字符串。

### 4. 衍生类型

衍生类型意味着 (1) 通道类型，(2) Map 类型，(3) 接口类型，(4) 切片类型，(5) 函数类型，(6) 联合类型，(7) 结构体类型，(8) 数组类型，(9) 指针类型。例如：`var arr [10]int` // * arr 是长度为 10 的数组 *

## 变量

Go 语言的变量名由字母、数字和下划线组成，其中第一个字符不能是数字。声明变量有三种方式。

(1) 声明变量的第一种语法是：

```go
var variable_name type variable_name = value
```

例如：`var a int = 100`

(2) 声明变量的第二种语法是：

```go
var variable_name = value
```

例如：`var b = "ruby"`

(3) 声明变量的第三种语法是：

```go
variable_name := value
```

例如：`c := 100`

```go
package main
func main(){
    var a = "C#"
    var b string = "is"
    var c bool = true
    println(a, b, c)
}
```

输出：`C# is true`

## 多变量声明

有三种方式声明多个变量：

(1) `var name1, name2, name3 type value1, value2, value3`

(2) `var name1, name2, name3 = value1, value2, value3`

例如：`var a, b, c int = 100, 200, 300`

(3) `name1, name2, name3 := value1, value2, value3`

`:=` 运算符用于给变量赋值。注意：变量应该预先声明，否则会导致编译错误。

```go
package main
func main(){
    var a, b, c int = 100, 200, 300
    var d, e, f = 400, 500, 600
    println(a, b, c)
    println(d, e, f)
}
```

输出：`100 200 300 400 500 600`

# 总结

在 Go 语言中，每个语句不需要分号来结束。`{` 不能放在单行上，所以以下代码产生错误。关键字不能作为变量、常量和函数的名称。变量名由字母、数字和下划线组成，第一个字符不能是数字。有三种方式声明多个变量：

1. `var name1, name2, name3 type value1, value2, value3`
2. `var name1, name2, name3 = value1, value2, value3`
3. `name1, name2, name3 := value1, value2, value3` `:=` 运算符用于给变量赋值。

# 第 3 小时

## 常量

常量是在程序运行时不会改变的标识符。定义常量的语法是：

`const name [type] = value`

或

`const name = value`

### 3.1

```go
package main
func main() {
    const x, y, z int = 10, 20, 30 // 定义三个常量
    const s = "jQuery in 8 Hours!"
    const b bool = true
    println(x, y, z)
    println(s)
    println(b)
}
```

输出：`10 20 30 jQuery in 8 Hours! true`

解释：`const` 用于定义常量。

### 3.2

```go
package main
// 定义枚举作为常量
func main() {
    const (
        // enumeration
        color1 = "Blue"
        color2 = "Pink"
        color3 = "Gray"
    )
    println(color1, color2, color3)
}
```

输出：`Blue Pink Gray`

解释：常量 `color1`、`color2`、`color3` 在枚举模式下定义。

`iota` 是一个特殊的常量。第一个 `iota` 的值为 0，每当在新行中使用 `iota` 时，它的值会自动加 1。

### 3.3

```go
package main
func main() {
    const (
        x = iota //第一个 iota 值为 0
        y = iota
        z = iota
    )
    println(x)
    println(y)
    println(z)
}
```

输出：`0 1 2`

解释：第一个 `iota` 的值为 0，第二个 `iota` 的值为 1，第三个 `iota` 的值为 2。

## 算术运算符

| 运算符 |
| :--- |
| `+` |
| `-` |
| `*` |
| `/` |
| `%` |
| `++` |
| `--` |

例如：给定 `a = 100`, `b = 2`。

计算：

- `a + b` 返回 `102`
- `a - b` 返回 `98`
- `a * b` 返回 `200`
- `a / b` 返回 `50`
- `a % b` 返回 `0`
- `a ++` 返回 `101`
- `a --` 返回 `99`

## 关系运算符

| 运算符 |
| :--- |
| `>` |
| `<` |
| `>=` |
| `<=` |
| `==` |
| `!=` |

例如：给定 `a = 100`, `b = 2`。

计算：

- `a > b` 返回 `true`
- `b < b` 返回 `false`
- `a >= b` 返回 `true`
- `a <= b` 返回 `false`
- `a == b` 返回 `false`
- `a != b` 返回 `true`

| `true && true; returns true;` | `true && false; returns false;` | `false && false; returns false;` |
| --- | --- | --- |
| `true \|\| true; returns true;` | `true \|\| false; returns true;` | `false \|\| false; return false;` |
| `! false; returns true;` | `! true; returns false;` |   |

## 赋值运算符

| 运算符 | 示例: |
| --- | --- |
| `+=` | `x+=y` |
| `-=` | `x-=y` |
| `*=` | `x*=y` |
| `/=` | `x/=y` |
| `%=` | `x%=y` |

例如：给定：`x=200;` `y=100;` 解释：`x+=y;` // `x=x+y;` 输出 300 `x/=y;` // `x=x / y;` 输出 2 `x-=y;` // `x=x \- y;` 输出 100 `x%=y;` // `x=x%y;` 输出 0

## 运算符优先级

下表列出了运算符的优先级：（从上到下表示优先级从高到低）。

| 优先级 |
| --- |
| 7 |
| 6 |
| 5 |
| 4 |
| 3 |
| 2 |
| 1 |

# 总结

常量是在程序运行期间值不会改变的标识符。定义常量的语法为：`const constant_name [type] = value` 或 `const constant_name = value`。“iota”是一个特殊的常量。第一个 `iota` 的值等于 0，每当在新的行中使用 `iota` 时候，它的值就会自动加 1。后续有以下运算符：算术运算符、关系运算符、逻辑运算符、赋值运算符。

## 第 4 小

### If 语句

| `if test-expression { // 如果为真执行此操作; }` |
| --- |

“if 语句”仅在指定条件为真时执行 `{ … }` 内部的代码；如果条件为假，则不执行 `{…}` 内部的代码。

示例 4.1

```go
package main
import "fmt"
func main() {
    var num int = 100
    if num > 50 {
        fmt.Printf("num is greater than 50")
    }
}
```

输出: num is greater than 50

解释：因为 `num` 的值大于 50，所以执行了 `{ }` 内部的代码。

### if…else 语句

| `if test_expression{ // 如果为真执行此操作 } else { // 如果为假执行此操作 }` |
| --- |

“if... else 语句”在条件为真时运行某些代码，在条件为假时运行另一段代码。

示例 4.2

```go
package main
func main() {
    var num int = 100
    if num > 200 {
        println("num is greater than 200")
    } else {
        println("num is less than 200")
    } 
}
```

输出: num is less than 200

解释：因为 `num` 的值小于 200，所以执行了 `else { }` 代码。

### Switch 语句

| `switch (variable ) { case 1: 如果等于此 case，执行此 case case 2: 如果等于此 case，执行此 case case 3: 如果等于此 case，执行此 case default : 如果等于任何 case，运行 default }` |
| --- |

`variable`（变量）的值将首先与每个 `case` 进行比较，如果等于其中一个 `case` 的值，它将执行该 `case` 代码。

示例 4.3



```go
package main
func main() {
    var number int=20
    switch ( number ) {
        case 10: println ("Running case 10")
        case 20: println ("Running case 20")
        case 30: println ("Running case 30")
        default: println ("Running default")
    }
}
```

输出: Running case 20

解释：`number` 的值为 20；它匹配了 `case 20`。

### Select 语句

Select 语句有点像 Switch 语句。Switch 语句顺序执行 case 代码，Select 语句随机执行 case 代码。

1) `make(chan int, number)`

`make(chan int, number)` 创建一个具有 `number` 个缓冲区的通道。例如：`make(chan int, 10)` 创建具有 10 个缓冲区的通道。

2) `chan <- data`

`chan <- data` 向通道发送数据。`data <- chan` 从通道接收数据。

3) `select { case 接收或发送数据 : 语句; default : 语句 }`

如果多个 case 都可以运行，Select 将随机选择一个执行。如果没有 case 能够运行，Select 将执行 `default` 子句。

示例 4.4

```go
package main
import "fmt"
func main() {
    c1:=make(chan int,24) // 创建通道
    c2:=make(chan int,24)
    c3:=make(chan int,24)
    c1 <- 100 // 向通道发送数据
    c2 <- 200
    c3 <- 300
    select {
        case <-c1: fmt.Println("Receive data from c1")
        case <-c2: fmt.Println("Receive data from c2")
        case <-c3: fmt.Println("Receive data from c3")
        default: fmt.Println("Not receive yet")
    }
}
```

输出: Receive data from c2

解释：select 语句随机执行了一个 case。

### For 循环

For 循环是一种可以执行指定次数循环的控制结构。

1) `for init; condition; in/decrease { }`

`init`：给变量赋初始值。

`condition`：测试表达式。

`in/decrease`：递增或递减。

示例 4.5

```go
package main
func main() {
    for a := 0; a <= 5; a++ {
        print(a)
    }
}
```

输出: 0 1 2 3 4 5

解释：`a :=0` 给 `a` 赋值 0。`a<=5` 是测试表达式。`a++` 是递增。

2) `for test_expression { }`

`test_expression` 检查条件为真为假。

示例 4.6

```go
package main
func main() {
    var a int =0
    var b int = 5
    for a < b {
        a++
        print(a)
    }
}
```

输出: 1 2 3 4 5

解释：`for a < b` 检查 `a` 是否小于 `b`。

# 总结

“if 语句”仅在指定条件为真时执行 `{ … }` 内部的代码；如果条件为假，不执行 `{…}` 内部的任何代码。在“switch 语句”中，变量的值首先与每个 `case` 进行比较，如果等于其中一个 `case` 的值，将执行该 `case` 代码。Select 语句有点像 Switch 语句。Switch 语句顺序执行 case 代码。Select 语句随机执行 case 代码。For 循环是一种可以执行指定次数循环的控制结构。

## 第 5 小

### Break

| `break` |
| --- |

break 语句用于终止循环。break 语句也用于终止 switch 语句中的 case。

示例 5.1

```go
package main
func main() {
    var num int = 20
    for num < 30 {
        print(num," ");
        num++;
        if num > 25 {
            break; // 终止 for 循环
        }
    }
}
```

输出: 20 21 22 23 24 25

解释：如果 `num > 25` 测试表达式为真，`break` 语句将终止循环。

### Continue

| `continue` |
| --- |

continue 语句跳过当前循环执行下一次。

示例 5.2

```go
package main
func main() {
    var num int = 20
    for num < 30 {
        if num == 25 {
            num = num + 1;
            continue; // 跳过当前循环
        }
        print(num, " ")
        num++;
    }
}
```

输出: 20 21 22 23 24 26 27 28 29

解释：如果 `num == 25` 测试表达式为真，`continue` 语句将跳过当前循环并执行下一次。注意：结果中没有 25。

### Goto

| `goto label; ... label: statement;` |
| --- |

goto 语句可以跳转到指定的代码并无条件执行。

示例 5.3

```go
package main
func main() {
    var num int = 10
    if num > 10{ goto code01 }
    if num == 10{ goto code02 }
    code01: print("num > 10")
    code02: print("num == 10")
}
```

输出: num == 10

解释：`goto code01` 意味着执行带有标签 `code01` 的语句。`goto code02` 意味着执行带有标签 `code02` 的语句。

## Example 5.4

```go
package main
func main() {
  var a int = 10
  var b int = 20
  var result int
  result = add(a, b)
  // call the function
  print("The sum is ", result)
}
func add(num1, num2 int) int {
  // define a function
  return num1 + num2
  // pass the result to the caller
}
```

**Output:** The sum is 30

**Explanation:** `add(a, b)` 调用了函数 `add(a, b)`，并将参数 `a` 和 `b` 的值传递给 `num1` 和 `num2`。`func add(num1, num2 int) int` 定义了一个函数 `add(…)`，`num1` 和 `num2` 接收来自 `a` 和 `b` 的值。`return num1 + num2` 将结果值传递给调用者 `add(…)`。

## Example 5.5

```go
package main
import "fmt"
func swap (a, b string) (string, string) {
  // define a function
  return b, a
  // returns two values to the caller
}
func main() {
  x, y := swap("in 8 Hours", "JavaScript")
  //call the function
  fmt.Println(x, y)
}
```

**Output:** JavaScript in 8 Hours

**Explanation:** `func swap(a, b string) (string, string){…}` 定义了一个函数。`swap("in 8 Hours", "JavaScript")` 调用函数 `swap(…)`，并将两个参数传递给函数 `swap(…){…}`。

## Working Scope

任何编码中的工作作用域都是变量可以被访问的范围，在该作用域之外，变量无法被访问。

- 在函数内部定义的变量被称为**局部变量**。

- 在函数外部定义的变量被称为**全局变量**。

## Example 5.6

```go
package main
func main() {
  var a, b, c int
  // defines local variables
  a = 100
  b = 200
  c = a + b
  print(a, b, c)
}
```

**Output:** 100 200 300

**Explanation:** `var a, b, c int` 在函数内部定义了三个局部变量。

## Example 5.7

```go
package main
var v int = 100
// define a global variable
func main(){
  print ("The value of the global variable is ", v)
}
```

**Output:** The value of the global variable is 100.

**Explanation:** `var v int = 100` 定义了一个全局变量。

## Summary

- `break` 语句用于终止循环。`break` 语句也用于终止 `switch` 语句中的 `case`。

- `continue` 语句跳过当前循环并执行下一个循环。

- `goto` 语句可以到指定的代码处并无条件执行。

1. 定义函数的语法如下：`func function_name ( parameter type) type { …… return … }`

2. 调用函数的语法如下：`variable = function_name ( parameter type )`

- 在函数内部定义的变量被称为**局部变量**。在函数外部定义的变量被称为**全局变量**。

## Hour 6

### Array

数组是相同类型和名称的变量的集合。

- **Array element**（数组元素）：数组中的每个变量。

- **Array index**（数组索引）：也称为键，每个元素上的数字。

- **Note**：数组索引或数组键从零开始。

定义数组有几种方法方法：

1. `var array_name[length] type` // 定义数组

2. `array_name[key] = value` // 给元素赋值

#### Example 6.1

```go
package main
func main() {
  var arr [3]int
  // define an array
  arr[0] = 100
  arr[1] = 101
  arr[2] = 102
  print(arr[0], arr[1], arr[2])
}
```

**Output:** 100 101 102

**Explanation:** `var arr [3]int` 定义了一个带有三个元素的数组。`arr` 是数组名，`3` 是长度，类型是 `int`。`arr[0]=100` 给元素赋值，`0` 是索引或键。

#### Example 6.2

```go
package main
func main() {
  var arr [3]int
  // define an array
  arr[0] = 100
  arr[1] = 101
  arr[2] = 102
  print(arr[0], arr[1], arr[2])
}
```

**Output:** 100 101 102

**Explanation:** `var arr [3]int` 定义了一个带有三个元素的数组。

#### Example 6.3

```go
package main
func main() {
  var arr [3]int
  // define an array
  arr[0] = 100
  arr[1] = 101
  arr[2] = 102
  print(arr[0], arr[1], arr[2])
}
```

**Output:** 100 101 102

**Explanation:** `var arr [3]int` 定义了一个带有三个元素的数组。

#### Example 6.4

```go
package main
func main() {
  var arr [3]int
  // define an array
  arr[0] = 100
  arr[1] = 101
  arr[2] = 102
  print(arr[0], arr[1], arr[2])
}
```

**Output:** 100 101 102

**Explanation:** `var arr [3]int` 定义了一个带有三个元素的数组。

### Pointers

指针代表内存地址的值。

1. `&variable` // 获取变量的地址

2. `var variable_name *type` // 声明指针；`*variable_name` 获取地址中的的值

例如：

- `var ipoint *int` // 声明 int 指针

- `var fpoint *float32` // 声明 float32 指针

- `*ipoint` // 获取地址中的 ipoint 值

- `*fpoint` // 获取地址中的 fpoint 值

#### Example 6.6

```go
package main
import "fmt"
func main() {
  var num int = 100
  var pt *int
  // declare a pointer
  pt = &num
  // &num get address and assign to pt
  fmt.Printf("The address of num: %x\n", &num)
  fmt.Printf("The address in pt: %x\n", pt)
  fmt.Printf("The value of the *pt: %d\n", *pt)
}
```

**Output:**

The address of num: C00004058

The address in pt: C00004058

The value of the *pt: 100

**Explanation:** `&num` 从 `num` 获取地址。`pt = &num` 将地址赋值给 `pt`。`*pt` 返回地址中的 `pt` 值。

#### Example 6.7

```go
package main
import "fmt"
func main() {
  var a string = "Hello"
  var b *string
  var c string
  b = &a
  // &a gets the memory address
  c = *b
  // *b gets the value in memory address
  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
}
```

**Output:**

Hello

0xc000381c8

Hello

**Explanation:** `&a` 返回 `a` 的内存地址。`*b` 返回内存地址的值。

### Nil Pointer

当指针被定义且未分配任何变量地址时，它的值为 `nil`。

#### Example 6.8

```go
package main
import "fmt"
func main() {
  var npt *int
  fmt.Printf("The address stored in npt: %x\n", npt)
}
```

**Output:** The address stored in npt: 0

**Explanation:** `npt` 是一个指针，尚未分配任何地址，所以值为 0。

## Hour 7

### Structures

结构体是相同或不同类型数据的集合。

1. **定义结构体类型**：`type structure_name struct { member1 type; member2 type; ... member3 type; }`

2. **访问结构体成员**：`structure_name{member1: value1, member2: value2, … }`

#### Example 7.1



```go
package main
import "fmt"
type Flower struct {
  // define a structure type
  color string
  // structure member
  size string
  number int
}
func main() {
  fmt.Println(Flower{color:"Red", size:"Large", number:10 })
}
```

**输出：** `{Red Large 10}`

**解释：** `type Flower struct` 定义了一个结构体类型。

## 示例 7.2

```go
package main
type Flower struct {
  // 定义一个结构类型
  color string
  // 结构成员
  size string
  number int
}
func main() {
  var Rose Flower   // 声明一个结构变量 Rose
  Rose.color = "Red"    // 给结构成员赋值
  Rose.size = "Large"
  Rose.number = 10
  println("Rose color : ", Rose.color);
  println("Rose size : ", Rose.size);
  println("Rose number : ", Rose.number);
}
```

**输出：**

```
Rose color: Red
Rose size: Large
Rose number: 10
```

**解释：** `var Rose Flower` 声明了一个结构变量 `Rose`。`Rose.color = "Red"` 给结构成员 `Rose.color` 赋值。

## 切片 (Slice)

`Slice` 是一种特殊的数组，但它的长度是可变的。(1) 创建 `Slice` 的种语法如下：

`slice_name := []type{val1, val2, … }`

### 示例 7.3

```go
package main
import "fmt"
func main() {
  s := []int{1,2,3,4,5}    // 创建一个切片
  fmt.Println(s)
}
```

**输出：**

```
1 2 3 4 5
```

**解释：** `s := []int{1,2,3,4,5}` 创建了一个包含五个值的 `Slice`。(2) 创建 `Slice` 的第二种语法如下：

`slice_name := make([]type, len, cap)`

`len` 表示切片的长度。`cap` 表示包含切片元素的容量。

### 示例 7.4

```go
package main
import "fmt"
func main() {
  s := make([]int, 5, 8)
  fmt.Printf("len=%d cap=%d slice=%v\n",len(s),cap(s),s)
}
```

**输出：**

```
len=5   cap=8   slice=[00000]
```

**解释：** `len(s)` 获取切片的长度。`cap(s)` 获取包含所有元素的容量。由于 `Slice` 元素尚未分配任何值，因此这个 `Slice` 的五个值均为零。(3) 从 `Slice` 元素中获取某些值：

`slice_name[key1, key2]`

获取从 `key1` 到 `key2-1` 的值。

### 示例 7.5

```go
package main
import "fmt"
func main() {
  var s = []int{0, 1, 2, 3, 4, 5, 6, 7, 8}
  mySlice:= s[2:6]  // 获取从 s[2] 到 s[5] 的值
  fmt.Println(mySlice)
}
```

**输出：**

```
2 3 4 5
```

**解释：** `s[2: 6]` 获取从 `s[2]` 到 `s[5]` 的值。(4) 给 `Slice` 元素赋值。

`slice_name[key] = value`

### 示例 7.6

```go
package main
import "fmt"
func main() {
  var s = []int{0, 1, 2, 3, 4, 5, 6, 7, 8}
  s[3] = 10      // 给 s[3] 赋新值
  s[6] = 100     // 给 s[6] 赋新值
  fmt.Println(s)
}
```

**输出：**

```
[0 1 2 10 4 5 100 7 8]
```

**解释：** `s[3] = 10` // 给 `s[3]` 赋新值；`s[6] = 100` // 给 `s[6]` 赋新值。

## append() & copy()

`append(slice_name, values)` // 向 `Slice` 中追加值

`copy(new_slice, old_slice)` // 将旧 `Slice` 拷贝到新的 `Slice`

### 示例 7.7

```go
package main
import "fmt"
func main() {
  mySlice := make([]int, 0, 0)
  showSlice(mySlice)
  mySlice = append(mySlice, 10,20,30)  // 追加
  newSlice := make([]int, len(mySlice), cap(mySlice)*2)
  copy(newSlice,mySlice)  // 拷贝
  showSlice(newSlice)
}
func showSlice(x []int){
  fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
}
```

**输出：**

```
len=0 cap=0 slice=[]
len=3 cap=4 slice=[10 20 30]
```

**解释：** `append(mySlice, 10,20,30)` 为 `mySlice` 添加了三个值。`newSlice := make([]int, len(mySlice), cap(mySlice)*2)` 创建了一个新切片，容量是原来的倍。`copy(newSlice,mySlice)` 执行了拷贝。

# 总结

`Slice` 是一个特殊的数组，但它的长度是可变的。

(1) 定义结构体类型：

```go
type structure_name struct {
  member1 type
  member2 type
  member3 type
}
```

(2) 访问结构体成员：`structure_name.member1`

(3) 声明结构体变量：`var structure_name`

(4) 给结构体成员赋值：`member = value`

# 第 8 章 GORoutine

`goroutine` 用于运行多个任务，意味着通过 `go` 关键字同时执行多个线程。以下示例是定义 `goroutine` 函数并运行它：

```go
go func(arguments) { // 定义 goroutine
}(arguments) // 运行 goroutine
```

### 示例 8.1

```go
package main
import "fmt"
func fn(s string) {
  for i := 0; i < 5; i++ {
    fmt.Println(s)
  }
}
func main() {
  fn("Thread A")
  go func() { // 定义 goroutine
    fmt.Println("Thread B")
  }() // 运行 goroutine
  fmt.Scan() // 从键盘输入
  fmt.Println("Complete!")
}
```

**输出：**

```
Thread A
Thread B
Complete!
```

**解释：** `go func(string) { ... }` 定义了 `goroutine` 函数。`("Thread B")` 运行了该 `goroutine`。

## Range

`Range` 是 Go 语言的内置函数，用于遍历数组、切片和映射。

* 遍历数组、切片返回索引和值。

* 遍历映射返回键和值。

* 遍历通道返回值。

(1) 遍历数组/切片

```go
for index, value := range array/slice {}
```

### 示例 8.2

```go
package main
import "fmt"
func main() {
  for key, value := range []int{10,11,12,13} {
    fmt.Printf("key:%d value:%d\n", key, value)
  }
}
```

**输出：**

```
key:0 value:10
key:1 value:11
key:2 value:12
key:3 value:13
```

**解释：** `range []int{10,11,12,13}` 遍历了切片并返回索引和值。

(2) 遍历字符串

```go
for key, value := range str {}
```

### 示例 8.3

```go
package main
import "fmt"
func main() {
  var str = "hello"
  for key, value := range str {
    fmt.Printf("key:%d value:%0x\n", key, value)
  }
}
```

**输出：**

```
key:0 value:0x68
key:1 value:0x65
key:2 value:0x6c
key:3 value:0x6c
key:4 value:0x6f
```

**解释：** `range str` 遍历字符串，返回其键（索引）和值（字符）。

(3) 遍历通道

```go
for value := range channel {}
```

### 示例 8.4

```go
package main
import "fmt"
func main() {
  c := make(chan int)
  go func() { // 定义 goroutine
    c <- 1 // 向通道发送数据
    c <- 2
    c <- 3
    close(c) // 关闭通道
  }() // 调用 goroutine 函数
  for v := range c { // 遍历通道
    fmt.Println("Send data to channel: ",v)
  }
}
```

**输出：**

```
Send data to channel: 1
Send data to channel: 2
Send data to channel: 3
```

**解释：** `range c` 遍历通道。`go func(){}` 定义了 `goroutine` 函数。`()` 调用了函数。

## Map

`Map` 是键值对的无序集合。`Map` 用于通过键快速检索数据，类似于索引并指向数据的值。定义 `map` 的两种语法如下：

(1) `m1 := map[key_type]value_type{}`

`m1` 是一个 map 变量。

(2) `m2 := make(map[key_type] value_type)`

`m2` 是一个 map 变量。

### 示例 8.5

```go
package main
import "fmt"
func main() {
  m1 := map[int]int{}
  m2 := make(map[int]int)
  m1[1] = 10
  m2[2] = 20
  for key, value := range m1 {
    fmt.Println("Key: ", key, "Value: ", value)
  }
  for key, value := range m2 {
    fmt.Println("Key: ", key, "Value: ", value)
  }
}
```

**输出：**

```
Key: 1 Value: 10
Key: 2 Value: 20
```

**解释：** `m1 := map[int]int{}` 定义了 map `m1`。`m2 := make(map[int]int)` 定义了 map `m2`。

## 类型转换

类型转换意味着变量的一种数据类型转换为另一种数据类型。

`data_type (variables)`

### 示例 8.6

```go
package main
import "fmt"
func main() {
  var num1 int = 100
  var num2 int = 3
  var result float32
  result = float32(num1)/float32(num2) // 转换
  fmt.Printf("The result is %f\n", result)
}
```

**输出：**

```
The result is 33.333332
```

**解释：** `float32(num1)/float32(num2)` 将数据类型从 `int` 转换为 `float32`。

# 递归

递归意味着函数调用自己。

```go
func recursion() { 
    recursion() // 调用自己 
} 
func main() { 
    recursion() 
}
```

### 示例 8.7

```go
package main
import "fmt"
func myRecur(n int) int { 
    if n == 0 { return 1 }
    return n * myRecur(n-1) // 调用自己 
}
func main() { 
    fmt.Print("Factorial of 10 is ") 
    fmt.Print(myRecur(10)) 
}
```

**输出：** `Factorial of 10 is 3628800`

**解释：** `myRecur(n-1)` 调用了自身。递归会一直进行，直到出现 `myRecur(0)`。

# 总结

- `goroutine` 用于同时运行多个任务，这意味着 `goroutine` 函数可以通过使用 `go` 关键字同时执行多个线程。

- `Range` 是 Go 语言的内置函数，用于遍历数组、`slices`、`strings` 和 `maps`。

- `Map` 是键值对的无序集合。`Map` 用于通过键快速检索数据，类似于索引并指向数据的值。

- 类型转换意味着将变量的一种数据类型转换为另一种数据类型。

- `data_type`（变量）

- 递归意味着函数调用自己。

```go
func recursion() { 
    recursion() // 调用自己 
} 
func main() { 
    recursion() 
}
```

# 附录 1

## 并发

Go 语言支持并发，我们可以使用 `go` 关键字来调用函数，启动一个新的运行时线程 `goroutine`。使用 `go` 关键字调用函数的语法如下：

`go function_name (arguments)`

### 示例：

```go
package main
import (
    "fmt"
    "time"
)
func fn(s string) { 
    // 定义一个函数 fn
    for i := 0; i < 5; i++ { 
        time.Sleep(200 * time.Millisecond) // 延迟运行
        fmt.Println(s) 
    } 
}
func main() { 
    go fn("Thread A") // 调用函数 fn 
    fn("Thread B") // 调用函数 fn 
    go func(msg string) { 
        // 定义一个 goroutine 函数
        fmt.Println(msg) 
    }("Press Enter to Stop!") // 运行 goroutine 函数
    fmt.Scanln() // 从键盘接受用户输入 
    fmt.Println("Complete! ") 
}
```

**输出：** `Thread B Thread A Thread B Thread A Thread B Thread A Thread B Thread A Press Enter to Stop! Thread A Complete!`

**解释：** `go fn("Thread A")` 使用 `go` 关键字调用函数 `fn`，启动了一个新线程 `goroutine`。

# 附录 2

## 测试

请选择正确答案。

**(01)**

```go
package main 
import "fill in" // 导入内置函数 
func main() { 
    fmt.Println("Hello, World! ") 
}
```

A. `iostream` | B. `math` | C. `i/o` | D. `fmt`

**(02)**

```go
fill in a int // 声明变量 
a = 100
```

A. `variable` | B. `variab` | C. `var` | D. `va`

**(03)**



```go
package main 
func main() { 
    const ( 
        x = fill in // 特殊常量 
        y = fill in
        z = fill in 
    ) 
    print(x, y, z) 
}
```

**输出:** `0 1 2`

A. `const` | B. `iota` | C. `constant` | D. `iote`

**(04)**

```go
package main 
func main() { 
    var number int=20 
    fill in ( number ) { // 让 number 比较每个 case 
    case 10 : println ("Running case 10") 
    case 20 : println ("Running case 20") 
    case 30 : println ("Running case 30") 
    default : println ("Running default code") 
    } 
}
```

A. `If` | B. `While` | C. `Do` | D. `Switch`

**(05)**

```go
package main 
func main() { 
    var num int = 10 
    if num > 10{ fill in code01 // 接下来运行指定的代码 
    } 
    if num == 10{ fill in code02 // 接下来运行指定的代码 
} 
code01: print("num > 10") 
code02: print("num == 10")
}
```

A. `goto` | B. `go` | C. `to` | D. `return`

**(06)**

```go
package main 
func main(){ 
    var arr []int = fill in ([]int, 3) // 定义数组 
    arr[0]=100 // 给数组赋值 
    arr[1]=101 
    arr[2]=102 
    print(arr[0], arr[1], arr[2]) 
}
```

A. `array` | B. `define` | C. `make`

**(07)**

```go
package main 
import "fmt" 
type fill in { // 定义结构体 
    color string // 成员 
    size string 
    number int 
} 
func main() { 
    fmt.Println(Flower{color:"Red", size:"Large", number:10}) 
}
```

A. `structure` | B. `struct` | C. `string`

**(08)**

```go
package main 
import "fmt" 
func fn(s string) { // 定义函数 
    for i := 0; i < 5; i++ { 
        fmt.Println(s) 
    } 
} 
func main() { 
    fn("Thread B") // 调用函数 
    fill in func(msg string) { // 定义 goroutine 函数
        fmt.Println(msg)
    }("Press Enter to Stop!") // 运行 goroutine 函数
    fmt.Scanln() // 从键盘接受用户输入 
    fmt.Println("Complete! ") 
}
```

A. `goto` | B. `go` | C. `to` | D. `goroutine`

**(09)**

```go
package main 
func main(){
    var a = "C# in 8 Hours"
    var b string = "is"
    c ="a book! " // 给 c 赋值 
    var e = true
    println(a, b, c, e)
}
```

A. `string` | B. `boolean` | C. `bool` | D. `char`

**(10)**

**给定：** `a = 100`, `b = 2`

**计算：** `a + b` 返回 `102`

`a - b` 返回 `98`

`a * b` 返回 `200`

`a / b` 返回 `50`

`a % b` 返回 fill in

A. `0` | B. `1` | C. `2` | D. `3`

**(11)**

```go
package main 
import "fmt" 
func main() { 
    c1:=make(chan int,10) // 创建 channel 
    c2:=make(chan int,10)
    c3:=make(chan int,10)
    c1<-100 // 向 channel 发送数据 
    c2<-200
    c3<-300 
    fill in { // 随机执行一个 case
    case c1: fmt.Println("Receive data from c1")
    case c2: fmt.Println("Receive data from c2")
    case c3: fmt.Println("Receive data from c3")
    default: fmt.Println("Not receive data yet") 
    }
}
```

A. `switch` | B. `select` | C. `while` | D. `if`

**(12)**

```go
package main 
import "fmt" 
fill in (a, b string) (string, string) { // 定义函数
    return b, a // 返回两个值给调用者 . 
} 
func main() { 
    x, y := swap("in 8 Hours", "JavaScript") // 调用函数
    fmt.Println(x, y) 
}
```

A. `function` | B. `def` | C. `void` | D. `func`

**(13)**

```go
package main 
import "fmt" 
func main() { 
    var num int=100 
    var pt *int // 声明指针
    pt = fill in // 获取地址并赋值给 pt
    fmt.Printf("The address of num: %x\n", &num) 
    fmt.Printf("The address in pt: %x\n", pt) 
    fmt.Printf("The value of pt: %d\n", *pt) 
}
```

A. `*num` | B. `$num` | C. `&num` | D. `#num`

**(14)**

```go
package main 
import "fmt" 
func main(){ 
    s := fill in int{1,2,3,4,5} // 创建 slice 
    fmt.Println(s) 
}
```

A. `[]` | B. `[0]` | C. `[1]`

**(15)**

```go
package main 
import "fmt" 
func main(){ 
    c := make(chan int)
    go func() { // 定义 goroutine 函数
        c<-1 // 向 channels 发送数据
        c<-2 
        c<-3 
        close(c) // 关闭 channels
    }() 
    for v := in c { // 遍历 channels
        fmt.Println("Send to channel: ",v) 
    } 
}
```

A. `iterate` | B. `chan` | C. `in` | D. `range`

**(16)**

```go
package main 
func main(){ 
    var a = "C# in 8 Hours" 
    var b string = "is"
    c ="a book! " // 给 c 赋值 
    var e fill in = true
    println(a, b, c, e) 
}
```

A. `<` | B. `=`

**(17)**

| `true && true` 返回 `true` | `true && false` 返回 `false` | `false && false` 返回 `false` |
| --- | --- | --- |
| `true || true` 返回 `true` | `true || false` 返回 fill in | `false || false` 返回 fill in |

A. `true` | B. `false` | C. `true` | D. `false`

**(18)**

```go
package main 
func main() { 
    var a int =0 
    var b int = 5 
    fill in a < b { // 语句 
    a++ 
    print(a) 
}
```

**输出:** `1 2 3 4 5`

A. `while` | B. `if` | C. `do` | D. `for`

**(19)**

```go
package main 
import "fmt" 
func swap (a, b string) (string, string) { // 定义函数
    fill in b, a // 将两个值传递给调用者 . 
} 
func main() { 
    x, y := swap("in 8 Hours", "JavaScript") // 调用函数
    fmt.Println(x, y) 
}
```

A. `pass` | B. `return` | C. `send` | D. `goto`

**(20)**

```go
package main 
import "fmt" 
func main() { 
    var n *int 
    fmt.Printf( n) 
} // 输出是什么？
```

A. `0` | B. `1` | C. `2` | D. `3` (21)

### 22

```go
package main
import "fmt"
func main() {
    var s = [9]int{0, 1, 2, 3, 4, 5, 6, 7, 8}
    mySlice := s[fill in]   // 获取四个值
    fmt.Println(mySlice)
}
```

输出: `2 3 4 5`

A. `2:6`

B. `1:5`

C. `3:7`

D. `3:6`

### 23

```go
package main
import "fmt"
func main() {
    m1 := fill in [int]int{}      // 定义一个 map
    m1 m2 := fill in (map[int]int) // 定义一个 map
    m1[1] = 10
    m2[2] = 20
    for key, value := range m1 {
        fmt.Println("Key: ", key, "Value: ", value)
    }
    for key, value := range m2 {
        fmt.Println("Key: ", key, "Value: ", value)
    }
}
```

A. `make`

B. `make map`

C. `map make`

D. `map map`

### 24

```go
package main
import "fmt"
func myRecur(n int) int {
    if n == 0 {
        return 1
    }
    return n * fill in      // 递归
}
func main() {
    fmt.Print("Factorial of 10 is ")
    fmt.Print(myRecur(10))
}
```

A. `myRecur(0)`

B. `myRecur(n-1)`

C. `recursion(0)`

D. `recursion(n-1)`

### 25

```go
package main
import (
    "fmt"
    "time"
)
func fn(s string) {
    // 定义一个函数 fn
    for i := 0; i < 5; i++ {
        time.Sleep(200 * time.Millisecond) // 延迟运行
        fmt.Println(s)
    }
}
func main() {
    fill in fn("Thread A")      // 调用函数 fn
    fn("Thread B")             // 调用函数 fn
}
```

A. `goroutine`

B. `goto`

C. `to`

D. `go`

#### 答案

| 题目 | 答案 |
| --- | --- |
| 01. | D |
| 02. | C |
| 03. | B |
| 04. | D |
| 05. | A |
| 06. | C |
| 07. | B |
| 08. | B |
| 09. | C |
| 10. | A |
| 11. | B |
| 12. | D |

注：本书仅供初学者，不适合有经验的程序员。

源码下载链接：[`forms.aweber.com/form/34/1805492434.htm`](https://forms.aweber.com/form/34/1805492434.htm)

#### 源码

Ray Yao 在亚马逊上的电子书与书籍

- Ray Yao 著《Advanced C++ Programming》
- Ray Yao 著《Advanced Java Programming》
- Ray Yao 著《AngularJs Programming》
- Ray Yao 著《C# Programming》
- 《C# 面试与认证》
- Ray Yao 著《C++ Programming》
- 《C++ 面试与认证》
- Ray Yao 著《Django Programming》
- Ray Yao 著《Go Programming》
- Ray Yao 著《Html Css Programming》
- 《Html Css 面试与认证》
- Ray Yao 著《Java Programming》
- 《Java 面试与认证》
- Ray Yao 著《JavaScript Programming》
- 《JavaScript 50 Useful Programs JavaScript 面试与认证》
- Ray Yao 著《JQuery Programming》
- 《JQuery 面试与认证》
- Ray Yao 著《Kotlin Programming》
- 《Linux Command Line Linux 面试与认证》
- Ray Yao 著《MySql Programming》
- Ray Yao 著《Node.Js Programming》
- 《Php 面试与认证》
- Ray Yao 著《Php MySql Programming》
- Ray Yao 著《PowerShell Programming》
- Ray Yao 著《Python Programming》
- 《Python 面试与认证》
- Ray Yao 著《R Programming》
- Ray Yao 著《Ruby Programming》
- Ray Yao 著《Rust Programming》
- Ray Yao 著《Scala Programming》
- Ray Yao 著《Shell Scripting Programming》
- Ray Yao 著《Visual Basic Programming》
- 《Visual Basic 面试与认证》
- Ray Yao 著《Xml Json Programming》
