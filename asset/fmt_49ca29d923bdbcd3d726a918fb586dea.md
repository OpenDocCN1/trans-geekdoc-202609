
```
String with double quotes:Hello
Go
String with backtick: Hello\n Go
Linebreak in string with backtick: Hello
Go
```

## 将 rune 切片转换为字符串

我们已经理解了如何将字符串转换为 rune。在 Go 中，我们也可以将 rune 切片转换为字符串。在下方的示例中，`rune` 包含几个码点，我们正将其转换为字符串。

**示例：**

```go
func main() {
    rune := []rune{0x4e16, 0x0048, 0x0065, 0x006c, 0x006c}
    str := string(rune)
    fmt.Println("string from rune:", str)
}
```

**输出：**

```
string from rune: 世 Hello
```

## 将字节切片转换为字符串

在下方的示例中，`b` 包含了几个字节，我们正将其转换为字符串。

**示例：**

```go
func main() {
    b := []byte{0xe4, 0xb8, 0x96, 0x48, 0x65, 0x6c, 0x6c, 0x6f, 0x20, 0x47, 0x6f, 0xe4, 0xb8, 0x96}
    str := string(b)
    fmt.Println("string from rune:", str)
}
```

**输出：**

```
string from rune: 世 Hello
```

## 字符串的不可变性

在 Go 中，字符串是不可变的。一旦定义，无法更改其值。它们是只读的。在 Go 语言中，无法更改已定义字符串的值。

**示例：**

```go
func main() {
    str := "Hello Go"
    str[0] = 'h' // error
}
```

## strings 包

在 Golang 中，我们有标准库 `strings` 提供了处理 UTF-8 编码字符串的多个函数。`strings` 包位于 Go 的 `src` ，包含多个 Go 文件。该包提供了多种修改和操作字符串的功能。

要在程序中使用包，首先需要导入它。导入包后，我们可以使用点运算符访问其导出函数。下述部分描述了 `strings` 包提供的大部分函数。为了避免反复访问 `Println` 方法，我们将其赋值给变量 `fp` 并在程序中使用。

## strings 包函数

### 转换字符串的大写和小写

`ToUpper` 函数将字符串中的每个字符转换为大写，而 `ToLower` 函数用于将字符串中的每个字符转换为小写。这两个函数都会对每个字符进行转换，无论它是小写还是大写。如果某个字符已经是大写的并应用了 `ToUpper` 函数，它将保持大写，反之亦然。

**示例：**

```go
package main

import (
    "fmt"
    "strings"
)

func main() {
    fp := fmt.Println
    str := "Hello Go"
    fp("string in uppercase:", strings.ToUpper(str)) // string in uppercase: HELLO GO
    fp("string in lowercase:", strings.ToLower(str)) // string in lowercase: hello go
}
```

### 搜索字符串前缀/后缀

`strings` 包提供了一个名为 `HasPrefix` 的函数，用于检查一个字符串是否以指定的字符串开头。同样，`HasSuffix` 函数检查一个字符串是否以指定的字符串结尾。调用这些函数时会传入两个参数：第一个是要检查前缀/后缀的字符串，第二个是我们要查找的字符串。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Hello Go"
    fp("has prefix He", strings.HasPrefix(str, "He")) // has prefix He true
    fp("has prefix he", strings.HasPrefix(str, "he")) // has prefix he false
    fp("has suffix go", strings.HasSuffix(str, "go")) // has suffix go false
    fp("has suffix Go", strings.HasSuffix(str, "Go")) // has suffix Go true
}
```

### 搜索特定文本

我们有一个名为 `Contains` 的函数，用于检查一个字符串是否存在于另一个字符串中。另一方面，我们还有 `ContainsAny` 函数，如果字符串中的任何一个字符存在于另一个字符串中，它将返回 true。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Hello Go"
    fp("contains ellO", strings.Contains(str, "ellO")) // contains ellO false
    fp("contains o G:", strings.Contains(str, "o G")) // contains o G: true
    fp("containsany welcome:", strings.ContainsAny(str, "welcome")) // containsany welcome: true
    fp("containsany shubh:", strings.ContainsAny(str, "shubh")) // containsany shubh: false
}
```

### 字符串中出现的次数

我们有一个函数可以检查一个特定字符串是否存在于另一个字符串中。`Count` 函数告诉我们特定字符串在另一个字符串中出现的次数。如果指定的字符串不在另一个字符串中，则返回 0。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow And Grow With Golang"
    fp("occurences of Gr:", strings.Count(str, "Gr")) // occurences of Gr: 2
    fp("occurences of welcome:", strings.Count(str, "welcome")) // occurences of welcome: 0
}
```

### 查找字符串的位置

在 `strings` 包中，`Index` 函数用于获取指定字符串在另一个字符串中首次出现的索引。如果指定的字符串不在另一个字符串中，则返回 -1。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow And Grow With Golang"
    fp("position of Gr:", strings.Index(str, "Gr")) // position of Gr: 0
    fp("position of welcome:", strings.Index(str, "welcome")) // position of welcome: -1
}
```

