

![mac2](Images/mac2.png)

在 Windows 平台上运行程序的输出。

![go_win](Images/go_win.png)

## 1.2 开发工具

基本上，你可以使用任何文本编辑器来编写 Go 代码。以下是文本编辑器的列表：

*   `vim`
*   `nano`
*   Intellij IDEA, [https://www.jetbrains.com/idea/](https://www.jetbrains.com/idea/)
*   Sublime text, [http://www.sublimetext.com/](http://www.sublimetext.com/)

下面图示中展示了 Intellij IDEA 的示例截图。

![ch1-1](Images/ch1-1.png)

## 1.3 Hello World

如何开始使用 Go？嗯，很容易。首先，创建一个名为 `hello` 的文件夹。

```
$ mkdir hello
$ cd hello
```

然后，在 `hello` 文件夹上创建一个名为 `main.go` 的文件。为 `main.go` 文件编写此代码。

```
package main

import "fmt"

func main() {
    fmt.Println("Hello, go!")
}
```

保存此文件。然后，返回到你的终端。你可以构建并运行它。

```
$ go build
$ go run main.go
```

在这种情况下，它将根据你的平台生成一个可执行文件。

下面图示中可以看到一个示例程序输出。

![ch1-4](Images/ch1-4.png)

## 1.4 Go 包

有很多你可以使用的 Go 包。Go 包的列表可以在此链接上看到 [https://golang.org/pkg/](https://golang.org/pkg/)。在本书中，我们将探索一些 Go 标准包。我们也尝试构建自己的 Go 包。

# 2. Go 编程语言

本章解释了 Go 编程语言的基础。

## 2.1 常见规则

Go 语言以“C 家族”作为主要语言，但我们在语法末尾不写“;”。以下是语法规则：

```
syntax_code1
syntax_code2
syntax_code3
```

## 2.2 变量

在本节中，我们探讨如何在 Go 中定义变量并为其赋值。

### 2.2.1 声明变量

要声明一个名为 `myvar` 的变量且数据类型为 `data_type1`，你可以编写以下脚本：

```
var myvar data_type1
```

以下是声明一些变量的示例脚本。

```
var str string
var n, m int
var mn float32
```

我们也可以按如下方式定义多个变量。

```
var (
    name string
    email string
    age int
)
```

一旦声明，这些变量就可以用来存储任何类型的数据。

### 2.2.2 为变量赋值

你已经声明的变量可以通过等号 `=` 来赋值。例如，将变量 `str` 赋值为字符串值 `"Hello World"`，你会这样写：

```
str = "Hello World"
n = 10
m = 50
mn = 2.45
```

我们也可以声明一个变量并为其赋值。

```
var city string = "London"
var x int = 100
```

另一种选择，我们可以使用 `:=` 语法声明一个变量而不定义数据类型，并为其赋值。

```
country := "DE"
val := 15
```

### 2.2.3 演示

为了说明在 Go 中声明变量，创建一个名为 `vardemo` 的文件夹。然后，创建一个名为 `main.go` 的文件。

为 `main.go` 编写以下脚本。

```
package main

import "fmt"

func main() {
    // declare variables
    var str string
    var n, m int
    var mn float32

    // assign values
    str = "Hello World"
    n = 10
    m = 50
    mn = 2.45

    fmt.Println("value of str= ",str)
    fmt.Println("value of n= ",n)
    fmt.Println("value of m= ",m)
    fmt.Println("value of mn= ",mn)

    // declare and assign values to variables
    var city string = "London"
    var x int = 100

    fmt.Println("value of city= ",city)
    fmt.Println("value of x= ",x)

    // declare variable with defining its type
    country := "DE"
    val := 15
    fmt.Println("value of country= ",country)
    fmt.Println("value of val= ",val)

    // define multiple variables
    var (
        name string
        email string
        age int
    )
    name = "john"
    email = "john@email.com"
    age = 27

    fmt.Println(name)
    fmt.Println(email)
    fmt.Println(age)
}
```

保存此文件。

然后，尝试构建并运行它。

```
$ cd vardemo
$ go build
$ go run main.go
```

下面图示中可以看到一个示例输出。

![ch2-1](Images/ch2-1.png)

## 2.3 注释

你可以用编写注释来解释代码的工作方式。要做到这一点，你可以使用 `//` 和 `/* */` 语法。以下是示例代码：

```
// declare variables
var str string
var n, m int
var mn float32

// assign values
str = "Hello World"
n = 10
m = 50
mn = 2.45

/* print the result */
fmt.Println("value of str= ",str)
```

## 2.4 算术运算

Go 支持相同的四种基本算术运算，如加法、减法、乘法和除法。为了测试，创建一个文件夹 `arithdemo`。然后，创建一个名为 `main.go` 的文件。

以下是 `main.go` 中基本算术的说明代码：

```
package main

import "fmt"

func main() {
    // declare variables
    var a, b int

    // assign values
    a = 5
    b = 10

    // arithmetic operation
    // addition
    c := a + b
    fmt.Printf("%d + %d = %d \n",a,b,c)
    // subtraction
    d := a - b
    fmt.Printf("%d - %d = %d \n",a,b,d)
    // division
    e := float32(a) / float32(b)
    fmt.Printf("%d / %d = %.2f \n",a,b,e)
    // multiplication
    f := a * b
    fmt.Printf("%d * %d = %d \n",a,b,f)
}
```

然后，尝试构建并运行它。

```
$ cd arithdemo
$ go build
$ go run main.go
```

以下是示例输出。

![ch2-2](Images/ch2-2.png)

## 2.5 数学函数

Go 提供了 `math` 库，你可以在 [https://golang.org/pkg/math/](https://golang.org/pkg/math/) 上阅读它。为了说明，我们尝试使用几个数学函数。

创建一个名为 `mathdemo` 的文件夹。然后，创建一个名为 `main.go` 的文件。编写以下代码。

```
package main

import (
    "fmt"
    "math"
)

func main(){
    a := 2.4
    b := 1.6

    c := math.Pow(a,2)
    fmt.Printf("%.2f^%d = %.2f \n",a,2,c)

    c = math.Sin(a)
    fmt.Printf("Sin(%.2f) = %.2f \n",a,c)

    c = math.Cos(b)
    fmt.Printf("Cos(%.2f) = %.2f \n",b,c)

    c = math.Sqrt(a*b)
    fmt.Printf("Sqrt(%.2f*%.2f) = %.2f \n",a,b,c)
}
```

然后，尝试构建并运行它。

```
$ cd mathdemo
$ go build
$ go run main.go
```

以下是示例输出。

![ch2-3](Images/ch2-3.png)

## 2.6 自增和自减

Go 有用于自增和自减的特殊语法。

*   `++` 语法用于自增。`a++` 表示 `a = a + 1`
*   `--` 语法用于自减。`a--` 表示 `a = a - 1`

为了测试，创建一个名为 `incdec` 的文件夹，然后创建一个名为 `main.go` 的文件。编写以下脚本。

```
package main

import "fmt"

func main() {
    // declare variables
    var a = 4

    // increment
    fmt.Printf("a = %d \n",a)
    a = a + 1
    fmt.Printf("a + 1 = %d \n",a)
    a++
    fmt.Printf("a++ = %d \n",a)

    // decrement
    a = a - 1
    fmt.Printf("a - 1 = %d \n",a)
    a--
    fmt.Printf("a-- = %d \n",a)
}
```

然后，尝试构建并运行它。

```
$ cd incdec
$ go build
$ go run main.go
```

以下是示例输出。

![ch2-4](Images/ch2-4.png)

## 2.7 从键盘获取输入

在 `fmt` 库中，它提供了一个从键盘获取输入的功能。我们可以使用 `Scanf()`。

为了说明，我们计算圆的面积。在这种情况下，我们需要一个半径值的输入。

创建一个名为 `inputdemo` 的文件夹。然后，创建一个名为 `main.go` 的文件，并编写此脚本。

```
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println("Circle Area calculation")
    fmt.Print("Enter a radius value: ")
    var radius float64
    fmt.Scanf("%f", &radius)

    area := math.Pi * math.Pow(radius,2)
    fmt.Printf("Circle area with radius %.2f = %.2f \n",radius, area)
}
```

然后，尝试构建并运行它。

```
$ cd inputdemo
$ go build
$ go run main.go
```

输入一个圆的半径。

以下是示例输出。

![ch2-5](Images/ch2-5.png)

## 2.8 比较运算符

你可能需要确定变量或值之间的相等性或差异。以下是比较运算符的列表：

