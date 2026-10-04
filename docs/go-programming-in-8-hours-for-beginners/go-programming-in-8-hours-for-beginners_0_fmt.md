

# Go 编程入门指南：8 小时快速通

## 关于作者

- 美国 `Zend` 认证的 PHP 工程师
- 美国 Sun 认证的 JAVA 程序员
- 美国 Oracle 认证的 SCWCD 开发者
- 美国 CompTIA 认证的 A+ 专业人士
- 微软认证的 ASP.NET 专家
- 微软认证的 MCP 专业人士
- 微软认证的 TECHNOLOGY（技术）专家
- 美国 CompTIA 认证的 NETWORK+ 专业人士

## 前言

《8 小时 Go 语言编程》涵盖了所有核心 Go 语言知识。你可以快速轻松地掌握 Go 编程技能。

本书包含了适用于初学者的实用示例，并包含了适用于考试、工程师认证和工作面试的测试。

### 源代码下载

本书提供了源代码下载，你可以将源代码下载到你喜欢的编辑器中进行测试。

下载链接：`https://forms.aweber.com/form/34/180549243.htm`

## 什么是 Go？

Go 是 Google 在 2009 年发布的开源编程语言。Go 是一种全新的、并发且带有垃圾回收的编译语言。它有一个很大的特点：可以在几秒钟完成大型 Go 程序的编译。

Go 提供了一种构建模型，使得依赖分析变得更容易。Go 是一种静态类型语言，其类型定义没有层次结构，因此用户不需要花时间定义类型之间的关系，这让用户觉得它比典型的面向对象的语言轻量。

Go 提供了一种在多核机器上构建系统软件的方法。Go 语言编程针对多处理器应用程序进行了优化，比 C 或 C++ 代码更快，并更安全地支持并行进程。

### Go 语言的特点

1. 简单、快速安全
2. 并发、有趣、开源
3. 内存管理、数组安全、快速编译

## 安装 Go