### 查找任意 Unicode 编码点的位置

`IndexAny` 函数在另一个字符串中搜索指定字符串的 Unicode 编码点（字符），并返回第一个出现的 Unicode 编码点的第一个索引。如果另一个字符串中没有出现任何 Unicode 编码点，则返回 -1。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow And Grow With Golang"
    fp("position of first appearing Unicode codepoint in Ground:", strings.IndexAny(str, "Ground")) // position of first appearing Unicode codepoint in Ground: 0
    fp("position of first appearing Unicode codepoint in sub:", strings.IndexAny(str, "sub")) // position of first appearing Unicode codepoint in sub: -1
}
```

### 从后往左查找字符串的位置

由于 `Index` 函数检查的是第一次出现，因此 `LastIndex` 函数检查的是字符串在另一个字符串中最后一次出现的位置。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow And Grow With Golang"
    fp("last position of Gr:", strings.LastIndex(str, "Gr")) // last position of Gr: 9
    fp("last position of welcome:", strings.LastIndex(str, "welcome")) // last position of welcome: -1
}
```

### 从后往左查找任意 Unicode 编码点的位置

`LastIndexAny` 函数的工作原理与 `IndexAny` 相同。区别在于 `IndexAny` 返回第一次出现的位置，而 `LastIndexAny` 如果 Unicode 编码点存在于另一个字符串中，则返回最后一次出现的位置。该函数找到在另一个字符串中最后出现的编码点，然后返回其最后一次出现的索引。如果另一个字符串中不存在 Unicode 编码点，则返回 -1。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow And Grow With Golang"
    fp("position of last appearing Unicode codepoint in Ground:", strings.LastIndexAny(str, "Ground")) // position of last appearing Unicode codepoint in Ground: 23
    fp("position of last appearing Unicode codepoint in sub:", strings.LastIndexAny(str, "sub")) // position of last appearing Unicode codepoint in sub: -1
}
```

### 替换字符串

`Replace` 函数用于将字符串中的旧子串替换为新子串。它接受四个参数：原字符串、旧子串、新子串和替换次数。如果替换次数为 -1，则替换所有匹配项。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow And Grow With Golang"
    fp("replace Gr with Pr:", strings.Replace(str, "Gr", "Pr", 1)) // replace Gr with Pr: Prow And Grow With Golang
    fp("replace all Gr with Pr:", strings.Replace(str, "Gr", "Pr", -1)) // replace all Gr with Pr: Prow And Prow With Polang
}
```

### 分割字符串

`Split` 函数根据分隔符将字符串分割为子串切片。`SplitN` 函数类似，但限制分割的子串数量。`SplitAfter` 和 `SplitAfterN` 在分隔符后分割。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Grow-And-Grow-With-Golang"
    fp("split by -:", strings.Split(str, "-")) // split by -: [Grow And Grow With Golang]
    fp("split by - n=2:", strings.SplitN(str, "-", 2)) // split by - n=2: [Grow And-Grow-With-Golang]
}
```

### 连接字符串

`Join` 函数将字符串切片连接为单个字符串，使用指定的分隔符。

**示例：**

```go
func main() {
    fp := fmt.Println
    strSlice := []string{"Grow", "And", "Grow", "With", "Golang"}
    fp("join with -:", strings.Join(strSlice, "-")) // join with -: Grow-And-Grow-With-Golang
}
```

### 重复字符串

`Repeat` 函数将字符串重复指定次数。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "Go"
    fp("repeat 3 times:", strings.Repeat(str, 3)) // repeat 3 times: GoGoGo
}
```

### 修剪字符串

`Trim` 函数移除字符串首尾指定的字符。`TrimLeft` 和 `TrimRight` 分别移除左侧和右侧的字符。`TrimSpace` 移除首尾的空白字符。`TrimPrefix` 和 `TrimSuffix` 移除指定的前缀和后缀。`TrimFunc`、`TrimLeftFunc` 和 `TrimRightFunc` 使用函数判断是否移除字符。

**示例：**

```go
func main() {
    fp := fmt.Println
    str := "-my-name-is-rahul-"
    fp(strings.Trim(str, "-")) // my-name-is-rahul
    fp(strings.TrimLeft(str, "-")) // my-name-is-rahul-
    fp(strings.TrimRight(str, "-")) // -my-name-is-rahul
    fp(strings.TrimFunc(str, func(c rune) bool {
        return c >= 23 && c <= 50
    })) // my-name-is-rahul
    fp(strings.TrimLeftFunc(str, func(c rune) bool {
        return c >= 23 && c <= 50
    })) // my-name-is-rahul-
    fp(strings.TrimRightFunc(str, func(c rune) bool {
        return c >= 23 && c <= 50
    })) // -my-name-is-rahul
    fp(strings.TrimPrefix(str, "-my-")) // name-is-rahul-
    fp(strings.TrimSuffix(str, "-rahul-")) // -my-name-is
    fp(strings.TrimSuffix(str, "welcome")) // -my-name-is-rahul- (未改变)

    str = " -my-name-is-rahul- "
    fp(strings.TrimSpace(str)) // -my-name-is-rahul-
}
```

