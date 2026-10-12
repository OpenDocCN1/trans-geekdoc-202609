

# 11. 控制结构

控制结构是用于让程序员更好地控制程序执行流程的编程构造。当程序被编译时，会构建一个可执行的二进制文件。该文件包含特定平台原生的机器级指令。每一行有意义的代码都会产生一条或多条机器级指令。例如，`var name string` 将产生一类机器级指令，而 `a = b + c` 将产生另一类指令。这是由编译器完成的，我们无需担心。在此章节中提及这一点的目的是为了解释执行流程。回到主题——每一行代码对应一条或多条可执行指令。多行代码将产生多条机器级指令。可执行二进制文件一旦运行，将从第一条指令开始执行，直到最后一条。从概念上讲，我们可以认为程序从第一行代码开始执行，直到最后一行（尽管实际上执行的是可执行二进制文件，而不是程序文件本身）。这是一种非常线性的执行流程。我们可以使用控制结构来改变这种执行流程。Go 语言提供了决策构造和循环作为控制结构。

## 11.1 决策制定

决策构造为程序的执行引入了条件性。例如，你可以根据某个条件是否满足来执行一块代码。Go 语言以 `if-else`、`switch` 以及一些高级构造的形式提供了决策构造。我们将重点介绍 `if-else` 和 `switch`。

### 11.1.1 If-Else 构造

If-Else 构造用于在给定条件为 `true` 时执行一块代码，并可选择在给定条件为 `false` 时执行另一块不同的代码。让我们从一个简单的 `if` 块开始。

**通用语法：**

```
if (<condition>) {
    /* 如果 <condition> 为 true 则执行的语句 */
}
```

**示例：**

```
if (num == 0) {
    fmt.Println("num is 0")
}
```

`if` 语句应提供一个用于求值的条件，在上述代码片段中标记为 `<condition>`。该条件通常是一个布尔表达式，其求值结果为 `true` 或 `false`。如果求值为 `true`，则执行 `if` 块内的语句（即 `if` 语句后花括号内的代码块）。如果求值为 `false`，则跳过 `if` 块，程序将从 `if` 块之后恢复执行。

> **注意：** 条件可以是简单的布尔表达式，如 `(a == 0)`，也可以是使用逻辑运算符组合的多个布尔表达式，如 `(a != 0) && (b > 1)`。

让我们编写一个简单的程序来演示 `if` 语句的用法：

```go
/* If Demo */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    var a int = 20

    fmt.Printf("\nProgram execution begins. This statement is before the if block.\n")

    /* 检查 a 是否大于 10 */
    if (a > 10) {
        fmt.Printf("\nInside if block.\n%d is greater than 10.\n", a)
    }

    fmt.Printf("\nOutside if block. Program coming to an end.\n")
}
```

**输出：**
![](Image00041.jpg)

在本例中，我们设置了一个求值为 `true` 的条件，因此 `if` 块得以执行。让我们修改代码，将 `if (a > 10)` 改为 `if (a < 10)` 并观察结果：

**输出：**
![](Image00042.jpg)

可以看到，当给定条件求值为 `false` 时，`if` 块内的语句不会被执行。可以使用 `else` 块在条件求值为 `false` 时执行另一块不同的代码。`else` 块必须紧跟在 `if` 块之后。

**通用语法：**

```
if (<condition>) {
    /* 如果 <condition> 为 true 则执行的语句 */
} else {
    /* 如果 <condition> 为 false 则执行的语句 */
}
```

**示例：**

```
if (num == 0) {
    fmt.Println("num is 0")
} else {
    fmt.Println("num is NOT 0")
}
```

`if-else` 构造的工作原理很简单——如果条件求值为 `true`，则执行 `if` 块并跳过 `else` 块；如果求值为 `false`，则跳过 `if` 块并执行 `else` 块。

让我们编写一个使用 `if` 和 `else` 块的程序，看看当 `if` 块的给定条件求值为 `false` 时会发生什么。

```go
/* If Else Demo */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    var a int = 5

    fmt.Printf("\nProgram execution begins. This statement is before the if block.\n")

    /* 检查 a 是否大于 10 */
    if (a > 10) {
        fmt.Printf("\nInside if block.\n%d is greater than 10.\n", a)
    } else {
        fmt.Printf("\nInside else block.\n%d is NOT greater than 10.\n", a)
    }

    fmt.Printf("\nOutside if/else blocks. Program coming to an end.\n")
}
```

