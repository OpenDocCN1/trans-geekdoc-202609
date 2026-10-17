
## 位运算符

| 运算符 | 说明 |
| --- | --- |
| `|` (位或) | 对两个操作数的每一位进行 OR 运算，如果两个位中有一个为 1 则返回 true。如果其中一个操作数位 1 则返回 1。 |
| `^` (位异或) | 对两个操作数的每一位进行 XOR 运算，如果两个位不同则返回 true。如果一个操作数的位为 0 而另一个位为 1 则返回 1，否则返回 false。 |
| `<<` (左移) | 第一个操作数的位向左移动 n 次。 |
| `>>` (右移) | 第一个操作数的位向右移动 n 次，其中 n 是第二个操作数的值。 |

**示例：**

```go
var a int = 50
var b int = 6
fmt.Println("a&b:", a&b) // a&b: 2
fmt.Println("a|b:", a|b) // a|b: 54
fmt.Println("a^b:", a^b) // a^b: 52
fmt.Println("a<<b:", a<<b) // a<<b: 24
fmt.Println("a>>b:", a>>b) // a>>b: 1
```

## 赋值运算符

`赋值运算符`用于设置或重置变量的值。它们可以用于给变量赋值，或通过评估任何特定表达式来改变变量的值。Go 语言中有多个赋值运算符。如下：

| 运算符 | 说明 |
| --- | --- |
| `=` | 将右侧的值赋值给左侧变量。 |
| `+=` | 左侧变量的值加上右侧计算的值，并将最终结果赋值给左侧。 |
| `-=` | 从左侧变量的值减去右侧计算的值，并将最终结果赋值给左侧。 |
| `*=` | 左侧变量乘以右侧计算的值。 |
| `/=` | 左侧变量的值除以右侧计算的值。 |
| `%=` | 对上述除法运算取模，并将最终结果赋值给左侧。 |
| `<<=` | 将左侧的值根据右侧的值向左移，并将最终结果赋值给左侧。 |
| `>>=` | 将左侧的值根据右侧的值向右移，并将最终结果赋值给左侧。 |
| `&=` | 对左侧变量的值和右侧计算的值进行位与，并将最终结果赋值给左侧。 |
| `^=` | 对左侧变量的值和右侧计算的值进行位异或，并将最终结果赋值给左侧。 |
| `|=` | 对左侧变量的值和右侧计算的值进行位或，并将最终结果赋值给左侧。 |
| `:=` | 将右侧的值赋值给之前定义的左侧变量。 |

**示例：**

```go
var a int = 50 //简单赋值
var b int = 5
a += b
fmt.Println("ex. of '+=' operator:", a) //prints ex. of '+=' operator: 55
a -= b
fmt.Println("ex. of '-=' operator:", a) //prints ex. of '-=' operator: 50
a *= 3
fmt.Println("ex. of '*=' operator:", a) //prints ex. of '*=' operator: 150
a /= b
fmt.Println("ex. of '/=' operator:", a) //prints ex. of '/=' operator: 30
a %= 7
fmt.Println("ex. of '%=' operator:", a) //prints ex. of '%=' operator: 2
b <<= 2
fmt.Println("ex. of '<<=' operator:", b) //prints ex. of '<<=' operator: 20
b >>= 2
fmt.Println("ex. of '>>=' operator:", b) //prints ex. of '>>=' operator: 5
a &= 10
fmt.Println("ex. of '&=' operator:", a) //prints ex. of '&=' operator: 2
a ^= 10
fmt.Println("ex. of '^=' operator:", a) //prints ex. of '^=' operator: 8
a |= 10
fmt.Println("ex. of '|=' operator:", a) //prints ex. of '|=' operator: 10
c := "hello world"
fmt.Println("ex. of ':=' operator:", c) //prints ex. of ':=' operator: hello world
```

## 杂运算符

Go 提供了其他特定语言的运算符。它们如下：

| 运算符 | 描述 |
| --- | --- |
| `Sizeof` | 该运算符用于获取任何类型任何变量的大小。我们有两个包，“reflect”和“unsafe”，它们提供了 `sizeof` 函数。 |
| `&` (地址运算符) | 地址运算符是一个一元运算符，它提供内存中存储指定变量的地址。 |
| `*` (指针/解引用运算符) | 这也是一个一元运算符，它提供存储在内存中操作数指定地址的变量的值。 |
| `<-` (接收运算符) | `<-ch` 是从通道 `ch` 接收到的值。 |

**示例：**

