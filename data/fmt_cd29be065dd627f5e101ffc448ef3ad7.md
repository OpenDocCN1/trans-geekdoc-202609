
```go
// Go program to explain parameters and returns

package main

import "fmt"

func main() {
/* declare local variables*/
var x int = 50
var y int = 40
var sum_value int

/* calling a function to get sum of values */
sum_value = sum(x, y)

fmt.Printf("Sum value is: %d\n", sum_value)
}

/* function returns the sum of two numbers */
func sum(num1, num2 int) int {
/* declare local variables */
var result int
result = num1 + num2
return result
}
```

上述程序的输出如下：

**和值为：90**

在创建 Go 函数时，你定义函数将执行的任务。要使用函数，你必须调用该函数来执行预定义的任务。

当程序调用函数时，程序控制权转移到被调用函数。被调用函数执行定义好的任务，并在执行其 `return` 语句或到达其函数结束的闭合大括号时，将程序控制权返回给主程序。

要调用函数，你只需将所需参数与其函数名一起传递。如果函数返回值，则可以存储返回值。

### 2.3 多返回值和命名返回值

Golang 允许在函数定义中为函数的返回或结果参数命名。此外，Go 内置支持多返回值。此功能用于从函数返回结果和错误值。

#### 2.3.1 多返回值

在 Go 中，函数可以使用 `return` 语句返回多个值。返回值的类型取决于参数列表中定义的参数类型，如下所示：

#### 程序 2.2

```go
// Go program to explain multiple returns

package main

import "fmt"

// testfunc return 2 values of int type
func testfunc(x, y int) (int, int) {
return x + y, x - y
}

func main() {
// Return values are assigned into different variables
var testvar1, testvar2 = testfunc(10, 20)

fmt.Printf("addition result: %d", testvar1)
fmt.Printf("\nsubtraction result: %d", testvar2)
}
```

上述程序的输出如下：

**加法结果：30**

**减法结果：-10**

#### 2.3.2 命名返回值

Golang 允许在函数定义中为函数的返回参数命名，即在函数定义中显式命名返回变量。它消除了在 `return` 语句中提及变量名的需要。

这个概念通常用于函数需要返回多个值时。Golang 提供此功能以方便用户并增强代码可读性。

命名返回的语法：

```go
func func_name(Par-list)(result_par1 data_type, result_par2
data_type, ...){
// function body

return
}
```

让我们看一个例子：

#### 程序 2.3

```go
// Golang program to show the use of named return arguments

package main

import "fmt"

// Main Method
func main() {

// calling the function which returns one values
x := sum(10, 20)

fmt.Println("10 + 20 =", x)
}

// function with named arguments
func sum(a, b int) (add int) {
add = a + b

// return keyword without any resultant parameters

return
}
```

上述程序的输出如下：

10 + 20 = 30

### 2.4 按值调用

Golang 支持按值调用来向函数传递参数。Go 没有按引用调用，因为它没有引用变量。然而，我们可以按值传递变量的地址。Golang 默认使用按值方式向函数传递参数。

```go
// call by value
replace(x)
fmt.Printf("\nvalue of x after function call = %d", x)
}
```

上述程序的输出如下：

```text
value of x before function call = 10
value of x after function call = 10
```

如前所述，Go 没有按引用调用，因为它没有引用变量。然而，我们可以按值传递变量的地址。在这里，我们将使用指针和解引用运算符的概念。地址运算符 `&` 用于获取任何数据类型的变量的地址，而解引用运算符 `*` 用于访问地址处的值。

由于实际参数和形式参数引用相同的位置，因此在函数内部所做的任何更改都会反映在调用者的实际参数中。这如下所示：

#### 程序 2.5

```go
// Go program to explain call by passing the address of the variable

package main
```

```
import "fmt"

// function to change the value of given variable
func replace(x *int) {
*x = 20
}

// main function
func main() {

var x int = 10
fmt.Printf("value of x before function call = %d", x)

// call by reference
replace(&x)
fmt.Printf("\nvalue of x after function call = %d", x)
}
```

以下是上述程序的输出：

**函数调用前 x 的值 = 10**

**函数调用后 x 的值 = 20**

### 2.5 可变参数函数

