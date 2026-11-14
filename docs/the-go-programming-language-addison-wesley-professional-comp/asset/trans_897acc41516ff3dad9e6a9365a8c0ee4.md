
```
$ go list -json hash
{
    "Dir": "/home/gopher/go/src/hash",
    "ImportPath": "hash",
    "Name": "hash",
    "Doc": "Package hash provides interfaces for hash functions.",
    "Target": "/home/gopher/go/pkg/darwin_amd64/hash.a",
    "Goroot": true,
    "Standard": true,
    "Root": "/home/gopher/go",
    "GoFiles": [
           "hash.go"
    ],
    "Imports": [
        "io"
    ],
    "Deps": [
        "errors",
        "io",
        "runtime",
        "sync",
        "sync/atomic",
        "unsafe"
    ]
}
```

`-f` 标志允许用户使用 `text/template` 包的模板语言（[§4.6](#part0041.html#id-template)）自定义输出格式。以下命令打印 `strconv` 包的传递依赖，以空格分隔：

[点击此处查看代码图像](#part0140_split_029.html#id300pro01_r)

```
$ go list -f '{{join .Deps " "}}' strconv
errors math runtime unicode/utf8 unsafe
```

以下命令打印标准库 `compress` 子树中每个包的直接导入：

[点击此处查看代码图像](#part0140_split_030.html#id300pro02_r)

```
$ go list -f '{{.ImportPath}} -> {{join .Imports " "}}' compress/...
compress/bzip2 -> bufio io sort
compress/flate -> bufio fmt io math sort strconv
compress/gzip -> bufio compress/flate errors fmt hash hash/crc32 io time
compress/lzw -> bufio errors fmt io
compress/zlib -> bufio compress/flate errors fmt hash hash/adler32 io
```

`go list` 命令既适用于一次性交互式查询，也适用于构建和测试自动化脚本。我们将在 [11.2.4 节](#part0106.html#id-externaltestpackages) 再次使用它。更多信息（包括可用字段集及其含义），请参阅 `go help list` 的输出。

在本章中，我们解释了 `go` 工具的所有重要子命令——除了一个。下一章我们将看到如何使用 `go test` 命令测试 Go 程序。

## 练习 10.4

构建一个工具，报告工作区中所有传递依赖于参数指定包的包的集合。提示：你需要运行两次 `go list`，第一次针对初始包，第二次针对所有包。你可能想使用 `encoding/json` 包（[§4.5](#part0040.html#id-json)）解析其 JSON 输出。

# 11. 测试

EDSAC（第一台存储程序计算机）的开发者 Maurice Wilkes 于 1949 年在实验室楼梯上有了一个惊人的感悟。在《计算机先驱回忆录》中，他回忆道：“我充分意识到，我余下的大部分人生将花在寻找自己程序中的错误上。”自那以后，每一位存储程序计算机的程序员都能对 Wilkes 产生共鸣，尽管或许会对他在软件构建困难方面的天真感到一丝哑然。

当然，如今的程序比 Wilkes 时代大得多、复杂得多，人们投入了大量精力开发技术来管理这种复杂性。有两种技术因其有效性而脱颖而出。第一种是部署前对程序进行常规同行评审。第二种是本章的主题：测试。

测试（我们隐含指*自动化*测试）是编写小程序检查被测代码（即*生产*代码）在特定输入下是否表现符合预期的实践，这些输入通常是精心挑选以覆盖特定功能，或随机生成以确保广泛覆盖。

软件测试领域庞大。测试任务占据所有程序员部分时间，也占据部分程序员全部时间。测试文献包括数千本印刷书籍和数百万字的博客文章。在每种主流编程语言中，都有数十个用于测试构建的软件包，有些包含大量理论，该领域似乎吸引了不少拥有邪教般追随者的先知。这几乎足以让程序员相信，要编写有效测试，必须掌握一套全新的技能。

相比之下，Go 的测试方法显得相当**低技术含量**。它依赖一个命令 `go test`，以及一套 `go test` 可运行的测试函数编写约定。这种相对轻量的机制对纯测试有效，并自然扩展到基准测试和用于文档的系统化示例。

实际上，编写测试代码与编写原程序本身差别不大。我们编写专注于任务一部分的短函数。我们必须小心边界条件，思考数据结构，推导合适输入下计算应产生的结果。但这与编写普通 Go 代码是同一过程；无需新符号、约定和工具。

## 11.1 `go test` 工具

`go test` 子命令是针对按特定约定组织的 Go 包的测试驱动器。在包目录中，文件名以 `_test.go` 结尾的文件通常不属于 `go build` 构建的包，但属于 `go test` 构建的包。

在 `*_test.go` 文件中，三种函数受到特殊对待：测试、基准测试和示例。*测试函数*以 `Test` 开头，用于验证程序逻辑的正确行为；`go test` 调用测试函数并报告结果，即 `PASS` 或 `FAIL`。*基准测试函数*以 `Benchmark` 开头，用于衡量某操作的性能；`go test` 报告该操作的平均执行时间。*示例函数*以 `Example` 开头，提供机器可检查的文档。我们将在 [11.2 节](#part0106.html#id-testfunctions) 详细介绍测试，[11.4 节](#part0108.html#id-benchmarkfunctions) 介绍基准测试，[11.6 节](#part0110.html#id-examplefunctions) 介绍示例。

`go test` 工具扫描 `*_test.go` 文件中的这些特殊函数，生成一个临时 `main` 包以适当方式调用它们，构建并运行，报告结果，然后清理。

## 11.2 `Test` 函数

每个测试文件必须导入 `testing` 包。测试函数签名如下：

```
func TestName(t *testing.T) {
    // ...
}
```

测试函数名必须以 `Test` 开头；可选的后缀 `Name` 必须以大写字母开头：

[点击此处查看代码图像](#part0141_split_000.html#id302pro01_r)

```
func TestSin(t *testing.T) { /* ... */ }
func TestCos(t *testing.T) { /* ... */ }
func TestLog(t *testing.T) { /* ... */ }
```

参数 `t` 提供报告测试失败和记录额外信息的方法。让我们定义一个示例包 `gopl.io/ch11/word1`，包含单个函数 `IsPalindrome`，用于判断字符串正读反读是否相同。（若字符串是回文，此实现会测试每个字节两次；稍后我们会改进。）

[点击此处查看代码图像](#part0141_split_001.html#id303pro01_r)

gopl.io/ch11/word1

```
// Package word provides utilities for word games.
package word

// IsPalindrome reports whether s reads the same forward and backward.
// (Our first attempt.)
func IsPalindrome(s string) bool {
    for i := range s {
        if s[i] != s[len(s)-1-i] {
            return false
        }
    }
    return true
}
```

在同一目录下，文件 `word_test.go` 包含两个测试函数 `TestPalindrome` 和 `TestNonPalindrome`。每个函数检查 `IsPalindrome` 对单个输入是否给出正确答案，并使用 `t.Error` 报告失败：

[点击此处查看代码图像](#part0141_split_002.html#id303pro02_r)