```go
package main
import (
    "fmt"
    "unsafe"
    "reflect"
)
func main(){
    var a int64 = 100
    fmt.Println("size of variable a:", unsafe.Sizeof(a)) //prints 8
    fmt.Println("size of variable a:", reflect.TypeOf(a).Size()) //prints 8
    fmt.Println("address of variable a:", &a) //prints Address of variable a: 0x1184e068
    fmt.Println("value of a at specified address:", *(&a)) //prints Address of variable a: 100
}
```

## 运算符优先级

**运算符优先级**决定了每个运算符的执行顺序，以便表达式能够正确求值。在计算表达式时，高优先级的运算符先求值。当我们有两个或多个表达式具有相同运算符或相同优先级的运算符时，就会涉及结合性。在这种情况下，表达式根据结合性规则从左到右或从右到左求值。

下表详细描述了每个运算符的结合性。

| 类别 | 运算符 | 结合性 |
| --- | --- | --- |
| `后缀 (Postfix)` | `() [] -> . ++ --` | `从左到右` |
| `一元 (Unary)` | `+ - ! ~ ++ -- (type)* & sizeof` | `从右到左` |
| `乘法 (Multiplicative)` | `* / %` | `从左到右` |
| `加法 (Additive)` | `+ -` | `从左到右` |
| `移位 (Shift)` | `<< >>` | `从左到右` |
| `关系 (Relational)` | `< <= > >=` | `从左到右` |
| `相等 (Equality)` | `== !=` | `从左到右` |
| `按位与 (Bitwise AND)` | `&` | `从左到右` |
| `按位异或 (Bitwise XOR)` | `^` | `从左到右` |
| `按位或 (Bitwise OR)` | `|` | `从左到右` |
| `逻辑与 (Logical AND)` | `&&` | `从左到右` |
| `逻辑或 (Logical OR)` | `||` | `从左到右` |
| `赋值 (Assignment)` | `= += -= *= /= %= >>= <<= &= ^= |=` | `从右到左` |

## 结论

在本章中，我们学习了关系、逻辑、位运算、赋值和杂类运算符。我们观察了运算符优先级是如何工作的。在学习完本章后，你需要：

## 问题

1. 运算符是什么意思？
2. 一元运算符是做什么的？
3. 什么是相等？
4. 什么是移位运算符？
5. 通道（channel）是如何工作的？
6. 什么是地址？
7. 什么是运算符？
8. 什么是移位？

# 第 6 章

## 控制结构

在 Go 语言中，我们有决策结构。这些是分支语句。

## 分支语句

### If/Else

`if` 语句有一个特定的条件。如果 `if` 内部给定条件为真，则执行 `if` 语句块；否则执行 `else` 语句。Go 程序可以包含多个 if-else 语句。

**示例：**

```go
package main
import "fmt"
func main() {
    var a int = 100
    var b int = 20
    if a==b{
        fmt.Println("a is equal to b")
    }else if a%b==0{
        fmt.Println("a is divisible by b")
    }else{
        fmt.Println("no match")
    }
}
```

**输出：**

```
a is divisible by b
```

### Switch

`switch` 语句类似于多个 `if-else` 语句，其中多个 `case` 替换了这些多个条件。我们需要比较的条件表达式放在 `switch` 语句中，并将求值结果与每个 `case` 值进行比较。与求值表达式匹配的 `case` 块将被编译器进一步执行。这里有一个可选的 `default` case，当没有 `case` 值与条件表达式匹配时将执行它。

**示例：**

```go
package main
import "fmt"
func main() {
    var a int = 100
    switch a{
    case 20:
        fmt.Println("value of a is 20")
    case 50:
        fmt.Println("value of a is 50")
    case 100:
        fmt.Println("value of a is 100")
    default:
        fmt.Println("switch loop processed")
    }
}
```

**输出：**

```
value of a is 100
```

## 循环语句

**循环语句**用于根据特定条件重复特定的代码块。循环条件决定了该特定代码块重复的次数。

### for

`for` 循环用于在有限次数内迭代特定的代码块。`for` 循环由三部分组成：变量的初始化、定义迭代次数的条件，以及在每次迭代后执行的后语句。首先，变量被初始化，然后检查条件。如果条件为真，则执行 `for` 循环内的代码块，然后执行后语句。该语句会改变变量的值，在下一次迭代中将通过给定的条件再次进行检查。如果发现条件为假，则停止迭代。此处的 `for` 循环不需要括号。为了定义代码块，始终使用大括号 `{}`。

**示例：**

```go
package main

import "fmt"

func main() {
    result := 1
    for i := 1; i < 10; i++ {
        result *= i
    }
    fmt.Println(result)
}
```

**输出：**

```
362880
```

## 跳转语句

