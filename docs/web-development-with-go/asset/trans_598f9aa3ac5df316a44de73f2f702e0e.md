

## 4.4 创建模板

这有助于确保你的 Web 应用程序是安全的。

让我们创建一个主函数来执行一个非常简单的模板，这样我们就可以看到它的运行效果。首先，我们需要为此应用程序创建一个目录。我们将创建一个名为 `exp` 的目录，表示这是一个用于测试各项内容的实验性目录。

列表 4.2：创建 `exp` 目录。

```bash
# 你应该从 lenslocked.com目录开始
$ cd $GOPATH/src/lenslocked.com
$ mkdir exp
$ cd exp
```

接下来，我们需要在 `exp` 目录中创建 `hello.gohtml` 文件，并将列表 4.3 中的代码添加到其中。

列表 4.3：`hello.gohtml` 的初始内容。

```html
<h1>Hello, {{.Name}}!</h1>
```

框 4.2：`.gohtml` 扩展名是可选的。

`gohtml` 扩展名通常被编辑器用来表示你想对 Go HTML 模板使用语法高亮。我相信 Atom（`go-plus`）和 Sublime Text（`GoSublime`）中的这两个包默认情况下都能识别这一点，因此这是我在本书中选择的文件类型。

这是我们的第一个模板，通过它我们本质上是在说，想要创建一个 HTML 文件，其中包含一个内容为 `Hello, {{.Name}}!` 的标题，并且我们希望将 `{{.Name}}` 部分替换为变量 `Name` 中的任何内容。

让我们创建一个 Go 文件来运行这个模板，这样你就可以看到它的效果了。在 `exp` 目录下创建一个名为 `main.go` 的文件，并将列表 4.4 中的代码添加到其中。

列表 4.4：`main.go` 的初始内容
```go
package main

import (
	"html/template"
	"os"
)

func main() {
	t, err := template.ParseFiles("hello.gohtml")
	if err != nil {
		panic(err)
	}

	data := struct {
		Name string
	}{"John Smith"}

	err = t.Execute(os.Stdout, data)
	if err != nil {
		panic(err)
	}
}
```

在列表 4.4 的 `main` 函数中，我们首先使用 `html/template` 包的 `ParseFiles` 函数来解析 `hello.gohtml` 模板文件。函数会打开模板文件并尝试对其进行验证。如果一切顺利，你将收到一个*模板和一个 nil 错误（error）*，否则你将得到一个 nil 模板和一个错误。

框 4.3：自动导入的潜在问题。

如果你正在使用插件来自动为你导入包，你可能需要花一点时间确保它导入了正确的模板包。

Go 的标准库同时提供了 `text/template` 和 `html/template` 包，并且两者的用法几乎完全相同，因此自动导入器很难判断你意图使用哪一个。

因此，在编写了使用模板的代码后，验证你正在使用预期的模板包始终是一个好主意。在这种情况下，我们希望导入 `html/template` 包。

在调用 `ParseFiles` 后，我们检查是否返回了错误。如果存在错误，我们执行 `panic`。否则，我们继续执行程序，因为我们知道通过变量 `t` 引用了一个有效的模板。

接下来，我们创建 `data` 变量，这是一个带有 `Name` 字段的匿名结构体。当我们实例化 `data` 时，我们将 `Name` 字段设置为“John Smith”。

最后，我们执行之前创建的模板，并传入两个参数：

1. 我们想要写入模板输出的位置
2. 执行模板时要使用的数据

在我们的案例中，我们希望将模板输出写入 `Stdout`，即你的终端窗口。这是 `fmt.Println` 等函数默认写入所在的地方，它是由 Go 标准库中的 `os` 包提供的。

我们还想为模板提供渲染模板时需要的数据。在列表 4.3 中，我们使用 `{{ .Name }}` 这一行代码来动态渲染名称，因此我们需要传递一个带有 `Name` 字段的数据结构。我们刚刚创建的变量 `data` 已经将该字段设置为“John Smith”，所以当我们将其提供给模板时，我们在最终输出中看到了“John Smith”这个名字。

