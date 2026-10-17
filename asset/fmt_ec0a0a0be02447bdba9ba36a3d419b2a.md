
# 模板

模板是一个字符串或文件，包含一个或多个用双大括号 `{{...}}` 括起来的部分，称为*动作*。字符串的大部分内容会按原样打印，但动作会触发其他行为。每个动作包含一个模板语言表达式，这是一种简单但强大的表示法，用于打印值、选择结构体字段、调用函数和方法、表达控制流（如 `if`-`else` 语句和 `range` 循环）以及实例化其他模板。下面展示了一个简单的模板字符串：

```
const templ = `{{.TotalCount}} issues:
{{range .Items}}----------------------------------------
Number: {{.Number}}
User:   {{.User.Login}}
Title:  {{.Title | printf "%.64s"}}
Age:    {{.CreatedAt | daysAgo}} days
{{end}}`
```

此模板首先打印匹配的问题数量，然后打印每个问题的编号、用户、标题和存在天数。在一个动作内部，存在一个当前值的概念，称为“dot”，写作“`.`”，即一个句点。dot 最初指向模板的参数，在本例中将是一个 `github.IssuesSearchResult`。`{{.TotalCount}}` 动作会展开为 `TotalCount` 字段的值，以常规方式打印。`{{range .Items}}` 和 `{{end}}` 动作创建了一个循环，因此它们之间的文本会被多次展开，且 dot 绑定到 `Items` 的连续元素上。

在一个动作内部，`|` 表示法使一个操作的结果成为另一个操作的参数，这类似于 Unix shell 管道。对于 `Title`，第二个操作是 `printf` 函数，它是所有模板中 `fmt.Sprintf` 的内置同义词。对于 `Age`，第二个操作是下面的函数 `daysAgo`，它使用 `time.Since` 将 `CreatedAt` 字段转换为经过的时间：

```
func daysAgo(t time.Time) int {
    return int(time.Since(t).Hours() / 24)
}
```

请注意 `CreatedAt` 的类型是 `time.Time`，而不是 `string`。正如类型可以通过定义某些方法来控制其字符串格式化（**§2.5**），类型也可以定义方法来控制其 JSON 编组和解组行为。`time.Time` 的 JSON 编组值是一个采用标准格式的字符串。

使用模板生成输出是一个两步过程。首先我们必须将模板解析为合适的内部表示，然后在特定输入上执行它。解析只需进行一次。下面的代码创建并解析了上面定义的模板 `templ`。请注意方法调用的链式调用：`template.New` 创建并返回一个模板；`Funcs` 将 `daysAgo` 添加到该模板可访问的函数集中，然后返回该模板；最后，在结果上调用 `Parse`。

```
report, err := template.New("report").
    Funcs(template.FuncMap{"daysAgo": daysAgo}).
    Parse(templ)
if err != nil {
    log.Fatal(err)
}
```

因为模板通常在编译时固定，所以解析模板失败表明程序中存在致命 bug。`template.Must` 辅助函数使错误处理更方便：它接受一个模板和一个错误，检查错误是否为 nil（否则 panic），然后返回该模板。我们将在**第 5.9 节**回到这个想法。

一旦模板被创建、用 `daysAgo` 增强、解析并检查通过，我们就可以使用 `github.IssuesSearchResult` 作为数据源，`os.Stdout` 作为目标来执行它：

```
var report = template.Must(template.New("issuelist").
    Funcs(template.FuncMap{"daysAgo": daysAgo}).
    Parse(templ))

func main() {
    result, err := github.SearchIssues(os.Args[1:])
    if err != nil {
        log.Fatal(err)
    }
    if err := report.Execute(os.Stdout, result); err != nil {
        log.Fatal(err)
    }
}
```

该程序打印如下的纯文本报告：

```
$ go build gopl.io/ch4/issuesreport
$ ./issuesreport repo:golang/go is:open json decoder
13 issues:
----------------------------------------
Number: 5680
User:   eaigner
Title:  encoding/json: set key converter on en/decoder
Age:    750 days
----------------------------------------
Number: 6050
User:   gopherbot
Title:  encoding/json: provide tokenizer
Age:    695 days
----------------------------------------
...
```

现在让我们转向 `html/template` 包。它使用与 `text/template` 相同的 API 和表达语言，但增加了针对出现在 HTML、JavaScript、CSS 或 URL 中的字符串进行自动且上下文适当的转义功能。这些功能有助于避免 HTML 生成中一个长期存在的安全问题——*注入攻击*，即攻击者构造一个字符串值（如问题的标题）以包含恶意代码，当模板未正确转义时，这些代码会让他们控制该页面。

