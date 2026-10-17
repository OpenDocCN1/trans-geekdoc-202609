
# 4. Go 语言中 `defer` 语句的执行顺序是怎样的？

# 5. `panic` 在错误处理中起什么作用？

# 6. 如何使用 `recover` 函数捕获 `panic`？

# 第 19 章：反射

## 引言

反射是编程语言的一项关键特性，可以定义为在运行时检查程序的执行情况并对其进行修改。它在面向对象和动态编程中尤为重要，允许开发者编写灵活且自适应的代码。在本章中，我们将深入探讨 Go 中的反射概念。

## 结构

在本章中，我们将讨论以下主题：

* 反射简介
* `reflect` 包
* `Type`
* `Value`
* `Kind`
* `Numfield()`
* `Field`
* `String()`、`Int()` 和 `Float()`
* 反射法则

## 目标

学习本章后，你将能够在运行时检查变量的类型，动态地创建和修改变量及函数，并分析 Go 中的结构体字段。这些技能将使你利用 Go 的反射能力处理高级编程任务。

## 反射简介

反射允许在运行时探索任何数据，而无需知道其在编译时定义的名称。通过使用反射，我们可以检查任何方法、接口、结构体或任何数据的行为。在运行时检查源码被称为反射。

通过使用反射，我们可以获取任何类型的类型、字段和值。虽然在 Go 语言中，每个变量都声明了其类型，但在很多情况下我们可能需要在运行时知道变量的类型。这时反射派上用场了。

示例：

```go
func main(){
	slice_val :=[]string {"one", "two", "three", "four", "five", "six"}
	map_val := map [string] int64{}

	for itr:=0; itr<len(slice_val); itr++{
		map_val[slice_val[itr]] = 0
	}
}
```

在前面的示例中，我们初始化了一个字符串类型的切片。我们需要使用切片中的项作为 `map` 的键。这里，我们声明了一个键类型为字符串的 `map`。如果我们需要在运行时初始化该 `map`，或者切片是任意类型怎么办？在这种情况下，我们需要在运行时找到切片的类型。为此，我们可以使用反射。

`reflect` 包应该用于通用编程或框架，但应避免用于性能敏感的代码或类型安全至关重要的地方。它会引入性能开销，降低类型安全性，并使代码更难以维护。

## Reflect 包

Go 提供了一个名为 `reflect` 的内置包，它提供了运行时反射的功能。我们可以在标准库中获取 `reflect` 包。`reflect` 包包含了一些变量和方法，用于操作各种类型的对象。它用于返回静态或接口类型变量的动态类型。由于空接口可以接受任何值，我们可以使用 `reflect` 包获取接口所接受的精确类型。`reflect` 包主要用于获取变量的类型、值和种类。

## Type

`reflect` 包提供了 `TypeOf` 方法来获取变量的类型。该函数返回类型 `reflect` 类型的值。该类型有多种方法来定义该类型的属性。该函数的签名如下：

```go
funcTypeOf( i interface{}) type
```

该函数接受一个接口作为参数。任何值都被接口接受，然后由 `TypeOf` 函数进行分析。

语法：

```go
variable_type := reflect.TypeOf(variable)
```

示例：

```go
package main

import (
	"fmt"
	"reflect"
)

func main(){
	type student struct{
		name string
		age int
	}
	stu := student{"Akansha", 17}
	fmt.Println(stu)
	stu_type := reflect.TypeOf(stu)
	fmt.Println("type of 'stu' variable:", stu_type)
	fmt.Println("type of 'stu_type' variable:", reflect.TypeOf(stu_type))
	fmt.Println("name of 'stu' variable type:", stu_type.Name())
}
```

输出：

```text
{Akansha 17}
type of 'stu' variable: main.student
type of 'stu_type' variable: *reflect.rtype
name of 'stu' variable type: student
```

## Value

`reflect` 包有一个方法来评估变量的值。

语法：

```go
value := reflect.ValueOf( variable )
```

示例：

