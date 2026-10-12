
# 指针演示

## 指针基础

```go
/*Pointers Demo 1*/
/*Package Declaration*/
package main

/*Import Statement - import fmt package*/
import (
	"fmt"
)

/*Mandatory main function*/
func main() {
	/*Declare and initialize a string*/
	var name string = "Shaun"

	/*Declare a string pointer*/
	var name_ptr *string

	/*Assign the address of name to name_ptr*/
	name_ptr = &name

	/*Short declare and initialize int variable*/
	age := 19

	/*Short declare and initialize integer pointer*/
	aptr := &age

	/*Declare and initialize float variables*/
	var height, weight float32 = 182.36534, 165.75124

	/*Declare and initialize pointer variables*/
	var hptr, wptr *float32 = &height, &weight

	/*Print everything*/
	fmt.Printf("\nname = %s\nname_ptr (address of name var) = %v\n", name, name_ptr)
	fmt.Printf("\nage = %d\natpr (address of age var) = %v\n", age, aptr)
	fmt.Printf("\nheight = %f\nhtpr (address of height var) = %v\n", height, hptr)
	fmt.Printf("\nweight = %f\nwtpr (address of weight var) = %v\n", weight, wptr)
}
```

输出：

![](img/Image00079.jpg)

在该程序中，我们仅显示了变量的内容及其内存地址。此时你可能还无法理解其意义。你可能会问——变量的内存地址有什么用？我们马上就会讲到。我们可以**解引用**指针，以直接访问指针指向的内存地址处存储的值。为了解引用指针，必须在指针变量前加上 `*` 符号。以下代码片段解释了这一概念：

```go
var x int = 90
var ptr *int = &x
/*Dereference ptr to access the value of x and assign it to y*/
y := *ptr
```

该片段的工作原理如下图所示：

![](img/Image00080.jpg)

存在一个整型变量 `x`，初始化为 `90`。假设该变量存储在内存地址 `0x00a3h` 处。声明一个整型指针变量 `ptr`，并使用语句 `var ptr *int = &x` 将 `x` 的地址赋值给它。现在 `ptr` 持有 `0x00a3h`。接着，我们解引用 `ptr` 以访问内存地址 `0x00a3h` 处的值（`90`）并将其复制给另一个变量 `y`（假设 `y` 在地址 `0x01b6h`，但这在本例中无关紧要）。解引用和复制通过语句 `y := *ptr` 完成。在本例中，我们在不接触源变量的情况下，成功将一个变量的内容复制到了另一个变量。

让我们通过一个 Go 程序来理解这一概念：

```go
/*Pointers Demo 2*/
/*Package Declaration*/
package main

/*Import Statement - import fmt package*/
import (
	"fmt"
)

/*Mandatory main function*/
func main() {
	/*Declare and initialize a string*/
	var name string = "Anabelle"

	/*Declare a string pointer*/
	var name_ptr *string

	/*Assign the address of name to name_ptr*/
	name_ptr = &name

	/*Short declare and initialize int variable*/
	age := 33

	/*Short declare and initialize integer pointer*/
	aptr := &age

	/*Print everything*/
	fmt.Printf("\nname = %s\nname_ptr = %v\n*name_ptr = %s\n", name, name_ptr, *name_ptr)
	fmt.Printf("\nage = %d\natpr = %v\n*aptr = %d\n", age, aptr, *aptr)

	/*Modify values of name and age without touching name and age*/
	*name_ptr = "Diorah"
	*aptr = 21

	fmt.Printf("\nname = %s\nname_ptr = %v\n*name_ptr = %s\n", name, name_ptr, *name_ptr)
	fmt.Printf("\nage = %d\natpr = %v\n*aptr = %d\n", age, aptr, *aptr)
}
```

输出：

![](img/Image00081.jpg)

如上所示，有两个变量 `name` 和 `age` 持有任意初始值。我们通过解引用指向这些变量的指针（`name_ptr` 和 `aptr`）来修改这些变量的内容。

如果你已经很好地理解了变量和指针的概念，你可能会想——指针只是另一个变量，它也有自己的地址。是的，指针变量有自己的地址。你可以拥有一个指向另一个指针变量的指针。为此，指向另一个指针的指针必须声明为 `**<data type>`。请看以下代码片段：

