
在 Go 语言中，有两种独特的方式创建和引入 `map`：

## 1. 简单方法

在这种技术中，你可以不使用 `make()` 函数来创建和实例化 `map`：

### 创建 Map

你可以使用以下语法创建 `map`：

1. `//一个空 map`
2. `map[Key_Type]Value_Type{}`
3. `//带有键值对的 map`
4. `map[Key_Type]Value_Type{key1: value1, ..., keyN: valueN}`

示例：`var mymap map[int]string`

在 `map` 中，`map` 的零值是 `nil`，且 `nil` map 不包含任何键。如果你尝试在 `nil` map 中包含键值对，编译器将抛出运行时错误。

### 使用 map 字面量引入 map

`map` 字面量是实例化一个包含信息的 `map` 最简单的方法，使用冒号分隔键值对，且最后一个末尾的冒号至关重要，如果不使用它，编译器将报错。

示例：

```go
package main

import "fmt"

func main() {
    // 创建并初始化空 map
    // 使用 var 关键字
    var m1 map[int]int
    // 检查 map 是否为 nil
    if m1 == nil {
        fmt.Println("True")
    } else {
        fmt.Println("False")
    }
    m2 := map[int]string{
        90: "Ali",
        91: "Usama",
        92: "Usman",
        93: "Shahid",
        94: "Aslam",
    }
    fmt.Println("Map number 2: ", m2)
}
```

输出：

```
True
Map-2:  map[90:Ali 91:Usama 92:Usman 93:Shahid 94:Aslam]
```

## 2. 使用 make 函数

你同样可以使用 `make()` 函数创建 `map`。这种能力是一个内置功能，在这种策略中，你只需要传递 `map` 的类型，它就会返回一个初始化的 `map`。

语法：`make(map[Key_Type]Value_Type, initial_Capacity)`

`make(map[Key_Type]Value_Type)`

示例：

```go
package main

import "fmt"

func main() {
    var MP = make(map[float64]string)
    fmt.Println(MP)
    MP[1.3] = "Usama"
    MP[1.5] = "Maria"
    fmt.Println(MP)
}
```

输出：

```
map[]
map[1.3:Usama 1.5:Maria]
```

# 重要要点

## 1. 如何遍历 map？

你可以使用 `range` 循环来遍历 `map`。这个循环的顺序可能会改变，因为 `map` 是无序集合。

示例：

```go
package main

import "fmt"

// 主函数
func main() {
    // 创建并初始化一个 map
    newmap := map[int]string{
        90: "Fatima",
        91: "Sohail",
        92: "Maryam",
        93: "Sahar",
        94: "Sara",
    }
    // 使用 for range 遍历 map
    for idea, pre := range newmap {
        fmt.Println(idea, pre)
    }
}
```

输出：

```
90 Fatima
91 Sohail
92 Maryam
93 Sahar
94 Sara
```

## 2. 如何在 map 中包含键值匹配？

在 `map` 中，你允许使用给定的语法在实例化的 `map` 中包含键值组合：`map_name[key]=value`

在 `map` 中，如果你尝试包含一个已存在的键，它将用新值覆盖或更新该键的值。

# Struct（结构体）

`Struct` 或结构体可以与面向对象编程中的类（class）概念相比。如果你完全不知道什么是 OOP，那么可以将 `struct` 看作一个声明字段及其属性的公式。一个结构体有多个相同或不同类型的字段。当你需要描述一个由多个单独字段（属性）组成的类型时，通常会使用 `struct`。例如 Ross 是一种员工（`struct`），它有 `firstName`、`LastName`、`pay` 和 `fullTime` 状态（组合字段）。

### 声明 struct 类型

`struct` 类型仅是一个包含结构体将持有数据的轮的构造。为了简单起见，我们必须使用假设名称以便我们可以引用 `struct` 类型。创建 `struct` 的语法是：

```go
type StructName struct{
    field1 fieldType1
    field2 fieldType2
}
```

在上述语法中，`StructName` 是 `struct` 类型，而 `field1` 和 `field2` 是 `fieldType1` 和 `fieldType2` 的字段。

如果我们创建一个像检查的 `Employee` 类型，带有某些字段呢？

