
**示例：**

```go
package main
import "fmt"
type My_error struct{}
func (error_object *My_error) Error() string{
    return "Unexpected outcome"
}
func main(){
    fmt.Println(&My_error{})
}
```

**输出：**

```
Unexpected outcome
```

在上面的程序中，我们创建了一个没有任何字段的 `struct My_error`。使用 `struct My_error` 用于实现 `Error` 方法，该方法返回 `string` 类型的错误消息。我们可以在发生任何错误时直接调用 `Error` 方法来查找其输出。

**示例：**

```go
package main
import "fmt"
type My_error struct{}
func (error_object *My_error) Error() string{
    return "Unexpected outcome"
}
func main(){
    obj := My_error{}
    fmt.Println(obj.Error())
}
```

## errors 包

Go 在 `src` 目录下有一个名为 `errors` 的内置包。它实现了各种用于处理错误的函数。它有一个名为 `New` 的函数，用于返回指定格式的错误。

**示例：**

```go
package main
import ("fmt"
"os"
"errors"
)
func main(){
    file, err := os.Open("./example.json")
    if(err!=nil){
        error_msg := errors.New("file operation failed")
        fmt.Println(error_msg)
    }
    if(err==nil){
        fmt.Println("file opened successfully", file)
    }
}
```

**输出：**

```
file operation failed
```

在上面的程序中，在发生错误的情况下，我们通过传递错误消息调用了 `New` 函数。该函数接受 `string` 类型的错误消息并作为 `error` 类型值返回。在这里，`error_msg` 的类型是 `errors.errorString`，它指向 `errors.errorString`。`errorString` 是 `errors` 包中一个具有 `string` 类型类型字段的结构体类型。该结构体类型 `errorString` 实现了 `Error` 方法并返回一个 `string` 类型的值。为了更好地理解，你必须查看 `errors` 包。

## defer 语句

`defer` 关键字会延迟函数调用的执行，直到周围的函数返回。这对于清理资源（如关闭文件或数据库连接）特别有用。当使用多个 `defer` 语句时，它们将按照后进先出（LIFO）的顺序执行。

以下是 `defer` 工作原理示例：

```go
package main
import "fmt"

func main() {
    fmt.Println("Start")
    defer fmt.Println("First defer")
    defer fmt.Println("Second defer")
    fmt.Println("End")
}
```

**输出：**

```
Start
End
Second defer
First defer
```

你也可以在循环内部 `defer`，但要小心，因为调用直到周围函数返回时才会执行，而不是在循环迭代结束时执行。如果循环运行多次，可能会导致资源耗尽。

`Panic` 是另一种错误处理方式。它用于检查程序运行过程中出现的意外错误。它与异常某些相似，因为它也发生在运行时。如果函数返回了显示出意外行为的错误，它将跳过该函数的执行。每当在任何函数中调用 `Panic` 函数时，它会停止该函数的执行，执行提供的用于处理该 panic 的 `defer` 语句，返回调用者语句，并继续后续执行。

在 Go 中，某些情况下，运行时错误也会导致 panic，例如越界访问、除以零等等。

### 语法

`Panic (interface {})`

`Panic` 接受任何值作为参数，因为空接口可以接受任何类型的值。

### 示例

```go
package main

import "fmt"

var result int

func op(a, b int) int {
    result = a / b
    return result
}

func main(){
    result = op(10, 0)
    fmt.Println("Completed")
}
```

### 输出

```
panic: runtime error: integer divide by zero
```

执行上述示例时，会产生一个由数字除以零引起的运行时错误导致的 panic。当 panic 发生时，程序会立即终止。当程序显示出意外行为时，我们可以在特定情况下调用 `panic` 函数并按设置错误消息。

### 示例

```go
package main

import "fmt"

var result int

func op(a, b int) int {
    if(b==0){
        panic("Can't divide a number by zero!")
    }
    result = a/b
    return result
}

func main(){
    result = op(10, 0)
    fmt.Println("Completed")
}
```

### 输出

```
panic: Can't divide a number by zero!
```

在这里，一切保持不变，但它显示了所需的错误消息。同样，可以通过调用 `panic` 函数处理任何可能显示意外行为的条件或状况来启动 panic。

### 示例

```go
package main

import "fmt"

func show_value(max int){
    for itr:=1; itr<=max; itr++{
        if(itr==5){
            panic("Not acceptable")
        }
        fmt.Println(itr)
    }
}

func main(){
    show_value(10)
    fmt.Println("Completed")
}
```

### 输出

```
1
2
3
4
panic: Not acceptable
```

在上面提供的程序中，我们不想显示大于 4 的值。如果传递的参数大于 4，它会打印到 4 的值；而当遇到 5 时，它会显示 panic 并停止后续执行。在某些情况下，可以在程序终止之前执行某些清理或必要操作。可以通过使用 `defer` 函数在 panic 发生后执行来实现这一点。

### 示例

```go
package main

import "fmt"

var result int

func op_defer(){
    fmt.Println("op defer executed")
}

func main_defer(){
    fmt.Println("main defer executed")
}

func op(a, b int) int {
    defer op_defer()
    if(b==0){
        panic("Can't divide a number by zero!")
    }
    result = a/b
    return result
}

func main(){
    defer main_defer()
    result = op(10, 0)
    fmt.Println("Completed")
}
```