**输出：**
![](Image00043.jpg)

可以看到，条件 `(a > 10)` 求值为 `false`，因为 `a` 为 `5`。因此，`if` 被跳过，`else` 块得以执行。

一个 `if-else` 块组合只会检查一个条件的有效性。根据给定条件的求值结果，将执行 `if` 或 `else` 块。如果你想检查多个条件，可以在 `if-else` 块内嵌套 `if-else` 块，如下所示：

```
if (<condition 1>) {
    /* 如果 <condition 1> 为 true 则执行的语句 */
    if (<condition 2>) {
        /* 如果 <condition 1> 和 <condition 2> 都为 true 则执行的语句 */
    } else {
        /* 如果 <condition 1> 为 true 且 <condition 2> 为 false 则执行的语句 */
    }
} else {
    /* 如果 <condition 1> 为 false 则执行的语句 */
    if (<condition 3>) {
        /* 如果 <condition 1> 为 false 且 <condition 3> 为 true 则执行的语句 */
    } else {
        /* 如果 <condition 1> 和 <condition 3> 都为 false 则执行的语句 */
    }
}
```

检查多个条件的另一种方法是使用 `else-if` 块。将有一个强制性的 `if` 块和一个可选的 `else` 块。在这两个块之间，你可以拥有任意数量的 `else-if` 块，每个 `else-if` 语句都有自己的条件。这样你就可以检查任意数量的条件。以下是通用语法：

```
if (<condition 1>) {
    /* 如果 <condition 1> 为 true，则执行此块。 */
} else if (<condition 2>) {
    /* 如果 <condition 1> 为 false 且 <condition 2> 为 true，则执行此块。 */
} else if (<condition 3>) {
    /* 如果 <condition 1> 和 <condition 2> 为 false 且 <condition 3> 为 true，则执行此块。 */
} else {
    /* 如果 <condition 1>、<condition 2> 和 <condition 3> 都为 false，则执行此块。 */
}
```

当存在 `if-else if-else` 块组合时，发生的过程是——首先检查 `if` 语句的条件。如果该条件求值为 `true`，则执行 `if` 块，故事到此结束！所有剩余的块都将被跳过。然而，如果条件求值为 `false`，执行控制将跳转到紧随其后的 `else if` 语句并检查其条件。如果求值为 `true`，则执行该特定的 `else if` 块，其余块被跳过。如果其条件求值为 `false`，控制将跳转到下一个 `else-if` 块（如果存在），并检查该块的条件。此过程将持续进行，直到找到一个有效的条件，或者不再有 `else-if` 块为止。如果没有任何条件求值为 `true`，则会执行 `else` 块（如果存在）。

让我们编写一个 Go 程序来检查给定的数字是正数、负数还是零：

```go
/* Positive Negative Zero */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 和 strconv 包 */
import (
    "fmt"
    "strconv"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明变量存储输入 */
    var num_str string

    fmt.Printf("\nEnter a number: ")

    /* 使用 Scanln 函数读取用户输入 */
    fmt.Scanln(&num_str)

    /* 将 num_str 转换为整数 */
    num, err := strconv.Atoi(num_str)

    /* 将 err 赋值给空标识符 */
    _ = err

    /* 检查 num > 0 */
    if (num > 0) {
        fmt.Printf("\n%d is positive.\n", num)
    } else if (num < 0) {
        fmt.Printf("\n%d is negative.\n", num)
    } else {
        fmt.Printf("\n%d is zero.\n", num)
    }
}
```

**输出：**
![](Image00044.jpg)

### 11.1.2 Switch-Case 构造

我们已经了解了如何使用多个 `else if` 块来检查多个条件的有效性。`switch-case` 构造提供了一种处理多个条件的更好方式。编写 `switch-case` 构造有多种方式，我们将介绍几种重要的方式。让我们从基本格式开始：

```
switch (<expression>) {
    case <constant expression 1>:
        /* 如果 <expression> 匹配 <constant expression 1> 则执行的语句 */
    case <constant expression 2>:
        /* 如果 <expression> 匹配 <constant expression 2> 则执行的语句 */
    case <constant expression 3>:
        /* 如果 <expression> 匹配 <constant expression 3> 则执行的语句 */
    ...
    case <constant expression n>:
        /* 如果 <expression> 匹配 <constant expression n> 则执行的语句 */
    default:
        /* 如果 <expression> 未找到匹配项则执行的语句 */
}
```