```go
type Employee struct {
    firstName string
    lastName string
    salary int
    fullTime bool
}
```

你也可以在同一行中组合不同的字段，正如我们在练习中发现的那样。所以我们可以编写上面的程序：

```go
type Employee struct {
    firstName, lastName string
    salary int
    fullTime bool
}
```

### 创建 struct

由于我们创建了 `Employee` 类型，我们应该从它创建一个 `struct`。由于 `Employee` 是一个类型，创建该类型的变量是简单的。

```go
package main
import "fmt"

type Employee struct {
    FN, LN string
    sal    int
    FT    bool
}

func main(){
    var ro Employee
    fmt.Println(ro)
}
```

上述程序的输出看起来很奇怪，但它给了 `struct` 的零值，因为我们定义了 `Employee` 类型的变量但还没有实例化它。

### 匿名结构体（Anonymous struct）

匿名 `struct` 是没有明确定义的 `struct` 类型别名的 `struct`。到目前为止，我们创建了 `Employee` struct 类型名称以便 Ross 可以推断。但如果出现匿名 `struct` 的情况，我们不定义任何 `struct` 类型别名，直接从内联 `struct` 类型创建 `struct`。

```go
package main
import "fmt"

func main(){
    monica:= struct {
        FN, LN string
        sal    int
        FT    bool
    } { FN: "Obama", LN: "Barak", sal: 20000, }
    fmt.Println(monica)
}
```

# 模板（Templates）

两个包正在使用模板操作。

* `text/template`
* `html/template`

两者提供了类似的接口；在任何情况下，`html/template` 包被用于创建防止代码注入的 HTML 输出。`text/template` 包旨在接收消息作为信息，并根据对文章第一个内容的更改产生多样化的内容。布局的输入文本是任何组织评估或控制结构中的 UTF-8 编码消息——它们由 `{{` 和 `}}` 分隔；所有之外的内容都将原样复制到输出。除了原始字符串外，操作（activities）不能包含换行符，但注释可以。目前，`Template` 中的“操作”是什么？让我们来探究一下。`Template` 中的操作以字符串或“原始字符串”的形式赋予了相应的能力。操作对应数据评估、属性或循环。它们由 `{{}}` 分隔。其他非部分。数据评估（Data evaluations）——当使用模板时，你将把它们绑定到某些数据结构（例如 `struct`），并从中获取信息。我们可以通过 `{{FieldName}}` 从结构体中获取信息，它将在解析时将其替换为给定结构体的 `FieldName` 属性，该结构体被传递给 `Execute`。此外还有一个 `{{.}}` 操作，你可以用来引用非结构体类型的属性。

在 Golang 中解析模板有三个最重要且最常用的功能：

1. `New`: 它允许创建新的、模糊的格式，
2. `Parse`: 它解析给定的布局字符串并返回解析后的格式，
3. `Execute`: 它将解析后的布局应用于数据结构并将结果写入给定的作者。

现在，我们来看 `text/template` 程序的完整代码。

```go
package main

import (
	"os"
	"text/template"
)

type Netflix struct {
	Show string
	Lead string
}

func main() {
	netfl := Netflix{"Ali Salary", "very good"}
	t, error := template.New("netfl").Parse("Description {{.Show}} has: {{.Lead}}")
	if error != nil {
		panic(error)
	}
	error = t.Execute(os.Stdout, netfl)
	if error != nil {
		panic(error)
	}
}
```

输出 ➜

```
hello
go run hello.go
Ali Salary has: "very good."
```

正如输出所示，布局提供了一种修改文本输出的极佳方法。`text/template` Go 的 `html/template` 包为 HTML 格式提供了丰富的模板语言。它大部分用于 Web 应用程序，以组织化的方式在客户端程序中显示信息。Go 模板语言的一个巨大优势是信息的程序化获取。无需担心 XSS 攻击，因为 Go 在解析 HTML 布局并在将其显示给程序之前会对所有输入进行转义。在 Go 中编写模板非常简单。在渲染格式时，输入的信息可以是任何 Go 数据结构。它可能是一个简单的字符串或数字，甚至可以是固定的数据结构。我们可以以某种格式获取信息，而根变量通过 `.}}` 获取。大括号内的标签被称为管道（pipeline）以及根组件。