下面的模板将问题列表打印为 HTML 表格。请注意不同的导入：

```
import "html/template"

var issueList = template.Must(template.New("issuelist").Parse(`
<h1>{{.TotalCount}} issues</h1>
<table>
<tr style='text-align: left'>
  <th>#</th>
  <th>State</th>
  <th>User</th>
  <th>Title</th>
</tr>
{{range .Items}}
<tr>
  <td><a href='{{.HTMLURL}}'>{{.Number}}</td>
  <td>{{.State}}</td>
  <td><a href='{{.User.HTMLURL}}'>{{.User.Login}}</a></td>
  <td><a href='{{.HTMLURL}}'>{{.Title}}</a></td>
</tr>
{{end}}
</table>
`))
```

下面的命令在一个略有不同的查询结果上执行新模板：

```
$ go build gopl.io/ch4/issueshtml
$ ./issueshtml repo:golang/go commenter:gopherbot json encoder >issues.html
```

**图 4.4** 显示了该表格在 Web 浏览器中的外观。链接连接到 GitHub 上相应的网页。

![An HTML table of Go project issues relating to JSON encoding.](img/issues1.png)

**图 4.4.** 与 JSON 编码相关的 Go 项目问题的 HTML 表格。

**图 4.4** 中的问题没有对 HTML 构成挑战，但我们可以通过标题包含 `&` 和 `<` 等 HTML 元字符的问题更清晰地看到效果。我们为本示例选择了两个这样的问题：

```
$ ./issueshtml repo:golang/go 3133 10535 >issues2.html
```

**图 4.5** 显示了此查询的结果。请注意 `html/template` 包自动对标题进行了 HTML 转义，使它们按字面意思显示。如果我们错误地使用了 `text/template` 包，四字符字符串 `"&lt;"` 将被渲染为小于字符 `'<'`，而字符串 `"<link>"` 将变成一个 `link` 元素，改变 HTML 文档的结构并可能危及其安全性。

我们可以通过使用命名字符串类型 `template.HTML` 而不是 `string`，来抑制包含可信 HTML 数据的字段的这种自动转义行为。对于可信的 JavaScript、CSS 和 URL，也存在类似的命名类型。下面的程序通过使用两个具有相同值但不同类型的字段来演示这一原则：`A` 是一个 string，`B` 是一个 `template.HTML`。

![HTML metacharacters in issue titles are correctly displayed.](img/issues2.png)

**图 4.5.** 问题标题中的 HTML 元字符被正确显示。

```
func main() {
    const templ = `<p>A: {{.A}}</p><p>B: {{.B}}</p>`
    t := template.Must(template.New("escape").Parse(templ))
    var data struct {
        A string        // untrusted plain text
        B template.HTML // trusted HTML
    }
    data.A = "<b>Hello!</b>"
    data.B = "<b>Hello!</b>"
    if err := t.Execute(os.Stdout, data); err != nil {
        log.Fatal(err)
    }
}
```

**图 4.6** 显示了模板输出在浏览器中的样子。我们可以看到 `A` 被转义了，但 `B` 没有。

![String values are HTML-escaped but template.HTML values are not.](img/autoescape.png)

**图 4.6.** 字符串值被 HTML 转义，但 `template.HTML` 值不会。

我们这里只能展示模板系统最基本的特性。一如既往，欲了解更多信息，请参阅包文档：

```
$ go doc text/template
$ go doc html/template
```

**练习 4.14：** 创建一个 Web 服务器，查询一次 GitHub，然后允许导航 Bug 报告、里程碑和用户的列表。

# 5. 函数

函数让我们能够将一系列语句包装成一个单元，该单元可以在程序的其他地方被调用，也许会被多次调用。函数使得将一个大任务分解成更小的部分成为可能，这些部分完全可以由不同时间、不同地点的不同人员编写。函数向其用户隐藏了实现细节。基于所有这些原因，函数是任何编程语言中至关重要的部分。

我们已经见过许多函数了。现在让我们花时间进行更彻底的讨论。本章的贯穿示例是一个 Web 爬虫，即 Web 搜索引擎中负责抓取网页、发现其中的链接、抓取这些链接标识的页面等的组件。Web 爬虫给了我们充足的机会来探索递归、匿名函数、错误处理，以及 Go 语言特有的函数特性。

## 5.1 函数声明

函数声明包含一个名字、一个参数列表、一个可选的结果列表以及一个函数体：

```
func name(parameter-list) (result-list) {
    body
}
```