```go
var x int = 1050
var x_ptr *int = &x
var x_ptr_ptr **int = &xptr
**x_ptr_ptr = 7000
fmt.Println(x)
```

存在一个整型变量 `x`，持有值 `1050`。指针变量 `x_ptr` 用于持有 `x` 的地址，另一个指针变量 `x_ptr_ptr` 用于持有 `x_ptr` 的值。对 `x_ptr_ptr` 进行单次解引用（`*x_ptr_ptr`）将得到 `x_ptr` 的值，即 `x` 的地址。对 `x_ptr_ptr` 进行双重解引用（`**x_ptr_ptr`）将得到 `x` 的值。语句 `**x_ptr_ptr = 7000` 将把 `x` 的值改为 `7000`。

> **注意**：指针是一个高级主题，在数据结构、系统级编程、嵌入式系统等领域被大量使用。如果本章让你感到困惑，这很正常。你可以毫无问题地继续阅读本书的其余部分。作为初学者，你只需要知道什么是指针以及它有什么作用。

# 结构体

结构体是一种用户定义的数据类型，用于存储元素的集合。与数组不同，元素可以是任意数据类型。结构体元素也称为字段。

使用以下语法来定义结构体：

```
type <结构体名称> struct {
    <字段 1> <字段 1 的数据类型>
    <字段 2> <字段 2 的数据类型>
    <字段 3> <字段 3 的数据类型>
    ...
    <字段 n> <字段 n 的数据类型>
}
```

让我们定义一个结构体来存储学生的详细信息，例如 `student_id`、`first_name`、`last_name`、`age`、`gpa`：

```
type student struct {
    student_id int
    first_name string
    last_name string
    gpa float32
}
```

结构体定义仅仅是用户定义数据类型的蓝图。它本身不包含数据。为了使用结构体定义，应创建该结构体类型的变量，并设置其字段。

以下是创建结构体变量的方法：

```
var <结构体变量> <结构体名称>
```

示例：

```
var s1 student
var x, y, student
```

结构体变量的字段可以按如下方式设置：

```
<结构体变量>.<字段> = <值>
```

示例：

```
var s student
s.student_id = 100014
s.first_name = "Grant"
s.last_name = "Dewan"
s.age = 16
```

下面是一个定义结构体、创建结构体变量、设置其字段并在控制台打印它们的示例：

```go
/* 结构体演示 1 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 定义一个结构体 */
/* 设置 3 个字段 */
type student struct {
    s_id int
    f_name string
    l_name string
    grade int
    age int
    gpa float32
}

/* 强制性的 main 函数 */
func main() {
    /* 声明一个类型为 student 的结构体变量 S */
    var S student

    /* 设置 S 的字段 */
    S.s_id = 30657095
    S.f_name = "Sophia"
    S.l_name = "Johnson"
    S.grade = 12
    S.age = 18
    S.gpa = 8.97

    /* 打印 S 的详细信息 */
    fmt.Printf("\nStudent - S\n")
    fmt.Printf("\nS.s_id = %d", S.s_id)
    fmt.Printf("\nS.f_name = %s", S.f_name)
    fmt.Printf("\nS.l_name = %s", S.l_name)
    fmt.Printf("\nS.grade = %d", S.grade)
    fmt.Printf("\nS.age = %d", S.age)
    /* 打印 gpa，限制为 2 位小数 */
    fmt.Printf("\nS.gpa = %.2f\n", S.gpa)
}
```

输出：

![](img/Image00082.jpg)

结构体变量也可以使用以下语法进行初始化：

```
var <结构体变量> <结构体名称> = <结构体名称>{<字段 1>:<值 1>, ..., <字段 n>:<值 n>}
```

示例：

```
var s1 student = student{student_id: 231, first_name: "Rajat", last_name: "Singh", age: 20}
```

也可以使用以下语法短声明结构体变量：

```
<结构体变量> := <结构体名称>{<字段 1>:<值 1>, ..., <字段 n>:<值 n>}
```

示例：