在这种 `switch-case` 构造语法中，`switch` 语句被赋予一个用于工作的表达式——在上述代码片段中标记为 `<expression>`。表达式可以像变量一样简单。在 `switch` 块内部，有多个 `case` 块，每个 `case` 语句都有一个常量表达式。当遇到 `switch` 语句时，其表达式会被求值。生成的值将与 `case` 块的常量表达式进行比对。如果生成的值与其中一个常量表达式匹配，则执行该特定的 `case` 块。这个过程称为**情况测试**。如果值与任何常量表达式都不匹配，则执行 `default` case 块（如果存在）。

这是一个简单的 `switch-case` 演示：

```go
/* Switch Demo 1 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 创建一个用于 switch 的变量 */
    Option := 3

    /* Switch Option，其中 Option 是赋值为 3 的 int 变量 */
    switch (Option) {
        /* 用于匹配 Option 的各种 case */
        case 1:
            fmt.Printf("\nOption is 1.\n")
        case 2:
            fmt.Printf("\nOption is 2.\n")
        case 3:
            fmt.Printf("\nOption is 3.\n")
        /* 如果没有匹配项的默认 case */
        default:
            fmt.Printf("\nOption does not match any of the cases.\n")
    }
}
```

**输出：**
![](Image00045.jpg)

在上述程序中，有 3 个 case，变量 `Option` 用于 switch。该变量已赋值为 `3`，让我们将 `Option` 改为 `1` 和 `9` 并观察结果：

**输出 (Option = 1)：**
![](Image00046.jpg)

**输出 (Option = 9)：**
![](Image00047.jpg)

用于 switch 的变量也可以在 `switch` 语句本身中设置，如下所示：

```
switch <optional statement, set variable> (<variable/expression>) {
    case <constant expression 1>:
        /* 如果 <expression> 匹配 <constant expression 1> 则执行的语句 */
    ...
    case <constant expression n>:
        /* 如果 <expression> 匹配 <constant expression n> 则执行的语句 */
    default:
        /* 如果 <expression> 未找到匹配项则执行的语句 */
}
```

让我们重写之前的程序，在 `switch` 语句本身中将 `Option` 设置为 `2`：

```go
/* Switch Demo 1 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* Switch Option，其中 Option 是在 switch 中短声明并赋值为 2 的 int 变量 */
    switch Option := 2; (Option) {
        /* 用于匹配 Option 的各种 case */
        case 1:
            fmt.Printf("\nOption is 1.\n")
        case 2:
            fmt.Printf("\nOption is 2.\n")
        case 3:
            fmt.Printf("\nOption is 3.\n")
        /* 如果没有匹配项的默认 case */
        default:
            fmt.Printf("\nOption does not match any of the cases.\n")
    }
}
```

**输出：**
![](Image00048.jpg)

编写 `switch-case` 构造的另一种方式是为每个 `case` 语句使用布尔表达式，如下所示：

```
switch {
    case <boolean expression 1>:
        /* 当 <boolean expression 1> 求值为 true 时执行的语句 */
    case <boolean expression 2>:
        /* 当 <boolean expression 2> 求值为 true 时执行的语句 */
    case <boolean expression 3>:
        /* 当 <boolean expression 3> 求值为 true 时执行的语句 */
    ...
    case <boolean expression n>:
        /* 当 <boolean expression n> 求值为 true 时执行的语句 */
    default:
        /* 当所有布尔表达式都为 false 时执行的语句 */
}
```

让我们编写一个程序从用户处读取一个数字并检查它是奇数还是偶数。我们将使用上述代码片段中的 `switch-case` 语法：

```go
/* Switch Demo 2 -- Odd or Even */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明一个变量存储数字 */
    var num int

    /* 提示用户输入数字并使用 scanf 读取 */
    fmt.Printf("\nEnter a number: ")
    fmt.Scanf("%d", &num)

    /* Switch num % 2 */
    switch {
        /* 针对每种结果的各种 case */
        /* 如果余数为零，则数字为偶数 */
        case (num % 2) == 0:
            fmt.Printf("\n%d is even.\n", num)
        /* 如果余数为一，则数字为奇数 */
        case (num % 2) == 1:
            fmt.Printf("\n%d is odd.\n", num)
    }
}
```

**输出：**
![](Image00049.jpg)

