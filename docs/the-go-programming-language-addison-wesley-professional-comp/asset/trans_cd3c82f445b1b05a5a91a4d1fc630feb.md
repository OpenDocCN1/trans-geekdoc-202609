
根据 `Example` 函数的后缀，基于 Web 的文档服务器 `godoc` 会将示例函数与它们所演示的函数或包关联起来，因此 `ExampleIsPalindrome` 会显示在 `IsPalindrome` 函数的文档中，而一个仅名为 `Example` 的示例函数则会与整个 `word` 包关联。

第二个用途是示例作为由 `go test` 运行的可执行测试。如果示例函数包含一个像上面那样的最终 `// Output:` 注释，测试驱动程序将执行该函数，并检查其打印到标准输出的内容是否与注释中的文本匹配。

示例的第三个用途是动手实验。`golang.org` 上的 `godoc` 服务器使用 Go Playground，让用户可以在 Web 浏览器中编辑并运行每个示例函数，如[图 11.4](#part0110.html#id-figures-godoc-example)所示。这通常是对特定函数或语言特性建立直观认识的最快途径。

本书最后两章探讨 `reflect` 和 `unsafe` 包，极少 Go 程序员会经常用到它们——甚至更少的人*需要*用到它们。如果你还没有编写过任何实质性的 Go 程序，现在是个大显身手的好时机。

# 12. 反射

Go 提供了一种机制，可以在运行时更新变量、检查其值、调用其方法，并应用其表示形式固有的操作，而无需在编译时知道其类型。这种机制称为*反射*。反射还允许我们将类型本身视为一等值。

在本章中，我们将探索 Go 的反射特性，了解它们如何增强语言的表达能力，特别是它们对于两个重要 API 的实现至关重要：`fmt` 提供的字符串格式化，以及 `encoding/json` 和 `encoding/xml` 等包提供的协议编码。反射对于我们在第 [4.6 节](#part0041.html#id-template) 中看到的 `text/template` 和 `html/template` 包提供的模板机制也必不可少。然而，反射推理起来很复杂，不适合随意使用，因此尽管这些包是使用反射实现的，但它们自己的 API 并未暴露反射。

## 12.1 为什么需要反射？

有时我们需要编写一个函数，能够统一处理以下类型的值：它们不满足通用接口、没有已知的表示形式，或者在设计该函数时尚不存在——甚至同时满足这三个条件。

一个熟悉的例子是 `fmt.Fprintf` 内部的格式化逻辑，它可以有用地打印任意类型的任意值，甚至包括用户定义的类型。让我们尝试利用已有知识实现一个类似的函数。为简单起见，我们的函数将接受一个参数，并像 `fmt.Sprint` 那样将结果作为字符串返回，所以我们称之为 `Sprint`。

我们从一个类型开关开始，测试参数是否定义了 `String` 方法，如果有则调用它。然后我们添加开关分支，测试值的动态类型是否为各种基本类型——`string`、`int`、`bool` 等——并在每种情况下执行相应的格式化操作。

```
func Sprint(x interface{}) string {
    type stringer interface {
        String() string
    }
    switch x := x.(type) {
    case stringer:
        return x.String()
    case string:
        return x
    case int:
        return strconv.Itoa(x)
    // ...针对 int16、uint32 等类似的分支...
    case bool:
        if x {
            return "true"
        }
        return "false"
    default:
        // array, chan, func, map, pointer, slice, struct
        return "???"
    }
}
```

但我们如何处理其他类型，如 `[]float64`、`map[string][]string` 等？我们可以添加更多分支，但这类类型的数量是无限的。那命名类型呢，比如 `url.Values`？即使类型开关有其底层类型 `map[string][]string` 的分支，它也不会匹配 `url.Values`，因为这两个类型不相同，而且类型开关无法为每个像 `url.Values` 这样的类型包含一个分支，因为那将要求这个库依赖于它的客户端。

如果没有一种方法来检查未知类型值的表示形式，我们很快就会陷入困境。我们需要的是反射。

## 12.2 `reflect.Type` 和 `reflect.Value`

反射由 `reflect` 包提供。它定义了两个重要类型：`Type` 和 `Value`。`Type` 代表一个 Go 类型。它是一个接口，拥有许多用于区分类型和检查其组成部分的方法，比如结构体的字段或函数的参数。`reflect.Type` 的唯一实现是类型描述符（[§7.5](#part0065.html#id-rtype)），它是标识接口值动态类型的同一实体。

`reflect.TypeOf` 函数接受任意 `interface{}` 并将其动态类型作为 `reflect.Type` 返回：

```
t := reflect.TypeOf(3)  // 一个 reflect.Type
fmt.Println(t.String()) // "int"
fmt.Println(t)          // "int"
```

上面的 `TypeOf(3)` 调用将值 `3` 赋给 `interface{}` 参数。回顾第 [7.5 节](#part0065.html#id-interfacevalues)，从具体值到接口类型的赋值会执行隐式接口转换，创建一个包含两个分量的接口值：其*动态类型*是操作数的类型（`int`），其*动态值*是操作数的值（`3`）。

因为 `reflect.TypeOf` 返回接口值的动态类型，它总是返回具体类型。因此，例如，下面的代码打印 `"*os.File"`，而不是 `"io.Writer"`。稍后我们将看到 `reflect.Type` 也能表示接口类型。

```
var w io.Writer = os.Stdout
fmt.Println(reflect.TypeOf(w)) // "*os.File"
```

注意 `reflect.Type` 满足 `fmt.Stringer`。因为打印接口值的动态类型对调试和日志记录很有用，`fmt.Printf` 提供了一个简写 `%T`，它在内部使用 `reflect.TypeOf`：

```
fmt.Printf("%T\n", 3) // "int"
```

`reflect` 包中的另一个重要类型是 `Value`。`reflect.Value` 可以存放任意类型的值。`reflect.ValueOf` 函数接受任意 `interface{}` 并返回一个包含接口动态值的 `reflect.Value`。与 `reflect.TypeOf` 一样，`reflect.ValueOf` 的结果总是具体的，但 `reflect.Value` 也可以存放接口值。

```
v := reflect.ValueOf(3) // 一个 reflect.Value
fmt.Println(v)          // "3"
fmt.Printf("%v\n", v)   // "3"
fmt.Println(v.String()) // 注意："<int Value>"
```

像 `reflect.Type` 一样，`reflect.Value` 也满足 `fmt.Stringer`，但除非 `Value` 存放的是字符串，否则 `String` 方法的结果只会显示类型。相反，应使用 `fmt` 包的 `%v` 动词，它会特殊对待 `reflect.Value`。

在 `Value` 上调用 `Type` 方法会返回其类型作为 `reflect.Type`：

```
t := v.Type()           // 一个 reflect.Type
fmt.Println(t.String()) // "int"
```

`reflect.ValueOf` 的逆操作是 `reflect.Value.Interface` 方法。它返回一个存放与 `reflect.Value` 相同具体值的 `interface{}`：

```
v := reflect.ValueOf(3) // 一个 reflect.Value
x := v.Interface()      // 一个 interface{}
i := x.(int)            // 一个 int
fmt.Printf("%d\n", i)   // "3"
```
