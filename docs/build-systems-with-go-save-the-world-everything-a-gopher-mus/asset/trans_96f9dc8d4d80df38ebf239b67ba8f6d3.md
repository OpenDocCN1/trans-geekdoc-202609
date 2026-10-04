

```go
C float32

func main() {
	t := T{42, "forty two", 3.14}

	valueT := reflect.ValueOf(t)
	fmt.Println(valueT.Kind(), valueT)

	for i:=0;i<valueT.NumField();i++ {
		field := valueT.Field(i)
		fmt.Println(field.Kind(), field.String(), field.Interface())
	}
}
```

## 5.2.1 设置值

使用 `reflect.value`，我们可以在运行时设置值。每个值都有 `SetInt32`、`SetFloat32`、`SetString` 等方法，可以将字段设置为 `int32`、`float32`、`string` 等值。示例 5.8 将结构体中的字符串字段设置为大写。

## 示例 5.8: 使用反射设置值。

```go
package main

import (
	"fmt"
	"reflect"
	"strings"
)

type T struct {
	A string
	B int32
	C string
}

func main() {
	t := T{"Hello", "42"}
	fmt.Println(t)

	valueT := reflect.ValueOf(&t).Elem()
	for i:=0;i<valueT.NumField();i++ {
		f := valueT.Field(i)
		if f.Kind() == reflect.String {
			current := f.String()
			f.SetString(strings.ToUpper(current))
		}
	}
	fmt.Println(valueT)
}
```

如果操作无效，操作将发生 panic（崩溃）。例如，将字段设置为不同的类型，或尝试设置未设置的字段。在示例 5.9 中，字段 `c` 是未导出的。必须使用 `canSet()` 方法进行额外的检查。使用此方法我们可以跳过未导出字段。注意输出没有修改 `c` 的值。

## 示例 5.9: 考虑未导出字段的反射设置值。

```go
package main

import (
	"fmt"
	"reflect"
	"strings"
)

type T struct {
	A string
	B int32
	C string
}

func main() {
	t := T{"Hello", 42}

	valueOff := reflect.ValueOf(&t).Elem()
	for i := 0; i < valueOff.NumField(); i++ {
		f := valueOff.Field(i)
		if f.Kind() == reflect.String {
			if f.CanSet() {
				current := f.String()
				f.SetString(strings.ToUpper(current))
			}
		}
	}
	fmt.Println(t)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_63_0.png)

## 5.3 动态创建函数

在之前的章节中，我们探索了如何检查字段和修改值。此外，`reflect` 包允许动态地创建新实体，以函数的形式。这提供了在其他编程语言中可以某些功能。例如，Go 缺乏泛型带来了一些限制，尽管在本文写作时已经有一个相关的提案。

假设我们想写一个通用的加法操作函数。该函数必须能够处理数字（整数和浮点数）并拼接字符串。由于当前的语言定义，这是可能的。查看下面的代码。它不允许任何形式的函数重载。每个函数必须有唯一的名称。同样，泛型的缺乏使得无法通过为每个类型定义的相同加运算符 (`+`) 来重用相同的代码。

```go
func Sum(a int, b int) int {..}
```

```go
func Sum(a float32, b float32) float32 {..} // 不唯一。
```

```go
func Sum(a string, b string) string {..} // 不唯一。
```

一个有趣的变通是使用 `reflect.MakeFunction` 来构建具有不同签名的自定义函数。示例 5.10 在 `BuildAdder` 中构建了一个具有两个相同类型参数和一个输出的 `add` 函数。`MakeFunction` 接收一个相同类型函数的指针，并接收一个函数类型和一个位于数组中的可变数量的 `Value` 类型，返回一个 `Value` 数组。我们使用一个 `switch` 语句填充该函数，根据其类型实现两个参数之间的加法。最后，我们将此函数设置为原始函数（`fn.Set(newF)`）。

## 示例 5.10: 使用 `reflect.MakeFunction` 在运行时创建函数。

```go
package main

import (
    "fmt"
    "reflect"
)

func BuildAdder(i interface{}) {
    fn := reflect.ValueOf(i).Elem()
    newF := reflect.MakeFunction(fn.Type(), func(in []reflect.Value) []reflect.Value {
        if len(in) > 2 {
            return []reflect.Value{in[2].Value()}
        }
        a, b := in[0], in[1]
        if a.Kind() != b.Kind() {
            return []reflect.Value{reflect.ValueOf(nil)}
        }
        var result reflect.Value
        switch a.Kind() {
            case reflect.Int8, reflect.Int32, reflect.Int64:
                result = reflect.ValueOf(a.Int() + b.Int())
            case reflect.Uint, reflect.Uint8, reflect.Uint16, reflect.Uint32, reflect.Uint64:
                result = reflect.ValueOf(a.Uint() + b.Uint())
            case reflect.Float32, reflect.Float64:
                result = reflect.ValueOf(a.Float() + b.Float())
            case reflect.String:
                result = reflect.ValueOf(a.String() + b.String())
            default:
                result = reflect.ValueOf(interface{}(nil))
        }
        return []reflect.Value{result}
    })

    fn.Set(newF)
}

var intAdder func(int64, int64) int
var floatAdder func(float64, float64)
var strAdder func(string, string)

func main() {
    BuildAdder(&intAdder)
    fmt.Println(intAdder(10, 20))

    BuildAdder(&floatAdder)
    fmt.Println(floatAdder(1.1, 2.2))

    BuildAdder(&strAdder)
    fmt.Println(strAdder("Hello, ", "World"))
}
```