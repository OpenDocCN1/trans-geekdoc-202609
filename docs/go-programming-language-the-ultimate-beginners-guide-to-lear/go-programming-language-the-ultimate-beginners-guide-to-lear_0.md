# Go 语言编程：逐步学习 Go 编程的终极初学者指南








“编程不在于你知道什么，而在于你能弄懂什么。” - Chris Pine


## 引言
在过去的几年里，你可能听说过一种源自 Google 内部的新编程语言，被称为 Go（作为搜索引擎的搜索术语称为 `Golang`）。通过这本书，我们将尝试识别这种语言、它的优点、缺点以及它与其他语言的不同之处。

本书的第一章将仅作为口头教程，重点介绍该语言与其他语言的差异，并面向具有其他语言编程背景的读者，而后续章节将面向初学者。

## 第一章：通用概念
和往常一样，每十年都有新的工具和技术试图从前辈工具和技术的错误中吸取经验。“为什么需要一种新的编程语言？”或者“为什么他们不能对一种编程语言达成共识？”

编程语言仅仅是你完成任务的工具，每种工具都有其特定的任务。为每个任务选择最合适的工具即可，无需将工具神圣化，或在其周围引发非技术的战争，或是创造阻碍学习的虚幻执念。

来自 Google 内部的一个程序员团队认为是时候改进他们在 `C` 和 `C++` 中的工作流了，他们需要一种新工具来消除这两个工具的缺陷，进一步提高生产力，并符合 Google 计算需求的质量。他们于 2007 年在 Google 内部创立了 Go 编程语言。

该语言的资深团队包括 Unix 的创始人 Ken Thompson（计算机科学家 Ken，他曾任职于贝尔实验室），以及 Robert Pike，他也是贝尔实验室 Unix 团队的成员，`UTF-8` 编码的创始人之一；最后是 Robert Gries way，他是一位 `V8` JavaScript 引擎的工程师。

在了解了 Go 的这段简单历史回顾后，我想泼灭掉你们过度的热情。我不希望你们因为它的创始人或它出自你们喜爱的的公司而热爱这门语言，因此我将开始列出一些你们可能不喜欢 Go 编程语言的地方，即使你们并不喜欢，也可能想停止阅读。我个人更希望看到这个系列书中极少数读者真正知道自己在做什么，而不是在对缺乏认知和知识的情况下对一切新事物盲目热情。

### 你可能不喜欢 Go 编程语言的地方

#### 1. 面向对象并不是
如果你认为它是，那么它没有类（`Class`）或对象（`Objects`）的概念，因此没有继承。然而 Go 携带了一些面向对象编程的优势，例如提供接口（`Interface`）、结构函数和结构体（`Struct`）组合。为什么？语言创始人认为面向对象的语言带有许多缺陷和复杂性，可以通过完全放弃这些概念来消除它们。甚至 Java 程序员自己也更倾向于使用“组合”而非继承；语言创始人认为从技术上来说，面向对象编程通常是一个坏主意。

#### 2. 没有处理异常机制
这可能是由于 Go 缺乏对象编程概念导致的。Go 的错误以相当传统的方式处理，因为错误是作为普通值返回的。然而，Go 允许你通过关键字 `panic`（类似于其他语言中的 `raise` 或 `throw`）为异常情况抛出错误，并通过 `recover` 恢复这些错误。

#### 3. 没有默认或可选参数
在其他编程语言中，你可能习惯于类似 `function list(path, recursive = false)` 的操作。但在 Go 中，你不能将 `recursive = false` 传递，因为函数不接受此类默认/可选参数。语言创始人认为这些行为会导致构建不稳定的 API 或使其行为变得不可预测。

#### 4. 没有重载功能
出于同样的原因，没有方法重载，即你不能重新定义一个同名但签名不同的函数。
```go
func folder(path string) {}
func folder(path string, level int) {}
func folderToLevel(path string, level int) {}
```

#### 5. 没有泛型
其他语言允许你编写泛型函数或类，你不需要声明接受的参数类型，而是留到调用时再确定类型，因此可以轻松创建 `<String>` 或 `<Integer>` 的同时保持相同的函数和操作。Go 没有这种机制，相反，接口（interface）作为一种满足所有类型的通用类型。

#### 6. Go 是一门无聊的语言
因为语言简单且没有新花样，许多人认为它是一门无聊的语言。与其他语言相比，关键字和原始类型较少，它们极大地减少了完成某项任务的多样方法。它甚至没有 `while` 循环，而是限于 `for` 循环。

#### 7. 固执的语言
语言创始人对设计意见非常坚定，不要期望在短期或中期会发生重大的变化。

#### 8. 没有统一的包管理器
Python 有 `pip`，javascript 有 `npm`，其他语言都有流行的包管理器，Go 尚未对如何获取和列出依赖达成共识，最近通过 `Vendoring` 概念来实现。

## 你可能喜欢 Go 编程语言的地方

#### 1. 轻量级线程 (goroutines)
Go 允许你运行并行处理并充分利用 CPU，它所谓的 `goroutine` 比其他语言的线程要轻量得多。你可以通过 `go` 关键字来创建它：
```go
go func () {
    // 在线程中执行的操作
}
```