## 结论

在本章中，我们了解字符串在 Go 中是如何作为代码点运行的。Golang 提供了各种函数来分析和修改字符串。我们已经看到了多种从其他数据类型获取字符串的方法。`rune` 数据类型在 Golang 中是一个新概念。Golang 提供了丰富的库，而 `strings` 包就是其中之一，它为字符串提供了许多功能。在下一章中，我们将深入讨论另一种名为 `pointer`（指针）的数据类型。

## 问题

1. Go 语言字符串声明与其他语言有何不同？

2. Go 中的 `rune` 是什么？

3. 我们如何从 `rune` 获取字符串？

4. 使用哪个函数可以找到一个字符串在另一个字符串中的索引？

5. 如何在 Go 中访问 `strings` 包的导出函数？

6. Go 中的字符串是如何实现不可变的？

# 第 11 章：指针

在本章中，我们将讨论 `pointers`（指针）数据类型，它在提高程序运行速度和减少内存占用方面起着重要作用。`pointer` 允许数据共享，并使变量的默认值（空或零值）与未定义值之间产生区别。让我们来看并理解 Go 中的指针概念。

## 结构

在本章中，我们将讨论以下主题：

* 指针简介
* 指针的必要性
* 声明指针
* 初始化指针
* 指针解引用
* 操作指针
* 使用 `new` 创建指针
* 嵌套指针
* 指针数组
* 将指针传递给函数

## 目标

学习本章后，你将能够：

* 优化你的代码
* 在 Go 程序中使用动态内存分配
* 获取内存中变量的地址
* 通过指针对变量进行许多操作
* 构建复杂的数据结构

## 引言

`pointers`（指针）是 Go 语言中的核心概念。指针是派生数据类型之一。当我们声明变量时，Go 编译器会根据变量的类型在系统内存中分配一些空间。该内存空间有一个唯一的地址来识别该变量。该地址由十六进制值表示。指针通过存储系统内存中任何变量的地址来引用数据。它通过直接从内存访问数据，使得数据处理任务变得简单。指针的类型与其存储的地址的变量类型相同。因此，整数类型的指针持有整数类型变量的地址。通过访问值来引用指针，这被称为指针解引用。

## 指针的必要性

指针是一个存储另一个变量地址的变量。现在的问题是，我们为什么要使用它？虽然在大型应用程序中我们可以通过名称访问变量，但这个过程会在系统内存中占用额外的空间。如果我们需要通过函数传递大量数据，那么我们可以只传递它的地址而不是传递完整数据。指针用于分配和释放内存空间。因此，指针可以极大地利用内存。此外，使用指针的执行速度更快，因为通过内存位置直接访问数据。因此，我们可以得出以下点作为指针的优点：

* 更快的执行速度
* 内存利用
* 易于变量变量
* 动态内存分配

由于 Go 是一种并发语言，我们可以借助 `Goroutine` 和 `channels` 同时运行多个任务。在使用指针时，多个进程读取数据是容易的，但使用地址修改数据是非常危险的。Go 提供了指针支持，但指针的使用完全掌握在我们手中。对于 Go 语言来说，明智地使用指针是必要的。

## 声明指针

由于指针是一个变量，声明指针的方法与其他变量相同。在这里，星号（`*`）是区别所在。它告诉编译器该变量是一个指针。要声明指针，我们在指针变量的类型之前使用 `*`。

**语法：**

`var name_of_pointer *type_of_pointer`

**示例：**

```go
func main() {
    var pointerv *int
    fmt.Println("Default value of pointer is:", pointerv) // 指针的默认值是: <nil>
}
```

这里没有给指针赋值。因此，其默认值是整数类型指针的 `nil`。任何未初始化的指针都有一个零值，在这里是 `nil`。

## 初始化指针

`Initializing pointers`（初始化指针）意味着将变量的地址赋值给指针。在这里，地址由 `&` 运算符表示。我们将使用两个操作符：`*` 用于声明指针或访问特定地址的值，`&` 用于获取特定变量的地址。

**语法：**

`name_of_pointer = &name_of_variable`

**示例：**

```go
func main() {
    a := 10
    var pointerv *int
    pointerv = &a
    // 1
    fmt.Println(pointerv)  // 0x1184e068
    // 2
    fmt.Println(&pointerv) // 0x1183e0f
}
```

在上面的示例中，`statement1` 显示变量的地址，`statement2` 显示内存中指针的地址。

## 指针解引用

获取指针所指向的地址中存储的值被称为指针解引用。这使用 `*` 运算符。

**示例：**

```go
func main() {
    a := 10
    var pointerv *int
    pointerv = &a
    fmt.Println(pointerv)  // 0x1184e068
    fmt.Println(*pointerv) // 10
}
```

## 操作指针