`switch-case` 构造可以使用任意基本数据类型的变量进行切换，不一定非要是数字。让我们编写一个程序要求用户输入月份名称并确定其序号：

```go
/* Switch Demo 3 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明一个变量存储月份名称 */
    var month string

    /* 提示用户输入月份名称并使用 scanf 读取 */
    fmt.Printf("\nEnter month: ")
    fmt.Scanf("%s", &month)

    /* Switch month */
    switch month {
        /* 每个月份的各种 case */
        case "January", "january":
            fmt.Printf("\nJanuary comes at No.1 in a year.\n")
        case "February", "february":
            fmt.Printf("\nFebruary comes at No.2 in a year.\n")
        case "March", "march":
            fmt.Printf("\nMarch comes at No.3 in a year.\n")
        case "April", "april":
            fmt.Printf("\nApril comes at No.4 in a year.\n")
        case "May", "may":
            fmt.Printf("\nMay comes at No.5 in a year.\n")
        case "June", "june":
            fmt.Printf("\nJune comes at No.6 in a year.\n")
        case "July", "july":
            fmt.Printf("\nJuly comes at No.7 in a year.\n")
        case "August", "august":
            fmt.Printf("\nAugust comes at No.8 in a year.\n")
        case "September", "september":
            fmt.Printf("\nSeptember comes at No.9 in a year.\n")
        case "October", "october":
            fmt.Printf("\nOctober comes at No.10 in a year.\n")
        case "November", "november":
            fmt.Printf("\nNovember comes at No.11 in a year.\n")
        case "December", "december":
            fmt.Printf("\nDecember comes at No.12 in a year.\n")
        /* 默认 case */
        default:
            fmt.Printf("\n%s does not seem like the name of a month!\n")
    }
}
```

**输出：**
![](Image00050.jpg)

请参考该程序，注意每个 `case` 如何拥有两个常量表达式。当你需要为多个常量表达式执行同一段代码时，不必编写带有不同常量表达式的单独 `case`，而是可以只编写一个 `case` 语句，其中包含用逗号分隔的多个常量表达式。

## 11.2 循环

循环是一种编程构造，可以根据条件是否满足，反复运行一段代码。Go 语言仅提供一种循环，称为 `for` 循环。

### 11.2.1 for 循环

`for` 循环的基本语法如下：

```
for <condition> {
    /* 只要 <condition> 为 true 就执行的语句 */
}
```

**示例：**

```
num := 0
for num < 5 {
    fmt.Printf("num = %d", num)
    num = num + 1
}
```

当执行控制遇到 `for` 循环时，会检查其条件。如果求值为 `true`，则执行循环块内的语句。这称为一次**循环迭代**。一旦到达循环块的末尾，执行控制将跳回 `for` 语句并再次检查条件。如果再次求值为 `true`，循环块将再次被执行。只要给定条件求值为 `true`，这种循环迭代就会持续发生。一旦求值为 `false`，执行控制将退出循环。如果条件永远不变为 `false`，循环将持续执行。这样的循环称为**无限循环**。

下面是一个使用 `for` 循环打印 0 到 9 的程序：

```go
/* For Demo 1 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 初始化一个整数变量为 0 */
    var count int = 0

    /* 运行从 0 到 9 的 for 循环 */
    for (count < 10) {
        /* 打印 count */
        fmt.Printf("count = %d\n", count)
        /* 增加 count */
        count++
    }
}
```

**输出：**
![](Image00051.jpg)

编写 `for` 循环的另一种方式是使用**循环变量**。以下是通用语法：

```
for <loop variable initialization>; <condition>; <loop variable increment/decrement> {
    /* 只要 <condition> 为 true 就执行的语句 */
}
```

使用这种语法，你可以在 `for` 语句本身中初始化循环变量。它还提供了一个增加/减少循环变量的选项。每次迭代结束时，将检查给定条件。如果求值为 `true`，循环变量将被增加/减少，然后循环块将作为下一次迭代被执行。如果循环变量之前未声明，也可以在 `for` 语句中短声明。

使用这种语法，让我们编写一个程序打印 5 的倍数。循环变量已在 `for` 语句中短声明：

```go
/* For Demo 2 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    fmt.Printf("\nMultiples of 5\n\n")

    /* 运行从 1 到 10 的 for 循环 */
    for count := 1; count <= 10; count++ {
        /* 打印 count * 5 */
        fmt.Printf("%d\n", count * 5)
    }
}
```