本书以 Windows 操作系统作为安装 Go 的示例。下载链接：[`golang.org/dl/`](https://golang.org/dl/)

1. 点击链接，进入下载页面。
2. 点击 `go1.11.2 windows-amd64.msi`，将 Go 安装程序下载到本地计算机。
3. 点击 Go 安装程序，开始安装……默认情况下，Msi 文件将安装在 `c:\Go` 目录下。
4. 点击 `Next`。
5. 安装完成后，请点击 `Finish`。

### 环境变量

安装 Go 之后，你需要将 `c:\Go\bin` 添加到环境变量的 `PATH` 中。请配置环境变量。前往“控制面板” > “系统” > “高级系统设置” > “高级” > “环境变量” > `Path` > “编辑” > “新建”。将 `C:\Go\bin` 添加到 `Path` 的末尾。

注意：不同 Windows 操作系统的设置界面有所不同。请重启计算机使设置生效。

### Go 的第一个程序

请在 `C:\` 下创建一个工作文件夹 `myGo`，打开记事本编辑器，并将以下代码写入编辑器。示例 1.1

```go
package main
import "fmt"
func main() { 
    fmt.Println("Hello, World! ") 
}
```

将文件保存为 `hello.go` 并存放在 `C:\myGo` 中。使用 `cmd` 打开命令行，输入以下命令：

输出：Hello World!

**解释：**

- `package main` 定义包名为 `main`。每个 Go 应用程序必须包含一个名为 `main` 的包。
- 导入的包 `fmt` 包含 I/O 函数。
- `func main()` 是 Go 应用程序执行的第一个函数。
- `fmt.Println("Hello, World! ")` 输出文本 `Hello, World! `。
- `C:\Windows\system32>cd\` 返回 `C:` 根目录。
- `C:\cd myGo` 进入 `myGo` 文件夹。
- `go run` 是执行 Go 程序的命令。

### 注释

- `//` 是单行注释的符号。
- `/*` 和 `*/` 是多行注释的符号。
- 注释不会被编译。Go 编译器将忽略所有注释。示例 1.2

```go
package main  // 包声明
import "fmt" 
func main() {
    // 定义 main 函数
    fmt.Println("Hello, World! ") 
} 
/* 上述代码的输出是: Hello, World! */
```

请使用 `go run` 命令运行此程序并检查结果。

### 标识符

标识符用于命名变量、函数、表达式等。标识符由一个或多个字母（A~Z 和 a~z）、数字（0~9）和下划线组成，但第一个字符必须是字母或下划线。标识符的首字符不能是数字。

**有效的标识符：**

- `myVariable`
- `_Variable`
- `variable100`

**无效的标识符：**

- `continue`（`continue` 是 Go 语言的关键字）
- `100Variable`（以数字开头）

## 总结

- `package main` 定义包名为 `main`。每个 Go 应用程序必须包含一个名为 `main` 的包。
- 导入的包 `fmt` 包含 I/O 函数。
- `func main()` 是 Go 应用程序执行的第一个函数。
- `fmt.Println("Hello, World! ")` 输出文本 `Hello, World! `。
- `//` 是单行注释的符号。
- `/*` 和 `*/` 是多行注释的符号。注释不会被编译。Go 编译器将忽略所有注释。
- 标识符用于命名变量、函数、表达式等。标识符由一个或多个字母（A~Z 和 a~z）、数字（0~9）和下划线组成，但第一个字符必须是字母或下划线。标识符的首字符不能是数字。

## 第二小时

### 行分隔符

在 Go 语言中，每个语句不需要用分号来结束行。例如：

```go
fmt.Println("Hi, My friend! ")
fmt.Println("Hi, Guy! ")
```

上述代码中有两行，每一行代表一个语句的结束，每个语句不需要分号来结束行。

关于以下内容：

```go
fmt.Println("Hi, My friend! ")
fmt.Println("Hi, Guy! ")
```

以下代码会在运行时产生错误：

```go
func main() {
```

Go 语言中有 25 个关键字：`break`, `case`, `default`, `chan`, `const`, `continue`, `decl`, `else`, `for`, `func`, `go`, `import`, `interface`, `map`, `package`, `select`, `struct`, `switch`, `type`, `var`, `range`, `return`, `fallthrough`, `goto`。

### 数据类型

在 Go 中，我们定义变量。四种数据：

1. **布尔型：** `bool`
2. **数值型：** `int`, `int8`, `int16`, `int32`, `int64`, `uint`, `uint8`, `uint16`, `uint32`, `uint64`, `float32`, `float64`, `complex64`, `complex128`
3. **字符串型：** `string`
4. **派生类型：** `array`, `slice`, `map`, `struct`, `interface`, `pointer`

### 变量声明

有三种声明变量的方法：

1. `var name type value`
2. `var name = value`
3. `name := value`

示例：

```go
var a int = 100
var b = 200
c := 300
```

示例 2.1

```go
package main
import "fmt"
func main() {
    var a = "C# in 8 Hours"
    var b = "is a book!"
    var c = true
    fmt.Println(a, b, c)
}
```

输出：C# in 8 Hours is a book! true

示例 2.2

```go
package main
import "fmt"
func main() {
    var a, b, c int = 100, 200, 300
    var d, e, f = 400, 500, 600
    s1, s2, s3 := "R in 8 Hours", "is", "good book."
    fmt.Println(a, b, c)
    fmt.Println(d, e, f)
    fmt.Println(s1, s2, s3)
}
```

输出：

```
100 200 300
400 500 600
R in 8 Hours is a good book.
```

## 总结

在 Go 语言中，每个语句都不需要分号来结束行。`{` 不能被放在单行上，因此以下代码在运行时产生错误。关键字不能作为变量、常量和函数等的标识符。Go 语言的变量名由字母、数字和下划线组成，其中第一个字符不能是数字。

有三种方法声明多变量：

1. `var vname1, vname2, vname3 type vname1, vname2, vname3 = v1, v2, v3`
2. `var vname1, vname2, vname3 = v1, v2, v3`
3. `vname1, vname2, vname3 := v1, v2, v3`

`:=` 赋值运算符用于给变量赋值。

## 第 3 小时

### 常量

常量是在程序运行期间值不会改变的标识符。定义常量的语法为：

```
const constant_name [type] = value
```

或者

```
const constant_name = value
```

#### 示例 3.1

```go
package main
func main() {
    const x, y, z int = 10, 20, 30  // 定义三个常量
    const s = "jQuery in 8 Hours! "
    const b bool = true
    println(x, y, z)
    println(s)
    println(b)
}
```

**输出：** 10 20 30 jQuery in 8 Hours! true

**解释：** `const` 用于定义常量。

#### 示例 3.2

```go
package main  // 以枚举定义常量
func main() {
    const (
        // 枚举
        color1 = "Blue"
        color2 = "Pink"
        color3 = "Gray"
    )
    println(color1, color2, color3)
}
```

**输出：** Blue Pink Gray

**解释：** 常量 `color1`, `color2`, `color3` 以枚举模式定义。

### iota

`iota` 是一个特殊的常量。第一个 `iota` 的值等于 0，每当在的一行中使用 `iota` 时，它的值就会自动加 1。

#### 示例 3.3

```go
package main
func main() {
    const (
        x = iota  // 第一个 iota 值为 0
        y = iota
        z = iota
    )
    println(x)
    println(y)
    println(z)
}
```

**输出：** 0 1 2

**解释：** 第一个 `iota` 值为 0，第二个 `iota` 值为 1，第三个 `iota` 值为 2。

### 算术运算符

| 运算符 |
| :--- |
| `+` |
| `-` |
| `*` |
| `/` |
| `%` |
| `++` |
| `--` |

例如：

给定：`a = 100`, `b = 2`

计算：

- `a + b` 返回 102
- `a – b` 返回 98
- `a * b` 返回 200
- `a / b` 返回 50
- `a % b` 返回 0
- `a ++` 返回 101
- `a --` 返回 99

### 关系运算符

| 运算符 |
| :--- |
| `>` |
| `<` |
| `>=` |
| `<=` |
| `==` |
| `!=` |

例如：

给定：`a = 100`, `b = 2`

计算：

- `a > b` 返回 true
- `b < a` 返回 false
- `a >= b` 返回 true
- `a <= b` 返回 false
- `a == b` 返回 false
- `a != b` 返回 true

### 逻辑运算符

| 运算符 |
| :--- |
| `&&` |
| `||` |
| `!` |

例如：

给定：`a = true`, `b = false`

计算：

- `a && b` 返回 false
- `a || b` 返回 true
- `! a` 返回 false

**解释：**

| 表达式 | 结果 |
| :--- | :--- |
| `true && true` | `true` |
| `true && false` | `false` |
| `false && false` | `false` |
| `true || true` | `true` |
| `true || false` | `true` |
| `false || false` | `false` |

### 赋值运算符

| 运算符 | 示例 |
| :--- | :--- |
| `+=` | `x += y` |
| `-=` | `x -= y` |
| `*=` | `x *= y` |
| `/=` | `x /= y` |
| `%=` | `x %= y` |

示例：

给定：`x = 200`, `y = 100`

- `x += y` 输出 300
- `x -= y` 输出 100
- `x *= y` 输出 20000
- `x /= y` 输出 2
- `x %= y` 输出 0

### 运算符优先级

下表列出了运算符优先级（从上到下表示从高到低）：

| 优先级 | 运算符 |
| :--- | :--- |
| 7 | `*`, `/`, `%` |
| 6 | `+`, `-` |
| 5 | `<<`, `>>` |
| 4 | `<`, `<=`, `>=`, `>` |
| 3 | `==`, `!=` |
| 2 | `&&` |
| 1 | `||` |

## 总结

常量是在程序运行期间值不会改变的标识符。定义常量的语法为：`const constant_name [type] = value` 或 `const constant_name = value`。

`iota` 是一个特殊的常量。第一个 `iota` 的值等于 0，每当在的一行中使用 `iota` 时，它的值就会自动加 1。后续有运算符：算术运算符、关系运算符、逻辑运算符、赋值运算符。

## 第 4 小时

### If 语句

`if` 语句：`if expression` 只有当条件为真时执行 `{}` 中的代码。

#### 示例 4.1

```go
package main
func main() {
    if 10 > 5 {
        println("greater")
    }
}
```

**输出：** greater

**解释：** `10 > 5` 为真，因此执行了块。

### else 语句

如果 `if` 条件为假，则执行 `else` 块中的代码。

#### 示例 4.2

```go
package main
func main() {
    if 10 < 5 {
        println("less")
    } else {
        println("greater")
    }
}
```

**输出：** greater

**解释：** `10 < 5` 为假，执行了 `else` 块。

### else if 语句

如果前面的 `if` 条件为假，可以使用 `else if` 检查另一个条件。

#### 示例 4.3

```go
package main
func main() {
    if 10 > 5 {
        println("greater")
    } else if 10 == 5 {
        println("equal")
    } else {
        println("less")
    }
}
```

**输出：** greater

**解释：** `10 > 5` 为真，执行了第一个块。

### switch 语句

`switch` 语句允许根据多个值执行不同的代码块。

#### 示例 4.4




# Go 语言控制流与数据结构

## switch 语句

```go
package main
func main() {
    os := 2
    switch os {
    case 1:
        println("one")
    case 2:
        println("two")
    case 3:
        println("three")
    }
}
```

**输出：** two

**解释：** `os` 的值为 2，匹配到 `case 2`。

### break 语句

在 Go 的 `switch` 中，每个 `case` 后面都有隐含的 `break`，不需要手动编写。

### 示例 4.5

```go
package main
func main() {
    switch 2 {
    case 1:
        println("one")
    case 2:
        println("two")
        break
    case 3:
        println("three")
    }
}
```

**输出：** two

**解释：** 匹配到 `case 2` 后遇到 `break`，退出 `switch`。

### default 语句

如果没有 `case` 匹配，则执行 `default` 块。

### 示例 4.6

```go
package main
func main() {
    switch 5 {
    case 1:
        println("one")
    default:
        println("default")
    }
}
```

**输出：** default

**解释：** 没有匹配的项，执行了 `default`。

### 多值 case

一个 `case` 可以包含多个可能的值。

### 示例 4.7

```go
package main
func main() {
    switch 2 {
    case 1, 2:
        println("one or two")
    case 3:
        println("three")
    }
}
```

**输出：** one or two

**解释：** `2` 匹配了 `case 1, 2`。

### 无表达式 switch

如果 `switch` 后面没有跟表达式，它将充当一个更简洁的 `if-else` 链。

### 示例 4.8

```go
package main
func main() {
    n := 15
    switch {
    case n > 20:
        println("large")
    case n > 10:
        println("medium")
    default:
        println("small")
    }
}
```

**输出：** medium

**解释：** `n > 10` 为真。

## 总结

`if statement` 只有在指定条件为真时才执行 `{ … }` 内部的代码，如果条件为假，则不执行 `{…}` 中的任何代码。在 `switch statement` 中，变量的值将首先与每个 `case` 进行比较，如果等于其中一个 `case` 值，它将执行该 `case` 代码。`Select Statement` 有点像 `Switch Statement`。`Switch Statement` 按照顺序执行 case 代码。`Select Statement` 随机执行 case 代码。`For Loop` 是一种可以执行指定次数循环的控制结构。

# 第 5 小时

## break

`break` 语句用于终止循环。`Break` 语句也用于终止 `switch statement` 中的 `case`。

### 示例 5.1

```go
package main
func main() {
    var num int = 20
    for num < 30 {
        print(num," ");
        num++;
        if num > 25 {
            break;     // 终止 for 循环
        }
    }
}
```

**Output:** 20 21 22 23 24 25

**Explanation:** 如果 `num > 25` 是测试表达式，如果为真，`break` 语句将终止循环。

## continue

`continue` 语句跳过当前循环并执行下一次。

### 示例 5.2

```go
package main
func main() {
    var num int = 20
    for num < 30 {
        if num == 25 {
            num = num + 1;
            continue;     // 跳过当前的 for 循环
        }
        print(num, " ")
        num++;  
    }
}
```

**Output:** 20 21 22 23 24 26 27 28 29

**Explanation:** 如果 `num == 25` 是测试表达式，如果为真，`continue` 语句将跳过当前的 for 循环并执行下一次。

**Note：** 结果中没有 25。

## goto

`goto label; ... label: statement;`

`goto` 语句可以跳转到指定的代码并无条件地执行。

### 示例 5.3

```go
package main
func main() {
    var num int = 10
    if num > 10{
        goto code01
    }
    if num == 10{
        goto code02
    }
    code01: print("num > 10")
    code02: print("num == 10")
}
```

**Output:** num == 10

**Explanation:** `goto code01` 意味着执行标签为 `code01` 的语句。`goto code02` 意味着执行标签为 `code02` 的语句。

## Function

函数是一个重复用于执行相同任务的代码块。

(1) 定义函数的语法如下：

`func function_name ( parameter type) type { …… return … }`

`func`: 定义函数

`return`: 将结果传递给调用者。

(2) 调用函数的语法如下：

`variable = function_name ( parameter type )`

### 示例 5.4

```go
package main
func main() {
    var a int = 10
    var b int = 20
    var result int
    result = add(a, b)    // 调用函数
    print( "The sum is ", result )
}
func add(num1, num2 int) int {
    // 定义一个函数
    return num1 + num2 // 将结果传递给调用者
}
```

**Output:** The sum is 30

**Explanation:** `add(a, b)` 调用函数 `add(a, b)`，并将参数 `a` 和 `b` 的值传递给 `num1` 和 `num2`。`func add(num1, num2 int) int` 定义了函数 `add(...)`，`num1` 和 `num2` 接收来自 `a` 和 `b` 的值。`return num1 + num2` 将结果传递给调用者 `add(...)`。

### 示例 5.5

```go
package main
import "fmt"
func swap(a, b string) (string, string) {
    // 定义一个函数
    return b, a // 向调用者返回两个值
}
func main() {
    x, y = swap("8 Hours", "JavaScript") // 调用函数
    fmt.Println(x, y)
}
```

**Output:** JavaScript 8 Hours

**Explanation:** `func swap(a, b string) (string, string) {…}` 定义了一个函数。`swap("8 Hours", "JavaScript")` 调用函数 `swap(...)` 并将参数传递给函数。

## Working Scope

任何编码中的作用域是变量可以访问的范围，在该范围之外无法访问该变量。

在函数内部定义的变量称为局部变量。

在函数外部定义的变量称为全局变量。

### 示例 5.6

```go
package main
func main() {
    var a, b, c int // 定义局部变量
    a = 100
    b = 200
    c = a + b
    print(a, b, c)
}
```

**Output:** 300

**Explanation:** `var a, b, c int` 在函数 `main` 内部定义了三个局部变量。

### 示例 5.7

```go
package main
var v int = 100
```

（注：原文提供的示例 5.7 文本不完整，此处按原文提供的内容翻译）

# 第 6 小时

## 指针

指针代表内存地址的值。

例如：`var ipoint *int` // 声明一个 int 指针

`var fpoint *float32` // 声明一个 float32 指针

`*ipoint` // 获取内存地址中的 ipoint 值

`*fpoint` // 获取内存地址中的 fpoint 值

### 示例 6.6

```go
package main
import "fmt"
func main() {
    var num int= 100
    var pt *int // 声明一个指针 pt
    pt = &num // &num 获取地址并赋值给 pt
    fmt.Printf("The address of num: %x\n", &num)
    fmt.Printf("The address in pt: %x\n", pt)
    fmt.Printf("The value of the *pt: %d\n", *pt)
}
```

**输出：**

```
The address of num: C000044058
The address in pt: C000044058
The value of the *pt: 100
```

**解释：**

`&num` 从 `num` 获取内存地址。

`pt = &num` 将内存地址赋值给 `pt`。

`*pt` 返回内存地址中的 `pt` 值。

### 示例 6.7

```go
package main
import "fmt"
func main() {
    var a string="Hello"
    var b *string
    var c string
    b=&a //&a 获取内存地址
    c=*b //*b 获取内存地址中的值
    fmt.Println(a)
    fmt.Println(b)
    fmt.Println(c)
}
```

**输出：**

```
Hello
0xc0000381c8
Hello
```

**解释：**

`&variablename` 返回一个内存地址。

`*variable` 返回内存地址中的值。

### 空指针 (Nil Pointer)

当指针被定义但没有赋值给任何变量地址时，它的值为 `nil`。

### 示例 6.8

```go
package main
import "fmt"
func main() {
    var npt *int
    fmt.Printf("The address stored in npt: %x\n", npt)
}
```

**输出：**

```
The address stored in npt: 0
```

**解释：** `npt` 是一个指针，尚未被分配任何地址，因此 `npt` 的值为 0。

## 总结

数组是相同类型和同名变量的集合。

- **数组元素**：数组中的每个变量。
- **数组索引**：也称为键（key），每个元素上的数字。
- **注意**：数组索引或数组键从零开始计数。
- 指针代表内存地址的值。
- `&variable` // 获取变量的内存地址
- `var variable_name *type` // 声明一个指针
- `*variable_name` // 获取地址中的变量值
- 当指针被定义但没有赋值给任何变量地址时，它的值为 `nil`。

# 第 7 小时

## 结构体 (Structures)

结构体是相同或不同类型数据的集合。

### (1) 定义结构体类型

```go
type structure_name struct {
    member1 type;
    member2 type;
    ...
    member3 type;
}
```

### (2) 访问结构体成员

```go
structure_name{member1: value1, member2: value2, … }
```

### 示例 7.1

```go
package main
import "fmt"
type Flower struct {
    // 定义一个结构体类型
    color string // 结构体成员
    size string
    number int
}
func main() {
    fmt.Println(Flower{color:"Red", size:"Large", number:10 })
}
```

**输出：**

```
Red
Large
10
```

**解释：** `type Flower struct` 定义了一个结构体类型。

### (3) 声明结构体变量

```go
var variable structure_name
```

### (4) 给结构体成员赋值

```go
variable.member = value
```

### 示例 7.2

```go
package main
type Flower struct {
    // 定义一个结构体类型
    color string // 结构体成员
    size string
    number int
}
func main() {
    var Rose Flower // 声明一个结构体变量
    Rose.color = "Red" // 给结构体成员赋值
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

**解释：** `var Rose Flower` 声明了一个结构体变量 `Rose`。`Rose.color = "Red"` 给结构体成员 `Rose.color` 赋值。

## 切片 (Slice)

切片是一种特殊的数组，它的长度是可变的。

### (1) 创建切片的第一种语法：

```go
slice_name := []type{val1, val2, …
```

### 示例 7.3

```go
package main
import "fmt"
func main(){
    s := []int{1,2,3,4,5} // 创建切片
    fmt.Println(s)
}
```

**输出：**

```
1 2 3 4 5
```

**解释：** `s := []int{1,2,3,4,5}` 创建了一个包含五个值的切片。

### (2) 创建切片的第二种语法：

```go
slice_name := make([]type, len, cap)
```

`len` 表示切片的长度，`cap` 表示容量。

### 示例 7.4

```go
package main
import "fmt"
func main() {
    s := make([]int, 5, 8)
    fmt.Printf("len=%d cap=%d\n", len(s), cap(s))
}
```

**输出：**

```
len=5 cap=8
```

**解释：** `len(s)` 获取切片的长度。`cap(s)` 获取容量。由于切片元素尚未赋值，该切片的值为零。

### (3) 从切片中获取某些值：

```go
slice_name[key1:key2]
```

获取从 `key1` 到 `key2` 的值。

### 示例 7.5

```go
package main
import "fmt"
func main() {
    var s = []int{0, 1, 2, 3, 4, 5, 6, 7}
    mySlice := s[2:6] // 从 s[2] 到 s[5] 获取值
    fmt.Println(mySlice)
}
```

**输出：**

```
2 3 4 5
```

**解释：** `s[2:6]` 获取从 `s[2]` 到 `s[5]` 的值。

### (4) 给切片元素赋值。

```go
slice_name[key] = value
```

### 示例 7.6



```go
package main
import "fmt"
func main() {
    var s = []int{0, 1, 2, 3, 4, 5, 6, 7}
    s[3] = 10 // 给 s[3] 赋值新值
    s[6] = 100 // 给 s[6] 赋值新值
    fmt.Println(s)
}
```

输出：

```
0 1 2 10 4 5 100 7
```

解释：`s[3] = 10` 和 `s[6] = 100` 赋值了新值。

## `append()` & `copy()`

```go
append(slice_name, values) // 向切片追加值
copy(new_slice, old_slice) // 将旧切片拷贝到新切片
```

### 示例 7.7

```go
package main
import "fmt"
func main() {
    mySlice := make([]int, 0, 0)
    showSlice(mySlice)
    mySlice = append(mySlice, 10, 20, 30) // append
    showSlice(mySlice)
    newSlice := make([]int, len(mySlice), cap(mySlice)*2) // copy
    copy(newSlice, mySlice)
    showSlice(newSlice)
}
func showSlice(x []int){
    fmt.Printf("len=%d cap=%d slice=%v\n", len(x), cap(x), x)
}
```

输出：

```
len=0 cap=0 slice=[]
len=3 cap=4 slice=[10 20 30]
len=3 cap=8 slice=[10 20 30]
```

解释：`append(mySlice, 10, 20, 30)` 向 `mySlice` 追加了三个值。`cap(mySlice)*2` 使容量翻倍。`copy(newSlice, mySlice)` 将 `mySlice` 的内容拷贝到 `newSlice`。

# 总结

结构体是相同或不同类型数据的集合。

- **(1) 定义结构体类型**：

```go
type structure_name struct {
    member1 type;
    member2 type;
    ...
    member3 type;
}
```

- **(2) 访问结构体成员**：`structure_name{member1: value1, member2: value2, …}`

- **(3) 声明结构体变量**：`var variable structure_name`

- **(4) 给结构体成员赋值**：`variable.member = value`

- 切片是一种特殊的数组，但它的长度是可变的。

- `append(slice_name, values)` // 向切片追加值

- `copy(new_slice, old_slice)` // 将旧切片拷贝到新切片

# 第 8 小

## GOROUTINE (协程)

“goroutine”用于同时运行多个任务，这意味着 goroutine 函数可以通过使用 `go` 关键字同时执行多个线程。以下示例是定义一个 goroutine 函数并运行该 goroutine 函数。

```go
go func(arguments) {
    // 定义一个 goroutine 函数
} (arguments) // 运行 goroutine 函数
```

### 示例 8.1

```go
package main
import "fmt"
func fn(s string) {
    // 定义一个用于...循环的函数
    for i := 0; i < 5; i++ {
        fmt.Println(s)
    }
}
func main() {
    fn("Thread B") // 调用函数
    go func(msg string) {
        // 定义一个 goroutine 函数
        fmt.Println(msg)
    } ("Press Enter to Stop! ") // 运行 goroutine 函数
    fmt.Scanln() // 接收键盘用户输入
    fmt.Println("Complete! ")
}
```

输出：

```
Thread B
Thread B
Thread B
Thread B
Thread B
Press Enter to Stop!
Complete! 
```

解释：`go func(msg string) {…}` 定义了一个 goroutine 函数。`("Press Enter to Stop! ")` 运行 goroutine 函数，并将参数传递给 goroutine 函数。

## Range

`Range` 是 Go 语言的内置函数，用于遍历数组、切片、字符串和 map。

- 遍历数组、切片、字符串会返回索引和值。

- 遍历 map 会返回键和值。

- 遍历通道（channel）返回值。

### (1) 遍历数组/切片

```go
for key, value : = range array/slice { }
```

**示例 8.2**

```go
package main
import "fmt"
func main(){
    for key, value : = range []int{10, 11, 12, 13} {
        fmt.Printf("key:%d  value:%d\n", key, value)
    }
}
```

**输出：**

```
key: 0    value: 10
key: 1    value: 11
key: 2    value: 12
key: 3    value: 13
```

**解释：** `range []int{10, 11, 12, 13}` 遍历了一个数组或切片，并返回键和值。

### (2) 遍历字符串

```go
for key, value : = range str { }
```

**示例 8.3**

```go
package main
import "fmt"
func main(){
    var str = "hello"
    for key, value : = range str {
        fmt.Printf("key:%d value:0x%x\n", key, value)
    }
}
```

**输出：**

```
key : 0    value : 0x68
key : 1    value : 0x65
key : 2    value : 0x6c
key : 3    value : 0x6c
key : 4    value : 0x6f
```

**解释：** `range str { }` 遍历一个字符串，返回其键和值。

### (3) 遍历通道

```go
for value : = range channel
```

**示例 8.4**

```go
package main
import "fmt"
func main(){
    c : = make(chan int)
    go func() {
        // 定义一个 goroutine 函数
        c <- 1    // 向通道发送数据
        c <- 2
        c <- 3
        close(c)  // 关闭通道
    }() // 调用该 goroutine 函数
    for v := range c {
        // 遍历通道
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

**解释：** `range c` 遍历通道。`go func(){}` 定义了一个 goroutine 函数。`()` 调用了该 goroutine 函数。

## Map 

`Map` 是一个无序的键值对集合。`Map` 用于通过键快速检索数据，类似于索引并指向数据的值。定义 map 的两种语法如下：

### (1)

```go
m1 : = map[key_type]value_type{}
```

**解释：** `m1` 是一个 map。

### (2)

```go
m2 : = make(map[key_type]value_type)
```

**解释：** `m2` 是一个 map。

**示例 8.5**

```go
package main
import "fmt"
func main(){
    m1 := map[int]int{1:10} = 10
    m1[2] = 20
    for key, value : = range m1 {
        fmt.Println("Key: ", key, "Value:", value)
    }
    m2 := make(map[int]int)
    m2[1] = 10
    m2[2] = 20
    for key, value : = range m2 {
        fmt.Println("Key: ", key, "Value:", value)
    }
}
```

**输出：**

```
Key:  1 Value: 10
Key:  2 Value: 20
Key:  1 Value: 10
Key:  2 Value: 20
```

*(注：顺序可能会变化，因为 map 是无序的)*

# 类型转换

类型转换意味着将变量的一种数据类型转换为另一种类型。

### (1)

```go
data_type (variables)
```

**示例 8.6**

```go
package main
import "fmt"
func main(){
    var num1 int = 100
    var num2 int = 33
    var result float32 = float32(num2)
    fmt.Printf("The result is %f\n", result)
}
```

**输出：**

```
The result is 33.000000
```

**解释：** `float32(num2)` 了数据类型。

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

**示例 8.7**

```go
package main
import "fmt"
func myRecur(n int) int {
    if n == 0 {
        return 1
    }
    return n * myRecur(n-1)
}
func main() {
    fmt.Print("Factorial of 10 is ")
    fmt.Print(myRecur(10))
}
```

**输出：**

```
Factorial of 10 is 3628800
```

**解释：** `myRecur(n-1)` 调用了它自己。在出现 `myRecur(0)` 之前，递归不会停止。

# 总结

`goroutine` 用于同时运行多个任务，这意味着 goroutine 函数可以通过 `go` 关键字同时执行多个线程。`Range` 是 Go 语言的内置函数，用于遍历数组、切片、字符串和 map。`Map` 是一个无序的键值对集合。`Map` 用于通过键快速检索数据，类似于索引并指向数据的值。`类型转换`意味着将变量的一种数据类型转换为另一种类型。`data_type (variables)` `递归` 意味着函数调用自己。

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

Go 语言支持并发，我们可以使用 `go` 关键字调用函数，启动一个新的运行时线程 goroutine。使用 `go` 关键字调用函数的语法如下：

```go
go function_name(arguments)
```

**示例：**

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
    }("Press Enter to Stop! ") // 运行 goroutine 函数
    fmt.Scanln() // 接受键盘用户输入
    fmt.Println("Complete! ")
}
```

**输出：**

```
Thread B
Thread A
Thread B
Thread A
Thread B
Thread A
Thread B
Thread A
Thread B
Press Enter to Stop!
Complete! 
```

**解释：** `go fn("Thread A")` 使用 `go` 关键字调用函数 `fn`，启动了一个新的线程 goroutine。

# 附录 2

# 测试

请选择正确的答案。

### (01)

```go
package main
import "fmt" // 导入内置函数
func main() {
    fmt.Println("Hello, World! ")
}
```

A. `iostream`

B. `math`

C. `i/o`

D. `fmt`

### (02)

```go
fill in a int // 声明一个变量 
a = 100
```

A. `variable`

B. `variab`

C. `var`

D. `va`

### (03)

```go
package main
func main() {
    const (
        x = fill in // 一个特殊的常量
        y = fill in
        z = fill in
    )
    print(x, y, z)
}
```

输出：0 1 2

A. `const`

B. `iota`

C. `constant`

D. `iote`

### (04)

```go
package main
func main() {
    var number int=20 
    fill in (number) { // number 比较每一个
        case 10: println("Running case 10")
        case 20: println("Running case 20")
        case 30: println("Running case 30")
        default: println("Running default")
    }
}
```

A. `If`

B. `While`

C. `Do`

D. `Switch`

### (05)

```go
package main
func main() {
    var num int = 10
    if num > 10 {
        fill in code1 // 执行指定的代码
        print("num > 10")
    }
    if num == 10 {
        fill in code2 // 执行指定的代码
        print("num == 10")
    }
}
```

A. `goto`

B. `go`

C. `to`

D. `return`

### (06)

```go
package main
func main(){
    var arr []int = fill in ([]int, 3) // 定义一个数组 
    arr[0]=100 // 给数组赋值 
    arr[1]=101
    arr[2]=102
    print(arr[0], " ", arr[1], " ", arr[2])
}
```

A. `array`

B. `define`

C. `make`

### (07)

```go
package main
import "fmt"
type fill in { // 定义一个结构体
    color string // 结构成员
    size string
    number int
}
func main() {
    fmt.Println(Flower{color:"Red", size:"Large", number:10})
}
```

A. `structure`

B. `struct`

C. `string`

D. `type`

### (08)



### (08)

```go
package main
import "fmt"
func fn(s string) { // 定义一个函数 
    for i := 0; i < 5; i++ {
        fmt.Println(s)
    }
}
func main() {
    fn("Thread B") // 调用函数 
    fill in func(msg string) { // 定义一个 goroutine 函数
        fmt.Println(msg)
    } ("Press Enter to Stop!") // 执行 goroutine 函数 
    fmt.Scanln() // 接收键盘输入
    fmt.Println("Complete!")
}
```

A. `goto`

B. `go`

C. `to`

D. `goroutine`

### (09)

```go
package main
func main(){
    var a = "C in 8 Hours"
    var b string = "is"
    c ="a good book!" 
    var e fill in = true
    println(a, b, c, e)
}
```

A. `string`

B. `boolean`

C. `bool`

D. `char`

### (10)

已知：

`a = 100`

`b = 2`

计算过程：

`a + b` 返回 102

`a – b` 返回 98

`a * b` 返回 200

`a / b` 返回 50

`a % b` 返回 fill in

A. `0`

B. `1`

C. `2`

D. `3`

### (11)

```go
package main
import "fmt"
func main() {
    c1:=make(chan int,1024) // 创建一个通道
    c2:=make(chan int,1024)
    c3:=make(chan int,1024)
    c1 <- 100 // 向通道发送数据
    c2 <- 200
    c3 <- 300
    fill in { // 随机执行一个 case
        case <- c1: // 从通道接收数据
            fmt.Println("Receive data from c1")
        case <- c2: fmt.Println("Receive data from c2")
        case <- c3: fmt.Println("receive data from c3")
        default: fmt.Println("Not receive data yet")
    }
}
```

A. `switch`

B. `select`

C. `while`

D. `if`

### (12)

```go
package main
import "fmt"
fill in swap(a, b string) (string, string) { // 定义一个函数 
    return b, a // 返回两个值给调用者
}
func main() {
    x, y = swap("in 8 Hours", "JavaScript") //调用函数
    fmt.Println(x, y)
}
```

A. `function`

B. `def`

C. `void`

D. `func`

### (13)

```go
package main
import "fmt"
func main() {
    var num int110
        var *int // 声明一个指针
    pt = fill in // 获取地址并赋值给 pt
    fmt.Printf("address of num: %x\n", pt)
    fmt.Printf("address of pt: %x\n", pt)
    fmt.Printf("value of:: %dn",",)
}
```

A. `*num`

B. `$num`

C. `&num`

D. `#num`

### (14)

```go
package main
import "fmt"
func main() {
    s := fill in 1,2,3,4,5 // 创建切片
    fmt.Println(s)
}
```

A. `[]`

B. `]`

C. `]`

D. `]`

### (15)

```go
package main
import "fmt"
func main(){
    c = make(chan int) // 创建通道
    go func() { // 定义 goroutine 函数
        c <- 1 // 向通道发送数据
        c <- 2
        c <- 3
        close(c) // 关闭通道
    }() // 执行 goroutine 函数
    for v := fill in c // 遍历通道
        fmt.Println("Send data to channel: ",v)
    }
}
```

A. `range`

B. `chan`

C. `in`

D. `for`

### (16)

```go
package main
import "fmt"
func main(){
    var a = "C in 8 Hours"
    var b string = "is"
    c = "a good book!"
    var e bool = true
    println(a, b, c, e)
}
```

A. `=`

B. `<=`

C. `=`

D. `<=`

### (17)

```go
package main
import "fmt"
func main() {
    var num int110
    var pt *int // 声明一个指针
    pt = fill in // 获取地址并赋值给 pt
    fmt.Printf("address of num: %x\n", &num)
    fmt.Printf("address of pt: %x\n", pt)
    fmt.Printf("value of pt: %d\n", *pt)
}
```

A. `*num`

B. `$num`

C. `&num`

D. `#num`

### (18)

```go
package main
import "fmt"
func main() {
    var num int110
    fill in = 5
    for { // 循环语句
        fmt.Println()
    }
}
```

A. `while`

B. `if`

C. `do`

D. `for`

### (19)

```go
package main
import "fmt"
func swap(a, b string) (string, string) { // 定义一个函数
    return b, a // 返回两个值给调用者
}
func main() {
    x, y = swap("in 8 Hours", "JavaScript") //调用函数
    fmt.Println(x, y)
}
```

A. `pass`

B. `return`

C. `send`

D. `goto`

### (20)

```go
package main
import "fmt"
func main() {
    var npt *int
    fmt.Printf( )
}
```

输出是什么？

A. `0`

B. `1`

C. `2`

D. `3`

### (21)

```go
package main
import "fmt"
func main() {
    var s = [9]int{0, 1, 2, 3, 4, 5, 6, 7, 8}
    mySlice:= s in // 获取四个值
    fmt.Println(mySlice)
}
```

输出: 2 3 4 5

A. `2: 6`

B. `1: 5`

C. `2`

D. `3`

### (22)

```go
package main
import "fmt"
func main(){
    var arr []int = fill in ([]int,3) // 定义一个数组
    arr[0]=100 // 给数组赋值
    arr[1]=101
    arr[2]=102
    fmt.Println(arr[0], " ", arr[1], " ", arr[2])
}
```

A. `array`

B. `define`

C. `make`

D. `type`

### (23)

```go
package main
import "fmt"
type fill in { // 定义一个结构体
    color string // 结构成员
    size string
    number int
}
func main() {
    fmt.Println(Flower{color:"Red", size:"Large", number:10})
}
```

A. `structure`

B. `struct`

C. `string`

D. `type`

### (24)

```go
package main
import ( "fmt" "time" )
func main(){
    c = make(chan int)
    go func() { // 定义一个 goroutine 函数
        c <- 1 // 向通道发送数据
        c <- 2
        c <- 3
        close(c) // 关闭通道
    }() // 执行 goroutine 函数
    for v := fill in c // 遍历通道
        fmt.Println("Send data to channel: ",v)
    }
}
```

# 推荐书籍

- [8 小时精通 C++ 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 `JAVA` 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 `AngularJS` 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [C# 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 C# 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [C# 编程：包含 100 个问答](https://www.amazon.com/-/e/B0863BQT8T)
- [C++ 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 C++ 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [编程面试，1000 问答](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 Django 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 Go 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [HTML CSS 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 HTML CSS 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [`JAVA` 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 `JAVA` 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [`JAVA` 编程：包含 100 个问答](https://www.amazon.com/-/e/B0863BQT8T)
- [JavaScript 50 个实用用程序](https://www.amazon.com/-/e/B0863BQT8T)
- [JavaScript 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 JavaScript 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [`JQuery` 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 `JQuery` 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 Kotlin 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [Linux 命令行](https://www.amazon.com/-/e/B0863BQT8T)
- [Linux 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 Linux Shell 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 MySQL 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [Node](https://www.amazon.com/-/e/B0863BQT8T)
- [.](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 js 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [PHP 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 PHP MySQL 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 PowerShell 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [Python 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 Python 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [Python 编程：包含 100 个问答](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 R 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 Ruby 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 Rust 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [8 小时精通 Scala 编程](https://www.amazon.com/-/e/B0863BQT8T)
- [Visual Basic 面试与认证考试](https://www.amazon.com/-/e/B0863BQT8T)
- [初学者 Visual Basic 编程](https://www.amazon.com/-/e/B0863BQT8T)