让我们运行代码来验证这一切吧。

```bash
# 在 exp 目录内执行此操作
$ go run main.go
<h1>Hello, John Smith!</h1>
```

框 4.4：模板路径是相对的。

当你处理模板时，需要注意的是，访问模板的文件路径相对于你运行代码的位置。

在这个示例中，我们在与 `main.go` 文件相同的文件夹中访问名为 `hello.gohtml` 的文件，因此不需要包含目录。如果我们相反移动到包含 `lenslocked.com` 的目录（例如在终端执行 `cd ..`）并使用 `go run lenslocked.com/main.go` 运行代码，将会报错，因为该文件夹中没有名为 `hello.gohtml` 的文件。它在 `lenslocked.com` 文件夹中。

目前这意味着你在运行程序时需要位于 `lenslocked.com` 文件夹中，否则可能会看到错误。

如果你在终端中看到了一些 HTML 输出，说明你成功创建了第一个模板！

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

[已完成](https://book.usegolang.com/4.4)
[更改](https://book.usegolang.com/4.4-diff)

## 4.5 上下文编码

我之前提到过，Go 的 `html/template` 包根据代码的上下文进行编码。虽然在本书的这个阶段我们并不真的需要担心这一点，但我想演示我的意思，以便你理解为什么我们使用 `html/template` 包而不是其他东西。

为了演示这一点，我们正在更新 `hello.gohtml` 模板中使用的 `Name` 属性，将其更新为不安全直接渲染的内容，例如一个带有 JavaScript alert 的 script 标签。

打开 `main.go` 并 `Name` 字段更新为列表 4.5 所示的 script 标签。

列表 4.5：使用不安全的字符串。

```go
func main() {
  // ... 这部分保持不变
  data := struct {
    Name string
  }{"<script>alert('Howdy!');</script>"}
  // ... 这部分保持不变
}
```

现在运行你的程序。

```bash
# 在 exp 目录内执行此操作
$ go run main.go
<h1>Hello, &lt;script&gt;alert('Howdy!');&lt;/script&gt;</h1>
```

当你运行程序时，`html/template` 包会查看你想打印的每个变量并根据其位置调整每个的值。在这个示例中，我们在 HTML 部分使用了该变量，因此 `html/template` 包将 `<` 字符替换为 `&lt;`。这是为了确保当在浏览器中查看模板时，你会看到 `<` 字符，并且浏览器不会尝试将其解释为 HTML 标签。

虽然当你看到输出时这可能没有意义，但如果你通过浏览器查看输出，它就有意义了。复制你程序的输出并将其插入到名为 `test.html` 的文件中，然后在浏览器中打开该文件。你看到了什么？

![](img/d6be51afcf11b16bf9724d05fb9e635_69_0.png)

图 4.1：test.html 的

你应该看到一个像图 4.1 那样的页面。当你的浏览器看到文本 `&lt;` 时，它会渲染小于符号（<）。

框 4.5：想了解更多 HTML 代码吗？

如果你对学习更多 HTML 符号和字符代码感兴趣，可以搜索“HTML character codes”。

有很多网站列出了所有的 . . .; 样式代码，你可以通过编辑之前创建的 `test.html` 文件来测试每种代码。

这种现象发生是因为，否则浏览器无法判断你是想让字符串 `<script>` 在屏幕上显示相同的文本，还是想让它被视为 HTML 代码。结果是浏览器会将 `<` 内部的任何文本视为 HTML 元素。如果你想在网站上显示 `<` 字符，你需要使用 `&lt;` 字符串，浏览器在渲染页面时将其显示为 `<`。

如果 `html/template` 包没有编码 `<` 字符，你的网页将把该名称解析为实际的脚本，并渲染出像图 4.2 那样令人烦的 alert 警告消息。

![](img/d6be51afcf11b16bf9724d05fb9e635_70_0.png)

图 4.2：一个烦人的 JavaScript 警告框