#### 2. 编译型语言
与 Ruby、Python 和 Java 不同，Go 是编译型语言。它的最终输出是运行所需的可执行文件。

#### 3. 高效语言
因为这门语言是无聊的（简单的），它能让你专注于与工作本身。

#### 4. 多平台支持
同一份软件可以重新组合并在 Windows、Linux 甚至 Mac OS 上运行。

#### 5. 丰富的标准库
尽管缺乏新奇性，它的标准库包含了大多数应用程序所需的许多内容。

#### 6. 默认支持 Unicode
Go 默认支持 Unicode，使用 `rune` 类型而不是 `char` 类型。

#### 7. 内置工具
Go 自带 `godoc` 命令生成文档，通过 `gofmt` 改进格式化，通过 `go test` 进行单元测试。

#### 8. 易的语法和格式化
Go 的格式与 Python 类似，每条指令结尾没有分号（`;`）。你可以指定类型：
```go
age := 35
```
函数可以返回多个值：
```go
func Hello() { return "Hello" }
```

## 第二章：理解 Go
在上一章中，我们了解了 Go 以及与其他语言的区别。在本章中，我们将尝试解释如何安装它以及它的工作空间。

Go 有两种类型的编译器：
1. `gc`: 标准编译器。
2. `gcc`: 支持更多 CPU 架构的编译器。

### 安装 Go
- **Windows 和 Mac OS**: 下载 Go 语言版本。
- **Linux (Ubuntu/Debian)**:
  ```bash
  sudo add-apt-repository ppa:golang
  sudo apt-get update
  sudo apt-get install golang
  ```
- **Arch Linux**:
  ```bash
  sudo pacman -S go
  ```

### 理解工作环境
工作环境 `GOPATH` 指的是文件夹，它应该包含三个子文件夹：
```text
work folder
├── bin  # 可执行文件文件夹
├── pkg  # 库文件夹
└── src  # 代码文件夹
```
由于 Go 是一门语言，假设你会使用版本控制工具（VCS）如 `Git` 或 `Mercurial` 管理代码。

### 配置工作环境
**Linux 或 Mac OS**，将此添加到 `.bashrc` 或 `.zshrc`：
```bash
export GOPATH=$HOME/work
export PATH=$PATH:$GOPATH/bin
```
**Windows**，将 `GOPATH` 添加到环境变量中，并将 `C:\Users\username\work\bin` 添加到 Path 中。

### Bonus：如何制作可执行文件
无需每次浏览，使用 `go get`：
```bash
go get github.com/your-username/hello
```
这会将工具移动到 `GOPATH/bin`。

## 第三章：编写第一个程序
Go 像什么样？如何运行用 Go 编写的程序？

### 欢迎来到
```go
package main

import "fmt"

func main () {
    fmt.Print("Welcome to the world\n")
}
```
将此放在名为 `hello` 的文件夹内名为 `helloworld.go` 的文件中。使用以下命令运行：
```bash
go run helloworld.go
```

### 逐行解释
- `package main`: 每个 Go 文件必须属于一个包。`main` 是编译器视为程序入口的特殊名称。
- `import "fmt"`: 导入用于打印的标准库 `fmt`（格式）。
- `func main()`: 执行开始的主函数。
- `fmt.Print(...)`: 将字符串打印到控制台。`\n` 是换行符。

### HelloHello (返回值)
如果你想看函数如何返回一个值：
```go
package hello

import "fmt"

func HelloHello() string {
    return "Hello world!"
}
```
注意：函数名以大字母（大写）开头使其成为导出的（可以从其他包访问）。

## 第四章：规则
Go 语言的设计旨在通过静态类型和快速编译来轻松完成工作。

### 变量
Go 中的变量在使用前声明。
```go
var age int = 35
age := 35 // 短变量声明
```
字符串是不可变的。

### 数据类型
- `string`: 使用双引号 `""`。使用反引号 ``` ``` 表示包含换行的原始字符串字面量。
- `rune`: `int32` 的别名，代表 Unicode 字符。
- `float64`: 用于小数。
- `complex128`: 用于复数。
- `uint/byte`: 无符号整数。

### 数组与切片
数组在编译时具有固定大小：
```go
var a4 [4]int
var a3 = [3]int{1, 3, 5}
```
切片是动态的且更常用：
```go
s3 = []int{4, 5, 9}
s4 = make([]int, 4)
```
使用内置函数 `append` 向切片添加元素：
```go
s := []int{1, 2, 3}
s = append(s, 4, 5)
```

### 注释
使用 `//` 单行注释，`/* ... */` 多行注释。

## 第六章：创建后端
Go 的开发始于 Google 工程师的一次实验。

### 创建 Web 服务器
我们可以使用 `http` 包启动 Web 服务器。
```go
package main

import (
    "encoding/json"
    "net/http"
    "strings"
)

func main() {
    http.HandleFunc("/weather/", func(w http.ResponseWriter, r *http.Request) {
        // ... 逻辑
        w.Header().Set("Content-Type", "application/json; charset=utf-8")
        json.NewEncoder(w).Encode(data)
    })
    http.ListenAndServe(":8080", nil)
}
```

