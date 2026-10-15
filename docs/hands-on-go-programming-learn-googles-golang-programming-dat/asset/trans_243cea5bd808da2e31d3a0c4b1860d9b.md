
Key 91 是否存在：true

Key 95 是否存在：false

## 6.9 从映射中删除键

在映射中，允许使用 delete() 函数删除映射中存在的键。它是一个内置函数。它不返回任何值，并且如果给定映射中不存在该键，则不执行任何操作：

```
delete(map_name, key)
```

让我们看下面的示例：

### 程序 6.11

```go
// Go program to explain key deletion from a map

package main

import "fmt"

func main() {
// Create and initialize a map
var my_map = map[int]string{
1: "US",
91: "India",
86: "China",
44: "UK",
}
}
```

```go
fmt.Println("Map before deletion:\n", my_map)

// Delete keys in a Map using delete()
delete(my_map, 1)
delete(my_map, 44)
fmt.Println("\nMap after deletion:\n", my_map)
}
```

以下是上述代码的输出：

```
Map before deletion:
map[1:US 44:UK 86:China 91:India]

Map after deletion:
map[86:China 91:India]
```

```go
// Assigned the map into a new variable
new_map := my_map

// Perform modification in new_map
new_map[86] = "China"
new_map[33] = "France"

// Display map after modification
fmt.Println("New map:\n", new_map)
fmt.Println("Modification in old map:\n", my_map)
}
```

以下是上述代码的输出：

```
Original Map:
map[1:US 44:UK 81:Japan 91:India 972:Israel]
New map:
map[1:US 33:France 44:UK 81:Japan 86:China 91:India 972:Israel]
Modification in old map:
map[1:US 33:France 44:UK 81:Japan 86:China 91:India 972:Israel]
```

## 结论

映射是 Golang 中无序的键值对集合。映射中的键是唯一的，但值可能不是。它被广泛使用，因为它提供了快速查找，并且值可以通过键进行检索、更新或删除。

在 Golang 中，映射也称为关联数组、哈希表或字典。映射用于通过关联键查找值。

映射的零值为 nil，而 nil 映射没有键。因此，任何向 nil 映射添加键的尝试都会导致运行时错误。

在 Go 中，映射可以通过使用映射字面量或内置 make() 函数进行初始化。

映射字面量是在 Go 编程中用一些数据初始化映射的最简单方法。您只需在花括号内传递用冒号分隔的键值对即可。最后一个尾随逗号是必要的，否则您会收到编译器错误。

在 Go 中，您可以使用内置的 make() 函数初始化映射。您只需将映射的类型传递给 make() 函数，它将返回一个已初始化且可立即使用的映射。

您可以使用 Go 编程语言中 for 循环的 range 形式遍历映射。它在每次迭代中为您提供键值对。

在 Golang 中，映射是一个无序集合，因此，遍历映射的迭代顺序每次都不保证相同。因此，如果您多次运行任何程序，您将得到不同顺序的结果。

在映射中，如果您尝试添加已存在的键，它只会覆盖或用新值更新该键的值。

如果给定映射中不存在键，它将返回零值，即 nil；如果键存在于给定映射中，它将返回与该键相关的值。

在 Go 中，当您使用语法检索分配给给定键的值时，它还会返回一个额外的布尔值，如果键存在于映射中则为 true，如果不存在则为 false。

在映射中，允许使用 delete() 函数删除映射中存在的键。它是 Golang 中的内置函数。它不返回任何值，并且如果给定映射中不存在该键，则不执行任何操作。

映射是 Golang 中的引用类型。当您将映射分配给新变量时，两者都引用相同的底层数据结构。因此，由一个变量所做的更改对另一个变量可见。

## 问题

Golang 映射是什么？编写一个 Go 程序使用映射字面量初始化映射。

解释在 Golang 中使用 make() 函数初始化映射。

编写一个 Go 程序来解释遍历映射。

如何在 Golang 映射中添加键值对？使用 Go 程序进行解释。

编写一个 Go 程序来更新 Golang 映射中的键值对。

如何检索映射中键的值？借助 Go 程序进行解释。

如何检查键是否存在于 Golang 映射中？编写一个 Go 程序来解释它。

编写一个 Go 程序来解释从映射中删除键。

## 第 7 章

## 结构体

结构体是一种用户定义的类型，表示字段的集合。结构具有相同或不同数据类型的不同字段。结构体或结构可以与面向对象编程范式中的类进行比较。结构主要用于需要定义由不同单个字段或属性组成的模式时。

## 结构

- 什么是结构体？
- 声明和初始化结构体类型
- 结构体的零值
- 访问结构体的字段
- 指向结构体的指针
- 使用指针更新结构体成员的值
- 导出的与未导出的结构体和结构体字段
- 结构体是值类型
- 结构体相等性

## 目标

本章解释了结构体的基本概念以及如何在 Go 编程语言中使用它。它涵盖了如何声明和初始化结构体类型、访问结构体的字段、指向结构体的指针、导出的和未导出的结构体以及结构体字段。

### 7.1 什么是结构体？

结构体是包含命名字段和属性集合的用户定义类型。结构体使用分组相关数据形成一个单一单元。Golang 可以通过组合一个或多个类型（包括内置类型和用户定义类型）来声明和创建其数据类型。

结构体是在 Golang 中创建具体用户定义类型的唯一方法。它们提高了模块化，并允许在系统中创建和传递复杂的数据结构。

### 7.2 声明和初始化结构体类型

结构体的声明以关键字 type 开始，然后是新结构体的名称，最后是关键字 struct。在大括号内，一系列数据字段以名称和类型指定。

您可以使用结构体字面量初始化结构体类型变量。您还需要按结构体中声明的相同顺序传递字段值。

**结构体语法：**

```text
type identifier struct{
field_1 data_type
field_2 data_type
}
```

让我们看下面的程序：

### 程序 7.1

```go
// Golang program to declare and define struct

package main

import "fmt"
```

```go
// Define a struct type
type city_list struct {
city string
state string
country string
}

func main() {
// Declare and initialize struct using a struct literal
c1 := city_list{"Mumbai", "Maharashtra", "India"}
c2 := city_list{"Chicago", "Illinois", "US"}
c3 := city_list{"Sydney", "New South Wales", "Australia"}

fmt.Println("City1:", c1)
fmt.Println("City2:", c2)
fmt.Println("City3:", c3)
}
```

以下是上述代码的输出：

City1: {Mumbai Maharashtra India}
City2: {Chicago Illinois US}
City3: {Sydney New South Wales Australia}

让我们看下面的程序：

### 程序 7.2

```go
// Golang program to declare and define struct
```

```go
package main

import "fmt"

// Define a struct type
type city_list struct {
city string
state string
country string
}

func main() {
// Naming fields while initializing a struct
c1 := city_list{city: "Mumbai", state: "Maharashtra", country: "India"}
c2 := city_list{city: "Chicago", state: "Illinois", country: "US"}
c3 := city_list{city: "Sydney", state: "New South Wales", country: "Australia"}

fmt.Println("City1:", c1)
fmt.Println("City2:", c2)
fmt.Println("City3:", c3)
}
```

以下是上述代码的输出：

**City1:** {Mumbai Maharashtra India}
**City2:** {Chicago Illinois US}