**输出：**
![](Image00052.jpg)

这是一个循环变量已预先声明的示例：

```go
/* For Demo 3 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明一个 int 变量 */
    var count int

    fmt.Printf("\nMultiples of 3\n\n")

    /* 运行从 1 到 20 的 for 循环 */
    for count = 1; count <= 20; count++ {
        /* 打印 count * 3 */
        fmt.Printf("%d\n", count * 3)
    }
}
```

**输出：**
![](Image00053.jpg)

### 11.2.2 控制语句

只要给定条件为 `true`，循环就会持续执行。这是循环的正常执行过程。可以使用 `continue` 和 `break` 等控制语句来改变循环的这种执行流程。

#### 11.2.2.1 continue 语句

当遇到 `continue` 语句时，执行控制将跳转到循环的开头，从而跳过 `continue` 语句之后的所有语句。换句话说，循环将移至下一次迭代。

让我们编写一个程序仅打印 1 到 30 之间的奇数：

```go
/* For Demo -- continue */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    fmt.Printf("\nOdd numbers between 1 and 30\n\n")

    /* 运行从 1 到 30 的 for 循环 */
    for count := 1; count <= 30; count++ {
        if (count % 2 == 0) {
            continue
        }
        fmt.Printf("%d\n", count)
    }
}
```

**输出：**
![](Image00054.jpg)

#### 11.2.2.2 break 语句

当遇到 `break` 语句时，循环的执行将停止，控制将退出循环。

让我们通过一个编程示例来理解这个概念。我们将运行一个从 1 到 10 的循环，当 `count` 变为 7 时跳出循环：

```go
/* For Demo -- break */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 运行从 1 到 10 的 for 循环 */
    for count := 1; count <= 10; count++ {
        if (count == 7) {
            break
        }
        fmt.Printf("count = %d\n", count)
    }
}
```

**输出：**
![](Image00055.jpg)

通过以下程序可以理解 `break` 语句更实用的用法，我们要求用户输入一个数字并判断它是质数还是合数：

```go
/* Prime or composite - using break */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明变量存储用户输入并作为循环计数器 */
    var i, num int

    /* 提示用户输入数字并使用 Scanf 读取 */
    fmt.Printf("\nEnter a number: ")
    fmt.Scanf("%d", &num)

    /* 从 2 运行循环到 num，因为每个数字都能被 1 整除 */
    for i = 2; i <= num; i++ {
        if (num % i == 0) {
            break
        }
    }

    if (num != i) {
        fmt.Printf("\n%d is a composite number.\n", num)
    } else {
        fmt.Printf("\n%d is a prime number.\n", num)
    }
}
```

**输出：**
![](Image00056.jpg)

让我们编写更多程序以更好地理解循环。以下程序计算给定数字的阶乘。数字 `n` 的阶乘表示为 `n! = n x (n -1) x (n - 2) x ... x 1`。负数的阶乘无法计算，零的阶乘是 1。

```go
/* Factorial */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明变量存储用户输入、循环计数器和阶乘 */
    var i, num int
    var f int = 1

    /* 提示用户输入数字并使用 Scanf 读取 */
    fmt.Printf("\nEnter a number: ")
    fmt.Scanf("%d", &num)

    /* 从 num 运行循环到 1 */
    for i = num; i > 0; i-- {
        f = f * i
    }

    if (num >= 0) {
        fmt.Printf("\nFactorial of %d is %d\n", num, f)
    } else {
        fmt.Printf("\nFactorial of a negative number cannot be calculated\n")
    }
}
```

**输出：**
![](Image00057.jpg)

让我们使用循环编写另一个程序，计算前 `n` 个偶数的和。

```go
/* Sum of n even numbers */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 强制性的 main 函数 */
func main() {
    /* 声明变量存储 n、循环计数器和和 */
    var i, n int
    var even_num, sum int = 1, 0

    /* 提示用户输入数字并使用 Scanf 读取 */
    fmt.Printf("\nEnter n: ")
    fmt.Scanf("%d", &n)

    fmt.Printf("\nFirst %d even numbers: \n\n", n)

    for i = 1; even_num <= n; i++ {
        if (i % 2 == 0) {
            fmt.Printf("%d ", i)
            sum += i
            even_num++
        }
    }

    fmt.Printf("\n\nSum of above even numbers: %d\n", sum)
}
```

**输出：**
![](Image00058.jpg)

