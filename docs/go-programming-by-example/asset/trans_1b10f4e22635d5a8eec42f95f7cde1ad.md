

```
package main

import "fmt"

func main(){

    var x int

    x = 10
    fmt.Println(x)  // print a value of x
    fmt.Println(&x) // print address of x


    // declare pointer
    var num *int
    val := new(int)

    num = new(int)
    *num = x   // set value

    val = &x   // set address

    fmt.Println("===pointer num===")
    fmt.Println(*num)  // print a value of x
    fmt.Println(num) // print address of x
    fmt.Println("===pointer val===")
    fmt.Println(*val)  // print a value of x
    fmt.Println(val) // print address of x

}
```

保存此文件。

尝试构建并运行它。程序输出的示例显示在下图中。

![ch5-2](Images/ch5-2.png)  

## 5.2 Demo: 单向链表

在本节中，我们可以从头开始创建一个单向链表。你可以阅读你的数据结构书籍来了解单向链表是什么。你也可以在维基百科上阅读它，[http://en.wikipedia.org/wiki/Linked\_list#Singly\_linked\_lists](http://en.wikipedia.org/wiki/Linked_list#Singly_linked_lists) 。

现在我们可以使用 Go 创建一个单向链表。首先，我们创建文件夹，linkedlist。

```
$ mkdir linkedlist
$ cd linkedlist
```

创建一个文件，**main.go**。导入 Go 包并为指针定义结构体。

```
package main

import (
    "fmt"
    "math/rand"
)

type Node struct {
    value int
    next *Node
}
```

next 是指针变量，它引用下一个指针变量的内存地址。

我们创建一个函数，add()，我们在单向链表上插入新数据。以下是 add() 函数的实现。

```
func add(list *Node,data int) *Node {
    if list==nil {
        list := new(Node)
        list.value = data
        list.next = nil

        return list
    }else{
        temp := new(Node)
        temp.value = data
        temp.next = list

        list = temp

        return list
    }
}
```

我们也可以显示单向链表的内容。创建一个函数，display()，并编写此代码。

```
func display(list *Node){
    var temp *Node
    temp = list

    for temp!=nil {

        fmt.Println(temp.value)
        temp = temp.next
    }
}
```

在主入口中，我们将单向链表定义为指针变量，称为 head。我们向指针列表中添加五个数据。然后，我们显示所有数据。为 main() 函数编写以下代码。

```
func main(){

    var head *Node
    head = nil

    // add 5 data
    fmt.Println("=== insert 5 data=== ")
    n := 0
    for n < 5 {
        fmt.Printf("data %d\n",n)

        head = add(head,rand.Intn(100))
        n++
    }
    fmt.Println("=== display ===")
    display(head)

}
```

保存此文件。  

尝试构建并运行它。

```
$ go build
$ go run main.go
```

程序输出的示例可以在下图中看到。

![ch5-3](Images/ch5-3.png)  

# 6. 结构体和结构体方法

本章解释如何在 Go 中使用结构体和结构体方法。

## 6.1 结构体

我们可以使用结构体扩展我们的对象。如果你有 C/C++ 经验，我们在 Go 语言中使用结构体方法。

要定义一个结构体，我们可以使用 struct 关键字，例如，我们为结构体对象定义 struct_name。

```
type struct_name struct {
  // fields
}
```

为了说明，我们创建一个结构体，Employee。首先，我们通过创建一个名为 structdemo 的文件夹来构建一个新项目。

```
$ mkdir structdemo
$ cd structdemo
```

然后，创建一个名为 **main.go** 的文件。首先，我们定义我们的包和一个结构体，Employee。

```
package main

import (
    "fmt"
    "time"
)

// define  a struct
type Employee struct {
    id int
    name string
    country string
    created time.Time
}
```

Employee 结构体有四个字段：id、name、country 和 created。

要在 Go 中使用结构体，我们可以使用 new() 实例化我们的结构体对象。然后，我们设置其值。

在 **main.go** 文件的入口点编写此代码。

```
func main() {

    // declare variable
    var emp Employee
    newEmp := new(Employee)

    // set values
    emp.id = 2
    emp.name = "Employee 2"
    emp.country = "DE"
    emp.created = time.Now()

    newEmp.id = 5
    newEmp.name = "Employee 5"
    newEmp.country = "UK"
    newEmp.created = time.Now()


    // display
    fmt.Println("=====================")
    fmt.Println(emp.id)
    fmt.Println(emp.name)
    fmt.Println(emp.country)
    fmt.Println(emp.created)

    fmt.Println("=====================")
    fmt.Println(newEmp.id)
    fmt.Println(newEmp.name)
    fmt.Println(newEmp.country)
    fmt.Println(newEmp.created)
}
```

保存此文件。

尝试构建并运行它。

```
$ go build
$ go run main.go
```

程序输出的示例：

![ch6-1](Images/ch6-1.png)  

## 6.2 方法

我们通过传递结构体对象在我们的结构体对象中定义方法。为了说明，我们创建 Circle 结构体对象，它具有以下方法：

*   display()

*   area()

*   circumference()

*   moveTo()

如何实现？

创建一个名为 structmethod 的文件夹。

```
$ mkdir structmethod
$ cd structmethod
```

下一步是创建一个名为 **main.go** 的文件。导入我们的包并定义 Circle 结构体对象。

```
package main

import (
    "fmt"
    "math"
)

// define  a struct
type Circle struct {
    x,y int
    r float64
}
```

Circle 结构体有三个字段：x、y 和 r。

基本上，我们可以以创建函数相同的方式创建结构体方法。我们在方法名称前面传递我们的结构体对象。以下是我们结构体方法的实现。

```
func (c Circle) display() {
    fmt.Printf("x=%d,y=%d,r=%.2f\n",c.x,c.y,c.r)
}
func (c Circle) area() float64 {
    return math.Pi * math.Pow(c.r,2)
}
func (c Circle) circumference() float64 {
    return 2* math.Pi * c.r
}
func (c Circle) moveTo(newX,newY int) {
    c.x = newX
    c.y = newY
}
```

最后一步是在主程序中使用我们的结构体方法。编写以下代码。

```
func main() {
    // methods
    shape := Circle{10,5,2.8}
    shape.display()
    fmt.Printf("area=%2.f\n",shape.area())
    fmt.Printf("circumference=%2.f\n",shape.circumference())

    shape.moveTo(5,5)
    shape.display()
}
```

保存此代码。

在你的终端上构建并运行 **main.go**。

```
$ go build
$ go run main.go
```

程序输出的示例：

![ch6-2](Images/ch6-2.png)  

# 7. 字符串操作

本章解释如何在 Go 中使用字符串操作。

## 7.1 入门

我们已经将字符串用作数据类型。以下是处理字符串数据并在终端上打印的示例代码。

```
    // simple string demo
    var str string
    str = "Hello world"
    fmt.Println(str)
```

在本节中，我们尝试操作字符串数据。我们将探索 strconv，[http://golang.org/pkg/strconv/](http://golang.org/pkg/strconv/) 和 strings，[http://golang.org/pkg/strings/](http://golang.org/pkg/strings/) 包的几个函数。

首先，我们通过创建一个名为 stringdemo 的文件夹来构建一个新项目。

```
$ mkdir stringdemo
$ cd stringdemo
```

创建一个名为 **main.go** 的文件。导入 fmt、strcov 和 strings 包。

```
package main

import (
    "fmt"
    "strconv"
    "strings"
)
```

下一步是探索如何使用字符串。

## 7.2 拼接字符串

如果你有一组字符串，你可以将其拼接成一个字符串。你可以使用 + 运算符和 fmt.Sprintf() 函数。以下是示例代码

```
    str1 := "hello"
    str2 := "world"
    str3 := str1 + str2
    fmt.Println(str3)

    str4 := fmt.Sprintf("%s %s",str1,str2)
    fmt.Println(str4)
```

## 7.3 字符串转数字

有时你想执行数学运算但输入数据是字符串类型。要将字符串类型转换为数字，你可以使用 strcov.ParseInt() 将字符串转为整型，以及 strcov.ParseFloat() 将字符串转为浮点型。

以下是实现字符串到数字转换的示例代码。  
