

```
7 fmt.Println(aux)
9 aux = 10
11 fmt.Println(aux)
13 aux = "hello"
14 fmt.Println(aux)
```

空接口对于 Go 这种强类型语言来说，是一个非常模糊的上下文。在很多情况下，我们需要知道接口的底层数据类型。否则，就无法知道如何处理该数据。定义变量的一种实用方法是使用 `switch` 语句。示例 4.12 用一个整数、一个字符串和一个布尔值填充了一个空接口切片。`switch` 语句可以在运行时提取值的类型。这可以用来定义如何操作该值。在示例中，我们根据类型相应地修改了打印语句。注意打印语句中的 `%T` 获取的是值的类型的名称。

## 示例 4.12：探索空接口的类型。

```
1 package main
3 import "fmt"
5 func main() {
7 aux := []interface{}(42, "hello", true)
9 for i, v := range aux {
11 switch t := v.(type) {
13 default:
14 fmt.Printf("%T -> %s\n", t, i)
16 case int:
17 fmt.Printf("%T -> %d\n", t, i)
19 case string:
20 fmt.Printf("%T -> %s\n", t, i)
22 }
24 }
```

> Go 不能被完全认为是一门面向对象的语言。实际上，类或类层级等概念并不存在。然而，确实可以使用当前的语言定义获得类似的功能。但是，我们不能说 Go 是一门面向对象的语言。

## 4.4 总结

本章介绍了 Go 中中使用的结构体（struct）、方法（methods）和接口（interfaces）的概念。这些概念是 Go 语言的基础部分，将出现在本书的不同章节。此外，我们还解释了某些对早期使用者来说可能很奇怪的情况，例如方法中值接收者和指针接收者之间的区别。

## 第 5 章
 反射

在编程中，反射（reflection）是程序能够检查、修改其结构和行为的能力 [11]。换句话说，这是一种元编程。反射对于开发者来说是一个极其强大的工具，它扩展了任何编程语言的视野。遗憾的是，这带来了额外的复杂性。

在本章中，我们引入了 `reflect` 包，并解释了如何在运行时探索、内省和修改我们的代码的示例。根据 Go 组织反射包的方式，我们将这一解释分为两个部分。最后，我们介绍了 Go 如何使用标签（tags）来增强字段信息。

## 5.1 REFLECT.TYPE

理解 Go 反射的起点是记住在 4.3.1 中看到的空接口 `interface{}` 概念。空接口可以包含任何类型。例如：

```
unknown := interface{}(
a := 16
unknown = a
```

这段代码之所以有效，是因为 `interface{}` 接受一切，因此我们可以说任何东西都是空接口。这非常重要，因为函数 `reflect.TypeOf` 是代码内省的主要入口点，并接收空接口作为参数。观察示例 5.1 以及它是如何获取变量 `a` 和 `b` 的类型的。

**示例 5.1：** 用于基本类型的 `reflect.TypeOf`。

```
package main

import (
	"fmt"
	"reflect"
)

func main() {
	var a int32 = 42
	var b string = "Forty two"

	typeA := reflect.TypeOf(a)
	fmt.Println(typeA)

	typeB := reflect.TypeOf(b)
	fmt.Println(typeB)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_57_0.png)

`TypeOf` 函数返回 `Type` 类型，并带有一组方法用于代码内省。

示例 5.2 探索了一个带有两个字段的结构体。注意，我们可以遍历任何类型的字段，访问其名称和类型。

## 示例 5.2：用于结构体的 `reflect.TypeOf`。

```
package main

import (
	"fmt"
	"reflect"
)

type T struct {
	A int32
	B string
}

func main() {
	t := T(42, "forty two")

	type := reflect.TypeOf(t)
	fmt.Println(type)

	for i := 0; i < type.NumField(); i++ {
		field := type.Field(i)
		fmt.Println(field.Name, field.Type)
	}
}
```

除了类型探索外，我们还可以检查一个类型是否实现了接口。这可以使用示例 5.3 所示的 `Implements` 方法完成。这是 Go 中接口工作的一个良好示例。`Add` 方法有一个指针接收者（`*Calculator`），正因如此，主 `Calculator` 类型没有实现该接口。

## 示例 5.3：用于结构体的 `reflect.TypeOf`。

```
package main