通常情况下，函数只接受固定数量的参数，但可变参数函数可以接受可变数量的参数。

只有函数的最后一个参数可以是可变参数。如果函数定义的最后一个参数前面加上省略号，则该函数可以为该参数接受任意数量的参数。示例如下：

```
func variadic_function(a int, b ...int) {
// Body of variadic function
}
```

在上面的函数中，参数 `b` 是可变参数，因为它前面加上了省略号，并且可以接受任意数量的参数。

让我们使 `variadic_function` 的第一个参数变为可变参数。语法如下所示：

```
func variadic_function(a ...int, b int) {
// Body of variadic function
}
```

上述 `variadic_function` 将无法编译，并出现语法错误：

**不能对非最后一个参数 a 使用 ...**

在上面的函数中，不可能向参数 `b` 传递参数，因为我们传递的任何参数都会被分配给第一个参数 `a`，因为它是可变参数。因此，可变参数只能出现在函数定义的最后。可变参数函数的工作方式是将可变数量的参数转换为可变参数类型的一个切片。你将在 *第 5 章：切片* 中详细学习切片的概念：

#### 程序 2.6

// 用于解释可变参数函数的 Go 程序

```
package main

import (
"fmt"
"strings"
)

// Variadic function to join strings
func join(element ...string) string {
return strings.Join(element, "_")
}
```

```
func main() {

// multiple arguments
fmt.Println(join("GO", "language", "book"))
}
```

以下是上述程序的输出：

```
GO_language_book
```

可变参数函数提高了程序的可读性。它可以在参数数量未知等场景中使用。

让我们看下面的程序：

#### 程序 2.7

```
// Go program to explain the variadic function

package main

import (
"fmt"
"strings"
)

// Variadic function to join strings

func join(element ...string) string {
```

```
return strings.Join(element, "_")
}

func main() {

// pass a slice in variadic function
element := []string{"GO", "language", "book"}
fmt.Println(join(element...))
}
```

以下是上述程序的输出：

```
GO_language_book
```

让我们再看另一个程序：

#### 程序 2.8

```
//Select single argument from all arguments of variadic function

package main

import "fmt"

func main() {
variadicExample("IT", "Finance", "HR", "Recruitment", "Payroll")
}

func variadicExample(x ...string) {
fmt.Println(x[1])
```

```
fmt.Println(x[4])
}
```

以下是上述程序的输出：

**Finance**

**Payroll**

### 2.6 Defer

Go 有控制流机制：等，但其中一些使用较少的是 `defer`、`panic` 和 `recover`。

#### 2.6.1 Defer

`defer` 语句会推迟函数的执行，并将函数调用推入一个列表，直到包含的函数返回，无论是正常返回还是通过 `panic`。`defer` 通常用于简化执行各种清理操作的函数，如下所示：

#### 程序 2.9

```
//Program to explain defer

package main

import "fmt"

func main() {
defer fmt.Println("GO")
fmt.Println("Book")
}
```

以下是上述程序的输出：

Book

GO

### 结论

函数声明由关键字、函数名、参数列表（`main` 为空）、结果列表以及函数体——定义其行为的语句——用大括号括起来组成。

当函数被调用时，你会向参数传递一个值。这个值被称为实际参数或参数。参数列表指的是函数的参数的类型、顺序和数量。

当程序调用函数时，程序控制权转移到被调用的函数。被调用的函数执行定义的任务，并在其 `return` 语句执行或其函数结束的闭合大括号到达时，将程序控制权返回给主程序。

在 Go 中，函数可以使用 `return` 语句返回多个值。返回值的类型取决于参数列表中定义的参数类型。

Golang 允许在函数定义中为函数的返回参数命名，即在函数定义中显式命名返回变量。它消除了在 `return` 语句中提及变量名的需要。

Go 没有按引用调用，因为它没有引用变量。然而，我们可以按值传递变量的地址。这里，我们将使用指针和解引用运算符的概念。地址运算符 `&` 用于获取任何数据类型变量的地址，而解引用运算符 `*` 用于访问地址处的值。

通常情况下，函数只接受固定数量的参数，但可变参数函数可以接受可变数量的参数。只有一个函数的最后一个参数可以是可变参数。如果函数定义的最后一个参数前面加上省略号，则该函数可以为该参数接受任意数量的参数。

