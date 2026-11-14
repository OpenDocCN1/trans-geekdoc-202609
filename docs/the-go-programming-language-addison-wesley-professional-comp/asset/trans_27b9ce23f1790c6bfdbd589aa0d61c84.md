

## 练习 5.13

修改 `crawl`，使其创建所发现页面的本地副本，必要时创建目录。不要复制来自不同域名的页面。例如，如果原始页面来自 `golang.org`，则保存该域名下的所有文件，但排除来自 `vimeo.com` 的文件。

## 练习 5.14

使用 `breadthFirst` 函数来探索一种不同的结构。例如，你可以使用 `topoSort` 示例中的课程依赖关系（有向图）、计算机上的文件系统层次结构（树），或从市政府网站下载的公交或地铁路线列表（无向图）。

## 5.6.1 警告：捕获迭代变量

在本节中，我们将探讨 Go 语言词法作用域规则的一个陷阱，它可能导致令人惊讶的结果。我们强烈建议你在继续之前理解这个问题，因为即使是经验丰富的程序员也可能掉进这个陷阱。

考虑一个必须创建一组目录稍后再删除它们的程序。我们可以使用一个函数值切片来保存清理操作。（为简洁起见，本示例省略了所有错误处理。）

```go
var rmdirs []func()
for _, d := range tempDirs() {
    dir := d               // 注意：必要！
    os.MkdirAll(dir, 0755) // 同时创建父目录
    rmdirs = append(rmdirs, func() {
        os.RemoveAll(dir)
    })
}

// ...做一些工作...

for _, rmdir := range rmdirs {
    rmdir() // 清理
}
```

你可能会想，为什么我们将循环变量 `d` 赋值给循环体内的一个新局部变量 `dir`，而不是像下面这个微妙的错误变体那样直接将循环变量命名为 `dir`：

```go
var rmdirs []func()
for _, dir := range tempDirs() {
    os.MkdirAll(dir, 0755)
    rmdirs = append(rmdirs, func() {
        os.RemoveAll(dir) // 注意：错误！
    })
}
```

原因是循环变量作用域规则的后果。在上面的程序中，`for` 循环引入了一个新的词法块，其中声明了变量 `dir`。该循环创建的所有函数值都“捕获”并共享*同一个*变量——一个可寻址的存储位置，而不是该特定时刻的值。`dir` 的值在连续的迭代中被更新，因此当清理函数被调用时，`dir` 变量已被现已完成的 `for` 循环多次更新。因此 `dir` 保存的是最终迭代的值，结果所有对 `os.RemoveAll` 的调用都将尝试删除同一个目录。

为了解决这个问题而引入的内部变量——示例中的 `dir`——通常被赋予与其复制的外部变量完全相同的名称，从而导致看起来奇怪但至关重要的变量声明，如下所示：

```go
for _, dir := range tempDirs() {
    dir := dir // 声明内部 dir，初始化为外部 dir
    // ...
}
```

这种风险并非 `range` 形式的 `for` 循环所独有。下面示例中的循环因无意捕获索引变量 `i` 而遭受相同的问题。

```go
var rmdirs []func()
dirs := tempDirs()
for i := 0; i < len(dirs); i++ {
    os.MkdirAll(dirs[i], 0755) // 正确
    rmdirs = append(rmdirs, func() {
        os.RemoveAll(dirs[i]) // 注意：错误！
    })
}
```

迭代变量捕获问题最常在使用 `go` 语句（第 8 章）或 `defer`（我们马上就会看到）时遇到，因为两者都可能将函数值的执行推迟到循环结束之后。但这个问题并非 `go` 或 `defer` 固有的。

## 5.7 可变参数函数

*可变参数函数* 是指可以接受不同数量参数调用的函数。最熟悉的例子是 `fmt.Printf` 及其变体。`Printf` 在开头需要一个固定参数，之后接受任意数量的后续参数。

要声明一个可变参数函数，最后一个参数的类型前加上省略号 "`...`"，这表示该函数可以接受任意数量的该类型参数。

```go
// gopl.io/ch5/sum
func sum(vals ...int) int {
    total := 0
    for _, val := range vals {
        total += val
    }
    return total
}
```

上面的 `sum` 函数返回零个或多个 `int` 参数的和。在函数体内，`vals` 的类型是 `[]int` 切片。调用 `sum` 时，可以为其 `vals` 参数提供任意数量的值。

```go
fmt.Println(sum())           //  "0"
fmt.Println(sum(3))          //  "3"
fmt.Println(sum(1, 2, 3, 4)) //  "10"
```

隐式地，调用者分配一个数组，将参数复制到其中，并将整个数组的切片传递给函数。因此，上面的最后一次调用与下面的调用行为相同，后者展示了当参数已经在切片中时如何调用可变参数函数：在最后一个参数后加上省略号。

```go
values := []int{1, 2, 3, 4}
fmt.Println(sum(values...)) // "10"
```

虽然 `...int` 参数在函数体内表现得像一个切片，但可变参数函数的类型与带有普通切片参数的函数类型是不同的。

```go
func f(...int) {}
func g([]int)  {}

fmt.Printf("%T\n", f) // "func(...int)"
fmt.Printf("%T\n", g) // "func([]int)"
```

可变参数函数常用于字符串格式化。下面的 `errorf` 函数构造一个带有行号前缀的格式化错误消息。后缀 `f` 是一个广泛遵循的命名约定，用于接受 `Printf` 风格格式字符串的可变参数函数。

```go
func errorf(linenum int, format string, args ...interface{}) {
    fmt.Fprintf(os.Stderr, "Line %d: ", linenum)
    fmt.Fprintf(os.Stderr, format, args...)
    fmt.Fprintln(os.Stderr)
}

linenum, name := 12, "count"
errorf(linenum, "undefined: %s", name) // "Line 12: undefined: count"
```

`interface{}` 类型意味着该函数可以接受任意类型的值作为其最后的参数，我们将在第 7 章解释这一点。

### 练习 5.15

编写可变参数函数 `max` 和 `min`，类似于 `sum`。当这些函数在没有参数的情况下被调用时应该做什么？编写要求至少有一个参数的变体。

### 练习 5.16

编写 `strings.Join` 的可变参数版本。

### 练习 5.17

编写一个可变参数函数 `ElementsByTagName`，给定一个 HTML 节点树和零个或多个名称，返回所有匹配这些名称之一的元素。以下是两个示例调用：

```go
func ElementsByTagName(doc *html.Node, name ...string) []*html.Node

images := ElementsByTagName(doc, "img")
headings := ElementsByTagName(doc, "h1", "h2", "h3", "h4")
```

## 5.8 延迟函数调用

我们的 `findLinks` 示例将 `http.Get` 的输出作为 `html.Parse` 的输入。如果请求的 URL 内容确实是 HTML，这工作得很好，但许多页面包含图像、纯文本和其他文件格式。将此类文件送入 HTML 解析器可能会产生不良影响。

下面的程序获取一个 HTML 文档并打印其标题。`title` 函数检查服务器响应的 `Content-Type` 头部，如果文档不是 HTML 则返回错误。

```go
// gopl.io/ch5/title1
```