import (
	"fmt"
	"reflect"
)

type Adder interface {
	Add(int, int) int
}

type Calculator struct {
}

func (c *Calculator) Add(a int, b int) int {
	return a + b
}

func main() {
	var ptrAdder Adder
	adderType := reflect.TypeOf(ptrAdder).Elem()

	c := Calculator{}
	calcType := reflect.TypeOf(c)
	calcTypePtr := reflect.TypeOf(&c)

	fmt.Println(calcType, calcType.Implements(adderType))
	fmt.Println(calcTypePtr, calcTypePtr.Implements(adderType))
}
```

使用 `reflect` 我们可以探索具有任意数量字段和类型的结构体。示例 5.4 使用了一个递归检查器，打印任何给定类型的结构。检查器会遍历结构体字段，如果它们是其他结构体。这是通过获取字段的 `Kind` 并与 `struct` 进行比较（`f.Type.Kind() == reflect.Struct`）来实现。你可以检查这段代码是如何跳过导出字段的。

## 示例 5.4：递归结构体检查器。

```
package main

import (
	"fmt"
	"reflect"
	"strings"
)

type T struct {
	B int
	C string
}

type S struct {
	C string
	D T
	E map[string]int
}

func printerReflect(offset int, t reflect.Type) {
	indent := strings.Repeat("", offset)
	if t.Kind() == reflect.Struct {
		for i := 0; i < t.NumField(); i++ {
			innerIndent := strings.Repeat("", offset+4)
			field := t.Field(i)
			if field.Kind() == reflect.Struct {
				printerReflect(offset+4, field.Type)
			} else {
				fmt.Printf("%s%T -> %s\n", innerIndent, field.Name, field.Type)
			}
		}
	}
}

