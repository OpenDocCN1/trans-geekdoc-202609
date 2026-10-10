
```
$ go build gopl.io/ch5/findlinks3
$ ./findlinks3 https://golang.org
https://golang.org/
https://golang.org/doc/
https://golang.org/pkg/
https://golang.org/project/
https://code.google.com/p/go-tour/
https://golang.org/doc/code.html
https://www.youtube.com/watch?v=XCsL89YtqCs
http://research.swtch.com/gotour
https://vimeo.com/53221560
...
```

当所有可达的网页都已爬取完毕，或计算机内存耗尽时，该过程结束。

**练习 5.10：** 重写 `topoSort`，改用 map 而非 slice，并去掉初始排序步骤。验证结果虽具有非确定性，但却是有效的拓扑排序。

**练习 5.11：** 线性代数课程的讲师决定将微积分设为先修课程。扩展 `topoSort` 函数以报告环。

**练习 5.12：** `gopl.io/ch5/outline2` ([§5.5](#ebook_split_046.html#id-functionvalues)) 中的 `startElement` 和 `endElement` 函数共享一个全局变量 `depth`。将它们改为共享 `outline` 函数内部局部变量的匿名函数。

**练习 5.13：** 修改 `crawl` 使其在本地创建所发现页面的副本，并根据需要创建目录。不要复制来自不同域名的页面。例如，如果原始页面来自 `golang.org`，则保存该域名下的所有文件，但排除来自 `vimeo.com` 的文件。

**练习 5.14：** 使用 `breadthFirst` 函数探索不同的结构。例如，你可以使用 `topoSort` 示例中的课程依赖关系（有向图）、计算机上的文件系统层级（树），或从市政府网站下载的公交或地铁路线列表（无向图）。

### 5.6.1 警示：捕获迭代变量

在本节中，我们将探讨 Go 语言词法作用域规则的一个陷阱，它可能导致令人惊讶的结果。我们强烈建议你在继续之前先理解这个问题，因为即使是经验丰富的程序员也可能掉进这个陷阱。

考虑一个必须创建一组目录稍后再删除它们的程序。我们可以使用一个函数值的切片来保存清理操作。（为简洁起见，本示例省略了所有错误处理。）

```
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

你可能会疑惑，为什么我们将循环变量 `d` 赋值给循环体内的一个新局部变量 `dir`，而不是像下面这个微妙的错误变体那样直接将循环变量命名为 `dir`：

```
var rmdirs []func()
for _, dir := range tempDirs() {
    os.MkdirAll(dir, 0755)
    rmdirs = append(rmdirs, func() {
        os.RemoveAll(dir) // 注意：错误！
    })
}
```

原因是循环变量作用域规则的后果。在上述程序中，`for` 循环引入了一个声明变量 `dir` 的新词法块。该循环创建的所有函数值都“捕获”并共享同一个变量——一个可寻址的存储位置，而非某一特定时刻的值。`dir` 的值在连续迭代中被更新，因此当清理函数被调用时，`dir` 变量已被现已完成的 `for` 循环多次更新。因此 `dir` 保存的是最后一次迭代的值，结果导致对 `os.RemoveAll` 的所有调用都会尝试删除同一个目录。

通常，为解决此问题而引入的内部变量——示例中的 `dir`——会被赋予与其复制的外部变量完全相同的名称，从而产生外观奇特但至关重要的变量声明，如下所示：

```
for _, dir := range tempDirs() {
    dir := dir // 声明内部 dir，初始化为外部 dir
    // ...
}
```

此风险并非 `range` 形式的 `for` 循环所独有。下面示例中的循环因无意中捕获索引变量 `i` 而遭受相同问题：

```
var rmdirs []func()
dirs := tempDirs()
for i := 0; i < len(dirs); i++ {
    os.MkdirAll(dirs[i], 0755) // 正确
    rmdirs = append(rmdirs, func() {
        os.RemoveAll(dirs[i]) // 注意：错误！
    })
}
```

迭代变量捕获问题最常在使用 `go` 语句 ([第 8 章](#ebook_split_080.html#id-loopinginparallel)) 或 `defer`（稍后将介绍）时遇到，因为两者都可能将函数值的执行推迟到循环结束之后。但该问题并非 `go` 或 `defer` 固有。

## 5.7 变参函数

*变参函数* 是指可以接受不同数量参数调用的函数。最熟悉的例子是 `fmt.Printf` 及其变体。`Printf` 开头需要一个固定参数，随后接受任意数量的后续参数。

要声明变参函数，需在最后一个参数的类型前加上省略号 “`...`”，这表示该函数可以接受任意数量的该类型参数。

```
func sum(vals ...int) int {
    total := 0
    for _, val := range vals {
        total += val
    }
    return total
}
```

上面的 `sum` 函数返回零个或多个 `int` 参数的和。在函数体内，`vals` 的类型是 `[]int` 切片。调用 `sum` 时，可以为其 `vals` 参数提供任意数量的值。

```
fmt.Println(sum())           //  "0"
fmt.Println(sum(3))          //  "3"
fmt.Println(sum(1, 2, 3, 4)) //  "10"
```

隐式地，调用者分配一个数组，将参数复制进去，并将整个数组的切片传递给函数。因此上面的最后一次调用与下面的调用行为相同，后者展示了当参数已在切片中时如何调用变参函数：在最后一个参数后加上省略号。

```
values := []int{1, 2, 3, 4}
fmt.Println(sum(values...)) // "10"
```

虽然 `...int` 参数在函数体内表现得像个切片，但变参函数的类型与带有普通切片参数的函数类型是不同的。

```
func f(...int) {}
func g([]int)  {}

fmt.Printf("%T\n", f) // "func(...int)"
fmt.Printf("%T\n", g) // "func([]int)"
```

变参函数常用于字符串格式化。下面的 `errorf` 函数在开头带上行号构造一个格式化的错误消息。后缀 `f` 是一个广泛遵循的命名约定，用于接受 `Printf` 风格格式字符串的变参函数。

```
func errorf(linenum int, format string, args ...interface{}) {
    fmt.Fprintf(os.Stderr, "Line %d: ", linenum)
    fmt.Fprintf(os.Stderr, format, args...)
    fmt.Fprintln(os.Stderr)
}

linenum, name := 12, "count"
errorf(linenum, "undefined: %s", name) // "Line 12: undefined: count"
```

`interface{}` 类型意味着该函数的最后参数可以接受任意类型的值，我们将在第 7 章 ([Chapter 7](#ebook_split_059.html#id-interfaces)) 中解释。

**练习 5.15：** 编写变参函数 `max` 和 `min`，类似于 `sum`。当这些函数在无参数情况下被调用时该如何处理？编写要求至少一个参数的变体。

**练习 5.16：** 编写 `strings.Join` 的变参版本。