```go
package main

import (
	"html/template"
	"os"
)

type Mandalorian struct {
	Name string
}

func main() {
	toss := template.New("fieldname example")
	toss, _ = toss.Parse("Hey {{.Name}}!")
	mo := Mandalorian{Name: "John Wick"}
	toss.Execute(os.Stdout, mo)
}
```

输出 ➜

```
hello
go run hello.go
Hey John Wick!
```

`html/template` 包执行数据驱动的布局，以创建防止代码注入的 HTML 输出。它提供了与 `text/template` 包类似的接口，一旦输出是 HTML，就应该使用它而不是 `text/template`。

Golang 中 `html/template` 的用例参见下面的代码。

```go
package main

import (
	"html/template"
	"log"
	"os"
)

func main() {
	const tupple = `
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>{{.Title}}</title>
</head>
<body>
	{{range .Items}}
		<div>{{ . }}</div>
	{{else}}
		<div><strong>no rows</strong></div>
	{{end}}
</body>
</html>`
	check := func(erro error) {
		if erro != nil {
			log.Fatal(erro)
		}
	}
	t, erro := template.New("WEB").Parse(tupple)
	check(erro)
	dataIT := struct {
		Title string
		Items []string
	}{
		Title: "Disney plus Programs",
		Items: []string{
			"The Mandalorian",
			"Avengers Endgame",
		},
	}
	erro = t.Execute(os.Stdout, dataIT)
	check(erro)

	noItems := struct {
		Title string
		Items []string
	}{
		Title: "Upcoming Programs",
		Items: []string{},
	}
	erro = t.Execute(os.Stdout, noItems)
	check(erro)
}
```

输出 ➜

```
hello
go run hello.go
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Disney plus Programs</title>
</head>
<body>
	<div>The Mandalorian</div>
	<div>Avengers Endgame</div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Upcoming Programs</title>
</head>
<body>
	<div><strong>no rows</strong></div>
</body>
</html>
```

# 示例

随附源代码显示了一个名为 `max()` 的函数。该函数接受两个参数 `num1` 和 `num2` 并返回两者之间的最大值。

```go
func max(no1, no2 int) int {
    res int
    if (no1 > no2) {
        res = no1
    } else {
        res = no2
    }
    return res 
}
```

## 调用函数

在编写 Go 程序时，你赋予了函数需要执行的含义。要使用一个函数，你应该调用该函数来执行特定的赋值。当程序调用一个函数时，程序的控制权会转移到被调用的函数。被调用的函数执行特定的赋值，当它的返回语句执行或函数完成执行支持时，它会将程序控制权返回主程序。要调用一个函数，本质上需要连它的函数名传递必要的参数。如果函数返回一个值，此时你可以存储这个返回的值。

例如：

```go
package main
import "fmt"
func main() {
    var ant int = 100
    var boss int = 200
    var retur int
    retur = max(ant, boss)
    fmt.Printf( "Total : %d\n", retur ) 
}
func max(no1, no2 int) int {
    var re int
    if (no1 > no2) {
        re = no1
    } else {
        re = no2
    }
    return re 
}
```

我们将 `max()` 函数与 `principle()` 函数放在一起并汇总了源代码。在运行最后一个可执行文件时，它将交付以下结果：

```
Total: 200
```

## 函数返回多个值

Go 函数可以返回多个值。例如：

```go
package main
import "fmt"
func swap(x, y string) (string, string) {
    return y, x
}
func main() {
    ant, boy := swap("Barak", "Obama")
    fmt.Println(ant, boy )
}
```

当上述代码被编译并执行时，它会产生以下结果：

```
Obama Barak
```

## 函数参数

如果一个函数要使用参数，它必须声明能够接收参数估值的因素。这些因素被称为函数的形式参数。正确的参数的作用类似于函数内部的其他局部因素，并在进入函数时创建，在退出时销毁。

在调用函数时，有两种不同的方式可以将参数传递给函数：

1. **值传递 (Call by value)**：这种技术将参数的真实值复制到函数的形式参数中。在这种情况下，函数内部对参数的修改对参数没有影响。