参数列表指定了函数 `parameters`（形参）的名字和类型，它们是局部变量，其值或 `arguments`（实参）由调用者提供。结果列表指定了函数返回值的类型。如果函数返回一个未命名的结果或没有结果，括号是可选的，通常会省略。完全省略结果列表则声明一个不返回任何值的函数，该函数仅因其副作用而被调用。在 `hypot` 函数中，

```
func hypot(x, y float64) float64 {
    return math.Sqrt(x*x + y*y)
}

fmt.Println(hypot(3, 4)) // "5"
```

`x` 和 `y` 是声明中的 `parameters`（形参），`3` 和 `4` 是调用时的 `arguments`（实参），函数返回一个 `float64` 值。

与 `parameters`（形参）一样，`results`（返回值）也可以被命名。在这种情况下，每个名字声明一个局部变量，并初始化为其类型的零值。

除非执行流程明确无法到达函数末尾（例如函数以调用 `panic` 或不带 `break` 的无限 `for` 循环结束），否则带有结果列表的函数必须以 `return` 语句结尾。

正如我们在 `hypot` 中所见，同类型的连续 `parameters`（形参）或 `results`（返回值）可以合并，使得类型本身只需书写一次。这两个声明是等价的：

```
func f(i, j, k int, s, t string)                { /* ... */ }
func f(i int, j int, k int, s string, t string) { /* ... */ }
```

以下是声明一个具有两个参数和一个结果（均为 `int` 类型）的函数的四种方式。空标识符可用于强调某个参数未被使用。

```
func add(x int, y int) int   { return x + y }
func sub(x, y int) (z int)   { z = x - y; return }
func first(x int, _ int) int { return x }
func zero(int, int) int      { return 0 }

fmt.Printf("%T\n", add)   // "func(int, int) int"
fmt.Printf("%T\n", sub)   // "func(int, int) int"
fmt.Printf("%T\n", first) // "func(int, int) int"
fmt.Printf("%T\n", zero)  // "func(int, int) int"
```

函数的类型有时称为其 `signature`（签名）。如果两个函数具有相同的参数类型序列和相同的结果类型序列，则它们具有相同的类型或签名。`parameters`（形参）和 `results`（返回值）的名字不影响类型，它们是否使用合并形式声明也不影响类型。

每次函数调用都必须按照 `parameters`（形参）声明的顺序，为每个 `parameter`（形参）提供一个实参。Go 没有默认参数值的概念，也没有按名称指定实参的方式，因此 `parameters`（形参）和 `results`（返回值）的名字对调用者来说无关紧要，仅作为文档作用。

`Parameters`（形参）是函数体内的局部变量，其初始值设为调用者提供的 `arguments`（实参）。函数 `parameters`（形参）和命名的 `results`（返回值）是与函数最外层局部变量处于同一词法块中的变量。

`Arguments`（实参）通过*传值*方式传递，因此函数接收到的是每个 `argument`（实参）的副本；对副本的修改不会影响调用者。然而，如果 `argument`（实参）包含某种引用，如 `pointer`（指针）、`slice`（切片）、`map`（映射）、`function`（函数）或 `channel`（通道），则调用者可能会受到函数对 `argument`（实参）间接引用的变量所做修改的影响。

你偶尔可能会遇到没有函数体的函数声明，这表示该函数是用 Go 以外的语言实现的。这种声明定义了函数 `signature`（签名）。

```
package math

func Sin(x float64) float64 // 由汇编语言实现
```

## 5.2 递归

函数可以是*递归的*，即它们可以直接或间接地调用自身。递归是解决许多问题的有力技术，当然对于处理递归数据结构也是必不可少的。在 **第 4.4 节** 中，我们使用了树上的递归来实现一个简单的插入排序。在本节中，我们将再次使用它来处理 HTML 文档。

下面的示例程序使用了一个非标准包 `golang.org/x/net/html`，它提供了一个 HTML 解析器。`golang.org/x/...` 仓库存放由 Go 团队设计和维护的包，用于网络、国际化文本处理、移动平台、图像处理、加密和开发工具等应用。这些包不在标准库中，因为它们仍在开发中，或者因为大多数 Go 程序员很少需要它们。

我们将需要的 `golang.org/x/net/html` API 部分如下所示。函数 `html.Parse` 读取一字节序列，对其进行解析，并返回 HTML 文档树的根节点，即一个 `html.Node`。HTML 有几种节点——文本、注释等——但这里我们只关心形式为 `<name key='value'>` 的*元素*节点。