```
s2 := student{student_id: 592, first_name: "Jorge", last_name: "Fernandez", age: 17}
```

下面是一个展示所有字段设置方法的程序：

```go
/* 结构体演示 2 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
    "fmt"
)

/* 定义一个结构体 */
/* 设置 3 个字段 */
type person struct {
    name string
    address string
    age int
}

/* 强制性的 main 函数 */
func main() {
    /* 声明一个结构体变量 p1 */
    var p1 person

    /* 设置 p1 的字段 */
    p1.name = "Earl"
    p1.address = "NJ"
    p1.age = 25

    /* 声明并初始化一个结构体变量 p2 */
    var p2 person = person{name: "Manjunath", address: "New Delhi", age: 30}

    /* 短声明并初始化结构体变量 p3 */
    p3 := person{name: "Bella", address: "London", age: 19}

    fmt.Printf("\nperson p1\n")
    fmt.Printf("\np1.name = %s\np1.address = %s\np1.age = %d\n", p1.name, p1.address, p1.age)
    fmt.Printf("\nperson p2\n")
    fmt.Printf("\np2.name = %s\np2.address = %s\np2.age = %d\n", p2.name, p2.address, p2.age)
    fmt.Printf("\nperson p3\n")
    fmt.Printf("\np3.name = %s\np3.address = %s\np3.age = %d\n", p3.name, p3.address, p3.age)
}
```

输出：

# 17. 编程示例

既然我们已经学习了 Go 编程的基础知识，现在让我们将这些概念付诸实践，尝试一些编程示例。

## 17.1 数字各位之和

下面是一个程序，它从用户处读取一个整数并计算其各位数字之和：

```go
/*各位数字之和*/
/*包声明*/
package main

/*导入语句 - 导入 fmt 包*/
import (
	"fmt"
)

/*强制性的 main 函数*/
func main() {
	var number int
	var sum int = 0
	fmt.Printf("\n 请输入一个数字: ")
	fmt.Scanf("%d", &number)
	for number > 0 {
		/*将个位数字加到 sum 上*/
		sum = sum + (number % 10)
		/*丢弃个位数字*/
		number = number / 10
	}
	fmt.Printf("\n 所有数字之和: %d\n", sum)
}
```

**输出：**

![](img/Image00084.jpg)

## 17.2 斐波那契数列

斐波那契数列以 0 和 1 作为前两项开始。下一项通过将前两项相加得出。由于前两项是 0 和 1，接下来的项将是 1、2、3、5、8，依此类推。以下是该程序：

```go
/*斐波那契数列*/
/*包声明*/
package main

/*导入语句 - 导入 fmt 包*/
import (
	"fmt"
)

/*强制性的 main 函数*/
func main() {
	var terms, next int
	var previous, current int = 0, 1
	fmt.Printf("\n 请输入要生成的项数: ")
	fmt.Scanf("%d", &terms)
	if terms < 2 {
		fmt.Printf("\n 斐波那契数列至少包含两项")
	} else {
		fmt.Printf("\n\n 斐波那契数列:\n\n")
		for i := 0; i < terms; i++ {
			fmt.Printf("%d ", previous)
			next = previous + current
			previous = current
			current = next
		}
	}
	fmt.Printf("\n")
}
```

**输出：**

![](img/Image00085.jpg)

## 17.3 反转给定数字

下面是一个读取整数并将其反转的程序：

```go
/*反转数字*/
/*包声明*/
package main

/*导入语句 - 导入 fmt 包*/
import (
	"fmt"
)

/*强制性的 main 函数*/
func main() {
	var number int
	var rev int = 0
	fmt.Printf("\n 请输入一个数字: ")
	fmt.Scanf("%d", &number)
	for number > 0 {
		rev = (rev * 10) + (number % 10)
		number = number / 10
	}
	fmt.Printf("\n 反转结果: %d\n", rev)
}
```

**输出：**

![](img/Image00086.jpg)

## 17.4 字符串回文

如果一个字符串的反转与原字符串相同，则称该字符串为回文。例如，“book” 不是回文，而 “malayalam” 是回文。以下程序接收一个字符串作为输入并检查它是否为回文。请注意，未考虑大小写敏感性。