func main() {
	s := S{C: "hello", D: T{B: 1, C: "world"}, E: map[string]int{"a": 1}}
	printerReflect(0, reflect.TypeOf(s))
}
```

## 5.2 REFLECT.VALUE

理解 Go 反射的起点是记住 4.3.1 中见过的空接口 `interface{}` 概念。空接口可以包含任何类型。例如：

```
unknown := interface{}(
a := 16
unknown = a
```

这段代码之所以有效，是因为 `interface{}` 接受一切，因此我们可以说任何东西都是空接口。这非常重要，因为函数 `reflect.TypeOf` 是代码内省的主要入口点，并接收空接口作为参数。观察示例 5.1 以及它是如何获取变量 `a` 和 `b` 的类型的。

`TypeOf` 函数返回 `Type` 类型，并带有一组方法用于代码内省。

示例 5.2 探索了一个带有两个字段的结构体。注意，我们可以遍历任何类型的字段，访问其名称和类型。

## 5.2 REFLECT.VALUE

我们已经看到 `reflect.Type` 允许访问字段。然而，为了知道如何处理该数据，我们需要知道接口的底层数据类型。

示例 5.5：

```go
package main

import (
	"fmt"
	"reflect"
)

func main() {
	var a int32 = 42
	var b string = "Forty two"

	typeA := reflect.TypeOf(a)
	fmt.Println(typeA)

	typeB := reflect.TypeOf(b)
	fmt.Println(typeB)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_57_0.png)

`TypeOf` 函数返回 `Type` 类型，并带有一组方法用于代码内省。

示例 5.2 探索了一个带有两个字段的结构体。注意，我们可以遍历任何类型的字段，访问其名称和类型。

## 示例 5.2：用于结构体的 `reflect.TypeOf`。

```go
package main

import (
	"fmt"
	"reflect"
)

type T struct {
	A int32
	B string
}

func main() {
	t := T(42, "forty two")

	type := reflect.TypeOf(t)
	fmt.Println(type)

	for i := 0; i < type.NumField(); i++ {
		field := type.Field(i)
		fmt.Println(field.Name, field.Type)
	}
}
```

除了类型探索外，我们还可以检查一个类型是否实现了接口。这可以使用示例 5.3 所示的 `Implements` 方法完成。这是 Go 中接口工作的一个良好示例。`Add` 方法有一个指针接收者（`*Calculator`），正因如此，主 `Calculator` 类型没有实现该接口。

## 示例 5.3：用于结构体的 `reflect.TypeOf`。

```go
package main

import (
	"fmt"
	"reflect"
)

type Adder interface {
	Add(int, int) int
}

type Calculator struct {
}

func (c *Calculator) Add(a int, b int) int {
	return a + b
}

func main() {
	var ptrAdder Adder
	adderType := reflect.TypeOf(ptrAdder).Elem()

	c := Calculator{}
	calcType := reflect.TypeOf(c)
	calcTypePtr := reflect.TypeOf(&c)

	fmt.Println(calcType, calcType.Implements(adderType))
	fmt.Println(calcTypePtr, calcTypePtr.Implements(adderType))
}
```

使用 `reflect` 我们可以探索任何种的结构体，具有任意数量的字段和类型。示例 5.4 使用了一个递归检查器，打印任何给定类型的结构。检查器会遍历结构体字段，如果它们是其他结构体。这是通过获取字段的 `Kind` 并与 `struct` 进行比较（`f.Type.Kind() == reflect.Struct`）来实现。你可以检查这段代码是如何跳过导出字段的。

## 示例 5.4：递归结构体检查器。

```go
package main

import (
	"fmt"
	"reflect"
	"strings"
)

type T struct {
	B int
	C string
}

type S struct {
	C string
	D T
	E map[string]int
}

func printerReflect(offset int, t reflect.Type) {
	indent := strings.Repeat("", offset)
	if t.Kind() == reflect.Struct {
		for i := 0; i < t.NumField(); i++ {
			innerIndent := strings.Repeat("", offset+4)
			field := t.Field(i)
			if field.Kind() == reflect.Struct {
				printerReflect(offset+4, field.Type)
			} else {
				fmt.Printf("%s%T -> %s\n", innerIndent, field.Name, field.Type)
			}
		}
	}
}

func main() {
	s := S{C: "hello", D: T{B: 1, C: "world"}, E: map[string]int{"a": 1}}
	printerReflect(0, reflect.TypeOf(s))
}
```

[/content] (由于你提供的原始文本中存在大量的重复和错乱（部分示例和正文交替出现），我已根据逻辑关系对内容进行了清理和翻译。如下：

[content]
```
7 fmt.Println(aux)
9 aux = 10
11 fmt.Println(aux)
13 aux = "hello"
14 fmt.Println(aux)
```

空接口对于 Go 这种强类型语言来说，是一个非常模糊的上下文。在很多情况下，我们需要知道接口的底层数据类型。否则，就无法知道如何处理该数据。定义变量的一种实用方法是使用 `switch` 语句。示例 4.12 用一个整数、一个字符串和一个布尔值填充了一个空接口切片。`switch` 语句可以在运行时提取值的类型。这可以用来定义如何操作该值。在示例中，我们根据类型相应地修改了打印语句。注意打印语句中的 `%T` 获取的是值的类型的名称。

## 示例 4.12：探索空接口的类型。

```
1 package main
3 import "fmt"
5 func main() {
7 aux := []interface{}(42, "hello", true)
9 for i, v := range aux {
11 switch t := v.(type) {
13 default:
14 fmt.Printf("%T -> %s\n", t, i)
16 case int:
17 fmt.Printf("%T -> %d\n", t, i)
19 case string:
20 fmt.Printf("%T -> %s\n", t, i)
22 }
24 }
```

> Go 不能被完全认为是一门面向对象的语言。实际上，类或类层级等概念并不存在。然而，确实可以使用当前的语言定义获得类似的功能。但是，我们不能说 Go 是一门面向对象的语言。

## 4.4 总结

本章介绍了 Go 中使用的结构体（struct）、方法（methods）和接口（interfaces）的概念。这些概念是 Go 语言的基础部分，将出现在本书的不同章节。此外，我们还解释了某些对早期使用者来说可能很奇怪的情况，例如方法中值接收者和指针接收者之间的区别。

## 第 5 章
 反射

在编程中，反射（reflection）是程序能够检查、修改其结构和行为的能力 [11]。换句话说，这是一种元编程。反射对于开发者来说是一个极其强大的工具，它扩展了任何编程语言的视野。遗憾的是，这带来了额外的复杂性。

在本章中，我们引入了 `reflect` 包，并解释了如何在运行时探索、内省和修改我们的代码的示例。根据 Go 组织反射包的方式，我们将这一解释分为两个部分。最后，我们介绍了 Go 如何使用标签（tags）来增强字段信息。

## 5.1 REFLECT.TYPE

理解 Go 反射的起点是记住在 4.3.1 中见过的空接口 `interface{}` 概念。空接口可以包含任何类型。例如：

```
unknown := interface{}(
a := 16
unknown = a
```

这段代码之所以有效，是因为 `interface{}` 接受一切，因此我们可以说任何东西都是空接口。这非常重要，因为函数 `reflect.TypeOf` 是代码内省的主要入口点，并接收空接口作为参数。观察示例 5.1 以及它是如何获取变量 `a` 和 `b` 的类型的。

**示例 5.1：** 用于基本类型的 `reflect.TypeOf`。

```
package main

import (
	"fmt"
	"reflect"
)

func main() {
	var a int32 = 42
	var b string = "Forty two"

	typeA := reflect.TypeOf(a)
	fmt.Println(typeA)

	typeB := reflect.TypeOf(b)
	fmt.Println(typeB)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_57_0.png)

`TypeOf` 函数返回 `Type` 类型，并带有一组方法用于代码内省。

示例 5.2 探索了一个带有两个字段的结构体。注意，我们可以遍历任何类型的字段，访问其名称和类型。

## 示例 5.2：用于结构体的 `reflect.TypeOf`。

```
package main

import (
	"fmt"
	"reflect"
)

type T struct {
	A int32
	B string
}

func main() {
	t := T(42, "forty two")

	type := reflect.TypeOf(t)
	fmt.Println(type)

	for i := 0; i < type.NumField(); i++ {
		field := type.Field(i)
		fmt.Println(field.Name, field.Type)
	}
}
```

除了类型探索外，我们还可以检查一个类型是否实现了接口。这可以使用示例 5.3 所示的 `Implements` 方法完成。这是 Go 中接口工作的一个良好示例。`Add` 方法有一个指针接收者（`*Calculator`），正因如此，主 `Calculator` 类型没有实现该接口。

## 示例 5.3：用于结构体的 `reflect.TypeOf`。

```
package main

import (
	"fmt"
	"reflect"
)

type Adder interface {
	Add(int, int) int
}

type Calculator struct {
}

func (c *Calculator) Add(a int, b int) int {
	return a + b
}

func main() {
	var ptrAdder Adder
	adderType := reflect.TypeOf(ptrAdder).Elem()

	c := Calculator{}
	calcType := reflect.TypeOf(c)
	calcTypePtr := reflect.TypeOf(&c)

	fmt.Println(calcType, calcType.Implements(adderType))
	fmt.Println(calcTypePtr, calcTypePtr.Implements(adderType))
}
```

使用 `reflect` 我们可以探索任何种的结构体，具有任意数量的字段和类型。示例 5.4 使用了一个递归检查器，打印任何给定类型的结构。检查器会遍历结构体字段，如果它们是其他结构体。这是通过获取字段的 `Kind` 并与 `struct` 进行比较（`f.Type.Kind() == reflect.Struct`）来实现。你可以检查这段代码是如何跳过导出字段的。

## 示例 5.4：递归结构体检查器。

```
package main

import (
	"fmt"
	"reflect"
	"strings"
)

type T struct {
	B int
	C string
}

type S struct {
	C string
	D T
	E map[string]int
}

func printerReflect(offset int, t reflect.Type) {
	indent := strings.Repeat("", offset)
	if t.Kind() == reflect.Struct {
		for i := 0; i < t.NumField(); i++ {
			innerIndent := strings.Repeat("", offset+4)
			field := t.Field(i)
			if field.Kind() == reflect.Struct {
				printerReflect(offset+4, field.Type)
			} else {
				fmt.Printf("%s%T -> %s\n", innerIndent, field.Name, field.Type)
			}
		}
	}
}

func main() {
	s := S{C: "hello", D: T{B: 1, C: "world"}, E: map[string]int{"a": 1}}
	printerReflect(0, reflect.TypeOf(s))
}
```