### 输出

```
op defer executed
main defer executed
panic: Can't divide a number by zero!
```

## 恢复

Go 提供了一个名为 `Recover` 的内置函数来控制 panic 情况。在 Go 语言中，错误处理是通过使用 `recover` 函数完成的，就像其他语言使用 `try-catch`、`try-except` 或其他方法一样。在上面的示例中，我们看到当 panic 发生时程序执行终止。`Recover` 函数用在 `defer` 函数内部，因为只有 `defer` 语句会在 panic 之后执行。传递给 panic 的值由 `recover` 函数返回。如果程序中没有 panic，`recover` 函数返回 `nil`。

### 示例

```go
package main

import "fmt"

var result int

func op_defer(){
    fmt.Println("op defer executed")
}

func main_defer(){
    fmt.Println("main defer executed")
}

func op(a, b int) int {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Panic recovered", r)
        }
        op_defer()
    }()
    if(b==0){
        panic("Can't divide a number by zero!")
    }
    result = a/b
    return result
}

func main(){
    defer main_defer()
    result = op(10, 0)
    fmt.Println("Completed")
}
```

### 输出

```
main defer executed
Panic recovered Can't divide a number by zero!
op defer executed
```

在上面的程序中，当 panic 发生时程序执行终止。然而，在终止之前，它执行了 `defer` 调用。在执行 `defer` 函数时，`recover` 函数接管了 panic 并返回传递给 panic 的非空值。在这里，执行 `op_defer` 后，它返回调用者语句并继续执行。

## 结论

可以得出，我们可以通过 `error` 类型的多个返回值来识别错误。Go 提供了 `errors` 包，提供了各种函数来处理和分析错误。所有最后执行的操作都可以通过 `defer` 语句完成。内置函数 `panic` 控制程序的流并启动 panic。这种 panic 状态由 `recover` 函数控制。让我们在下一章讨论 Go 的另一个特性：反射。

## 问题

1. 用示例解释 Go 中的错误处理。

2. `defer` 语句的目的是什么？

3. "New" 函数在错误处理中的用途是什么？

4. Go 中 `defer` 语句的执行顺序是怎样的？

5. `panic` 在错误处理中的作用是什么？

6. 如何使用 `recover` 函数捕获 panic？

# 第 19 章 反射

## 结构

在本章中，我们将讨论：

* 反射简介
* `reflect` 包
* 反射法则

## 目标

学习本章后，你能够：

* 在运行时检查变量的类型
* 创建并修改变量和函数
* 分析结构字段

## 引言

反射是编程语言的一项关键特性，可以定义为在运行时对程序执行进行检查和修改。反射在面向对象的编程语言中起着重要作用。

反射允许在运行时探索任何数据，而无需在编译时知道其名称。通过反射，我们可以检查任何方法、接口、结构体或任何数据的行为。

Go 语言提供了一个名为 `reflect` 的内置包，它提供了运行时反射的功能。我们可以在 `src` 目录中找到 `reflect` 包。`reflect` 包包含了一些变量和方法，用于操作各种类型的对象。它被用于返回具有静态类型或接口类型的变量的动态类型。由于空接口可以接受任何值，我们可以使用 `reflect` 包获取接口所接受的具体类型。`reflect` 包主要用于获取变量的类型、值和种类（kind）。

## 类型 (Type)

`reflect` 包提供了 `TypeOf` 方法来获取变量的类型。该函数返回 `reflect.Type` 类型的值。该类型有多种方法可以定义该类型的属性。该函数的签名如下：

`func TypeOf(i interface{}) type`

该函数接受一个接口作为参数。任何值都会被接口接受，然后由 `TypeOf` 函数进行分析。

### 语法

`variable_type := reflect.TypeOf(variable)`

### 示例

```go
package main

import ("fmt"
"reflect")
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

### 输出

```
{Akansha 17}
type of 'stu' variable: main.student
type of 'stu_type' variable: *reflect.rtype
name of 'stu' variable type: student
```

## 值 (Value)

`reflect` 包有一个方法可以评估变量的值。

### 语法

`value := reflect.ValueOf(variable)`

### 示例

```go
package main

import ("fmt"
"reflect")
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

### 输出

```
{Akansha 17}
value of 'stu' variable: {Akansha 17}
value of 'stu_type' variable: main.student
```

## 种类 (Kind)

Kind 是 `reflect` 包中一个非常不同的方法。类型定义了变量的类型，而“kind”定义了变量类型的源类型。该函数与类型配合使用以获取源，而不是与变量。

### 示例

```go
package main

import ("fmt"
"reflect")
func main(){
    type student struct{
        name string
        age int
    }
    stu := student{"Akansha", 17}
    fmt.Println(stu)
    stu_type := reflect.TypeOf(stu)
    stu_kind := stu_type.Kind()
    fmt.Println("type of 'stu' variable:", stu_type.Name())
    fmt.Println("kind of 'stu_type' variable:", stu_kind)
}
```

### 输出

```
{Akansha 17}
type of 'stu' variable: student
kind of 'stu_type' variable: struct
```

在这里，我们可以看到 student 是 struct 的一种类型。因此，`student` 类型的源类型是 struct。

## NumField()

此方法用于获取结构体包含的字段数量。该方法在 `reflect` 包中定义，适用于结构体或 `reflect.Type`。

### 示例