可变参数函数提高了程序的可读性。它可以在参数数量未知的情况下使用。

`defer` 语句会推迟函数的执行，并将函数调用推入一个列表，直到包含的函数返回，无论是正常返回还是通过 `panic`。`defer` 通常用于简化执行各种清理操作的函数。

### 问题

编写 Golang 中创建函数的语法。

多返回值和命名返回值之间有什么区别？请用 Go 程序解释。

编写一个 Go 程序来解释 Golang 中的按值调用。

什么是可变参数函数？解释其可使用的场景。

Golang 中的 `defer` 语句是什么？

## 控制流

在 Go 中，控制流语句用于中断执行流程并使程序能够基于某些条件执行代码。本章将介绍 Go 中的控制流概念。它将介绍使用 `if...else` `switch...case` 和 `fallthrough` 语句在 Golang 中的决策制定。它还将介绍循环的概念 - `for` 循环、嵌套 `for` 循环、循环控制语句 – 等。

## 结构

决策（`if`, `if...else`, `if...else if...else`, `switch...case`）

循环（`for` 循环、嵌套 `for` 循环、循环控制语句-`break`、`goto`、`continue`、无限循环）和 `fallthrough`

编程示例

## 目标

本章的目的是向读者介绍控制流和循环的概念，并介绍如何在 Go 编程语言中使用它们。

### 3.1 决策

Golang 使用控制语句根据某些条件控制程序的执行流程。它们用于根据程序状态的变化确保程序执行期间的逻辑流程。

#### 3.1.1 If 语句

如果一个条件被发现为真，则语句会执行一段代码。如果该语句看起来像 C 或 Java 中的那样，只有一个区别，那就是我们需要使用 `{}` 而不是 `()`。语句声明的变量仅在 `if` 结束之前处于作用域内。

**语法：**

```
if condition {
// piece of code to be executed when the condition is true
}
```

例如，下面的程序将在变量 `a` 为 true 时打印。

#### 程序 3.1

```
// Go program to explain if statement

package main

import (
"fmt"
)
```

```go
func main() {
    var x = "Cricket"
    a := true
    if a {
        fmt.Println(x)
    }
}
```

上述程序的输出如下：

**Cricket**

#### 3.1.2 if...else 语句

`if` 语句在条件为真时执行一段语句块，如果条件为假，则会跳转到 `else` 块并执行它。

**语法：**

```go
if condition {
    // piece of code to be executed if condition is true
} else {
    // piece of code to be executed if condition is false
}
```

以下示例将在 `x` 为 New Delhi 时显示输出 Capital of India。

**程序 3.2**

```go
// Go program to explain if ...else statement

package main

import (
    "fmt"
)

func main() {
    x := "New Delhi"

    if x == "New Delhi" {
        fmt.Println("Capital of India")
    } else {
        fmt.Println("City is not the capital of India")
    }
}
```

上述程序的输出如下：

**Capital of India**

#### 3.1.3 if...else if...else 语句

`if...else if...else` 语句允许组合多个 `if...else` 语句。

**语法：**

```go
if condition-1 {
    // piece of code to be executed if condition-1 is true
} else if condition-2 {
    // piece of code to be executed if condition-2 is true
} else {
    // piece of code to be executed if both condition1 and condition2 are false
}
```

下面的示例将显示以下输出：

"**Capital of Maharashtra**" if `x` is "Mumbai"

"**City of Maharashtra**" if `x` is "Pune" and

"**Neither Pune nor Mumbai**" if `x` is other than "Pune" or "Mumbai"

让我们看下面的示例：

**程序 3.3**

## 具结书

日期：2023年05月22日

申请编号：20230522-001

具结人：张三

申请塘主：李四

| 鱼塘名称 | 塘口面积（亩） | 养殖品种 | 预计产量（斤） |
| --- | --- | --- | --- |
| 东塘 | 25 | 草鱼 | 5000 |
| 西塘 | 30 | 鲢鱼 | 6000 |
| 南塘 | 20 | 鲤鱼 | 4000 |

- 一、具结人承诺已仔细阅读并充分理解《养殖水域滩涂规划》和《水域滩涂养殖证管理办法》等法律法规，保证所提交的申请材料真实、合法、有效。