`跳转语句`用于跳过程序中的特定代码或跳转到特定的代码块。

### `break`

`break` 语句用于在满足特定条件下立即终止循环。`break` 语句用于 `for` 循环或 `switch` 语句。在嵌套循环中，`break` 语句在给定条件下停止执行并跳转到循环外的下一条语句。

**示例：**

```go
package main

import "fmt"

func main() {
    var a int = 0
    for a < 20 {
        fmt.Printf("value of a: %d\n", a);
        a++;
        if a==5 {
            /* 使用 break 语句终止循环 */
            break;
        }
    }
}
```

**输出：**

```
value of a: 0
value of a: 1
value of a: 2
value of a: 3
value of a: 4
```

### `continue`

`continue` 语句与 `break` 语句类似。它不是终止循环，而是跳过当前迭代并跳转到下一次迭代。`continue` 语句也用于循环内的特定条件。

**示例：**

```go
package main

import "fmt"

func main() {
    var a int = 0
    for a < 5 {
        if a == 3 {
            /* 跳过迭代 */
            a = a + 1;
            continue;
        }
        fmt.Printf("value of a: %d\n", a);
        a++;
    }
}
```

**输出：**

```
value of a: 0
value of a: 1
value of a: 2
value of a: 4
```

### `exit`

`exit` 语句用于通过强制返回操作系统来终止程序执行。

**示例：**

```go
package main

import "fmt"
import "os"

func main() {
    var a string = "hello"
    fmt.Println("string value is: ", a)
    os.Exit(0)
    a = a+" world"
    fmt.Println("updated string value is: ", a)
}
```

**输出：**

```
string value is: hello
```

## 结论

在本章中，我们讨论了各种将控制流转移到特定代码块的控制语句。这些控制结构与机器无关且易于维护。它们提供了根据需要控制语句的灵活性。通过循环语句，我们学习了如何重复运行特定的代码块。在下一章中，我们将看到如何使用函数对多个值执行特定的代码块。

## 问题

1. Go 语言中的分支语句是什么？
2. `switch` 和嵌套的 `if-else` 语句之间有什么区别？
3. `switch` 语句中的默认情况是什么？
4. 循环语句是指什么意思？
5. `break` 语句的作用是什么？
6. 使用哪种语句可以跳过循环中针对特定值的代码块的执行？

# 第 7 章

## 函数

在编程过程中，可能需要对多个值重复执行特定任务，例如计算 100 个数字的阶乘。在这种情况下，我们可以定义一个执行该特定任务的代码块，并为每 100 个值调用一次该块。在编程语言中，这样的块被称为函数。让我们在本章中了解一下函数。

## 结构

在本章中，我们将讨论以下主题：

* 函数简介
* 函数声明
* 函数参数和返回值
* 函数调用
* 值传递
* 引用传递
* 命名值
* 匿名函数
* 递归函数
* Defer 关键字
* 可变参数函数

## 目标

学习本章后，你将能够：

* 使用单个块执行重复性任务
* 使用函数降低复杂性
* 传递多个值
* 从函数返回所需的类型

## 简介

函数在任何语言中都起着至关重要的作用。将程序分成多个函数可以降低复杂性、程序体积，并使源代码易于理解。函数是执行任务并产生输出的语句组。在 Go 语言中，有一个 `main` 函数，它是任何可执行程序的入口。`main` 函数既不接受参数也不返回任何值。`main` 函数的初始化是由 `init` 函数完成的。

**示例：**

```go
package main

import "fmt"

func init(){
    fmt.Println("initialization of main function")
}

func main() {
    fmt.Println("Program begins")
}
```

**输出：**

```
initialization of main function
Program begins
```

## 函数声明

函数声明的第一行提供了函数的基本信息。它被称为函数的签名。它包含 `func` 关键字、函数名称、可选的逗号分隔的输入值列表（称为参数），以及带有特定类型的返回值。然后是一对大括号，指定了执行特定任务的函数体。

**语法：**

```go
func [function_name] (optional_inputval1 type, optional_inputval2 type..) (optional_returnval1 type, optional_returnval2 type){
    //函数体
}
```

**示例：**

```go
func first_function(){
    fmt.Println("Hi….I am introducing a function")
}
```

## 函数参数和返回值

在 Go 语言中，我们可以向函数传递零个或许多个参数。同样，函数也可以返回零个或多个值。在调用函数时，传递给函数的参数被称为**实际参数**，而在函数声明中由函数接收的值被称为**形式参数**。根据上述的签名，让我们创建一个处理两个整数的函数。这里有一个示例，它接受两个整数输入值并返回它们的和，和也是一个整数值。
