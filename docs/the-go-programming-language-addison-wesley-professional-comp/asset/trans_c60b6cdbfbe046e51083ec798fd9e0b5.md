

## 构建约束

某些包可能需要针对特定平台或处理器编译不同版本的代码，例如为了处理底层可移植性问题，或为重要例程提供优化版本。如果文件名包含操作系统或处理器架构名称，如 `net_linux.go` 或 `asm_amd64.s`，那么 `go` 工具仅在针对该目标进行构建时才会编译该文件。被称为*构建标签*的特殊注释提供了更细粒度的控制。例如，如果一个文件在包声明（及其文档注释）之前包含此注释：

```
// +build linux darwin
```

那么 `go build` 仅在为 Linux 或 Mac OS X 构建时才会编译它，而此注释表示永不编译该文件：

```
// +build ignore
```

更多详情，请参阅 `go/build` 包文档中的*构建约束*部分：

```
$ go doc go/build
```

## 10.7.4 为包编写文档

Go 风格强烈建议对包的 API 进行良好的文档记录。每个导出的包成员的声明，以及包声明本身，都应紧跟在一个解释其目的和用法的注释之前。

Go 的*文档注释*始终是完整的句子，第一句通常是一个以被声明的名称开头的摘要。函数参数和其他标识符在提及时不加引号或标记。例如，这是 `fmt.Fprintf` 的文档注释：

```
// Fprintf formats according to a format specifier and writes to w.
// It returns the number of bytes written and any write error encountered.
func Fprintf(w io.Writer, format string, a ...interface{}) (int, error)
```

`Fprintf` 的格式化细节在与 `fmt` 包本身关联的文档注释中进行了解释。紧邻 `package` 声明之前的注释被视为整个包的文档注释。包文档注释有且只能有一个，尽管它可以出现在任意文件中。较长的包注释可能需要一个单独的文件；`fmt` 包的注释超过 300 行。该文件通常命名为 `doc.go`。

良好的文档不必冗长，文档也不能替代简洁性。事实上，Go 的约定倾向于在文档中保持简洁和简单，正如在所有事情上一样，因为文档像代码一样也需要维护。许多声明只需一个措辞得当的句子即可解释清楚，如果行为确实显而易见，则无需注释。

全书中，在篇幅允许的情况下，我们为许多声明前面加上了文档注释，但浏览标准库时你会找到更好的示例。两个工具可以帮助你做到这一点。

`go doc` 工具打印命令行指定实体的声明及其文档注释，该实体可以是一个包：

```
$ go doc time
package time // import "time"

Package time provides functionality for measuring and displaying time.

const Nanosecond Duration = 1 ...
func After(d Duration) <-chan Time
func Sleep(d Duration)
func Since(t Time) Duration
func Now() Time
type Duration int64
type Time struct { ... }
...many more...
```

或一个包成员：

```
$ go doc time.Since
func Since(t Time) Duration

    Since returns the time elapsed since t.
    It is shorthand for time.Now().Sub(t).
```

或一个方法：

```
$ go doc time.Duration.Seconds
func (d Duration) Seconds() float64

    Seconds returns the duration as a floating-point number of seconds.
```

该工具不需要完整的导入路径或正确的标识符大小写。此命令打印 `encoding/json` 包中 `(*json.Decoder).Decode` 的文档：

```
$ go doc json.decode
func (dec *Decoder) Decode(v interface{}) error

    Decode reads the next JSON-encoded value from its input and stores
    it in the value pointed to by v.
```

第二个工具，命名为 `godoc`（容易混淆），提供交叉链接的 HTML 页面，这些页面提供与 `go doc` 相同的信息以及更多内容。位于 `https://golang.org/pkg` 的 `godoc` 服务器涵盖了标准库。[图 10.1](#part0103.html#id-figures-godoc-time) 展示了 `time` 包的文档，在 [11.6 节](#part0110.html#id-examplefunctions) 中我们将看到 `godoc` 对示例程序的交互式展示。位于 `https://godoc.org` 的 `godoc` 服务器拥有数千个开源包的可搜索索引。

![The time package in godoc.](images/00037.jpeg)

**图 10.1.** `godoc` 中的 `time` 包。

如果你想浏览自己的包，也可以在工作区中运行一个 `godoc` 实例。在运行此命令时，在浏览器中访问 `http://localhost:8000/pkg`：

```
$ godoc -http :8000
```

其 `-analysis=type` 和 `-analysis=pointer` 标志利用高级静态分析的结果增强文档和源代码。

## 10.7.5 内部包

包是 Go 程序中封装的最重要机制。未导出的标识符仅在同一个包内可见，而导出的标识符对全世界可见。

不过，有时中间地带会很有帮助，即一种定义标识符的方式，使其仅对一小组受信任的包可见，而不对所有人可见。例如，当我们将一个大包拆分为更易管理的部分时，可能不想向其他包暴露这些部分之间的接口。或者我们可能想在项目的几个包之间共享工具函数，而不想更广泛地暴露它们。又或者我们只是想通过将一个新包“试用”给有限的客户端集合，来在过早承诺其 API 之前进行试验。

为了满足这些需求，如果包的导入路径包含名为 `internal` 的路径段，`go build` 工具会对该包进行特殊处理。此类包称为*内部包*。内部包只能被位于 `internal` 目录父目录为根的树内的另一个包导入。例如，给定下面的包，`net/http/internal/chunked` 可以从 `net/http/httputil` 或 `net/http` 导入，但不能从 `net/url` 导入。然而，`net/url` 可以导入 `net/http/httputil`。

```
net/http
net/http/internal/chunked
net/http/httputil
net/url
```

## 10.7.6 查询包

`go list` 工具报告可用包的信息。在最简单的形式下，`go list` 测试包是否存在于工作区中，如果存在则打印其导入路径：

```
$ go list github.com/go-sql-driver/mysql
github.com/go-sql-driver/mysql
```

`go list` 的参数可以包含“`...`”通配符，它匹配包导入路径的任意子串。我们可以用它来枚举 Go 工作区内的所有包：

```
$ go list ...
archive/tar
archive/zip
bufio
bytes
cmd/addr2line
cmd/api
...many more...
```

或特定子树内的包：

```
$ go list gopl.io/ch3/...
gopl.io/ch3/basename1
gopl.io/ch3/basename2
gopl.io/ch3/comma
gopl.io/ch3/mandelbrot
gopl.io/ch3/netflag
gopl.io/ch3/printints
gopl.io/ch3/surface
```

或与特定主题相关的包：

```
$ go list ...xml...
encoding/xml
gopl.io/ch7/xmlselect
```

`go list` 命令获取每个包的完整元数据，而不仅仅是导入路径，并以多种格式将此信息提供给用户或其他工具。`-json` 标志使 `go list` 以 JSON 格式打印每个包的完整记录：