```go
package main

import (
	"fmt"
	"reflect"
)

func main(){
	type student struct{
		name string
		age int
	}
	stu := student{"Akansha", 17}
	fmt.Println(stu)
	stu_type := reflect.TypeOf(stu)
	fmt.Println("value of 'stu' variable:", reflect.ValueOf(stu))
	fmt.Println("value of 'stu_type' variable:", reflect.ValueOf(stu_type))
}
```

输出：

```text
{Akansha 17}
value of 'stu' variable: {Akansha 17}
value of 'stu_type' variable: main.student
```

## Kind

`reflect` 包提供了 `TypeOf` 方法来获取变量的类型。该函数返回类型 `reflect` 类型的值。该类型有多种方法来定义该类型的属性。该函数的签名如下：

```go
funcTypeOf( i interface{}) type
```

该函数接受一个接口作为参数。任何值都被接口接受，然后由 `TypeOf` 函数进行分析。

通过使用反射，我们可以获取任何类型的类型、字段和值。虽然在 Go 语言中，每个变量都声明了其类型，但在很多情况下我们可能需要在运行时知道变量的类型。这时反射派上用场了。

示例：

```go
fmt.Printf("Type of name is %T and value is %v\n", name, name)
fmt.Printf("Type of age is %T and value is %v\n", age, age)
fmt.Printf("Type of income is %T and value is %v\n", income, income)
```

Output:

```text
Type of name is reflect.Value and value is Akansha
Type of age is reflect.Value and value is 17
Type of income is reflect.Value and value is 40000.566

Type of name is string and value is Akansha
Type of age is int64 and value is 17
Type of income is float64 and value is 40000.56640625
```

## 反射定律

Go 定义了三条反射定律，这些定律定义了反射的工作以及在使用反射时需要记忆的点。这三条反射定律如下：

### 反射从接口值到反射对象

由于空接口可以接受任何值，这使得理解接口中存储了什么类型的数值非常困难。在这里，反射用于获取接口所包含的类型和值。正如我们在上一个示例中看到的，通过 `TypeOf` 和 `ValueOf` 函数评估变量的类型和值。第一条反射定律关于从接口中提取反射对象。

示例：

```go
package main

import (
	"fmt"
	"reflect"
)

func show_value(i interface{}) {
	value_type := reflect.TypeOf(i)
	value := reflect.ValueOf(i)
	fmt.Printf("Passed value is %v of type %v\n", value, value_type.Kind())
	fmt.Println(reflect.TypeOf(value))
	fmt.Println(reflect.TypeOf(value_type))
}

func main() {
	type student struct {
		name   string
		age    int
		income float32
	}
	stu := student{"Akansha", 17, 40000.565}
	show_value(stu)
}
```

Output:

```text
passed value is {Akansha 17 40000.566} of type struct
reflect.Value
*reflect.rtype
```

### 反射从反射对象到接口值

第二条定律是第一条定律的反向。第二条定律说类型 `reflect.Value` 和 `reflect.Type` 可以转换为接口值。以下是反射第二条定律的示例。

示例：

```go
package main

import (
	"fmt"
	"reflect"
)

func show_value(i interface{}) {
	value_type := reflect.TypeOf(i)
	value := reflect.ValueOf(i)
	fmt.Println(reflect.TypeOf(value))
	fmt.Println(reflect.TypeOf(value_type))
	interface_val := value.Interface()
	fmt.Println("Interface value is:", interface_val)
	fmt.Println("Interface value type is:", reflect.TypeOf(interface_val).Kind())
}

func main() {
	type student struct {
		name   string
		age    int
		income float32
	}
	stu := student{"Akansha", 17, 40000.565}
	show_value(stu)
}
```

Output:

```text
reflect.Value
*reflect.rtype
Interface value is: {Akansha 17 40000.566}
Interface value type is: struct
```

### 修改反射对象时，值必须是可设置的

在使用 `ValueOf` 函数获取变量值时，它返回类型为 `reflect.Value` 的值。第三条定律说，要给 `reflect.Value` 类型变量赋值，该值必须是 `reflect.Value` 类型。如果不是相同类型，它将抛出 `panic`（崩溃）。

示例：
