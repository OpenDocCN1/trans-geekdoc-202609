

此模板首先打印匹配的问题数量，然后打印每个问题的编号、用户、标题和存在天数。在一个动作内部，存在一个当前值的概念，称为“dot”，写作“`.`”，即一个句点。dot 最初指向模板的参数，在本例中将是一个 `github.IssuesSearchResult`。`{{.TotalCount}}` 动作会展开为 `TotalCount` 字段的值，以常规方式打印。`{{range .Items}}` 和 `{{end}}` 动作创建了一个循环，因此它们之间的文本会被多次展开，且 dot 绑定到 `Items` 的连续元素上。

在一个动作内部，`|` 表示法使一个操作的结果成为另一个操作的参数，这类似于 Unix shell 管道。对于 `Title`，第二个操作是 `printf` 函数，它是所有模板中 `fmt.Sprintf` 的内置同义词。对于 `Age`，第二个操作是下面的函数 `daysAgo`，它使用 `time.Since` 将 `CreatedAt` 字段转换为经过的时间：

[点击此处查看代码图片](#ch04_images.html#id114pro01_r)

```
func daysAgo(t time.Time) int {
    return int(time.Since(t).Hours() / 24)
}
```

请注意 `CreatedAt` 的类型是 `time.Time`，而不是 `string`。正如类型可以通过定义某些方法来控制其字符串格式化（**§2.5**），类型也可以定义方法来控制其 JSON 编组和解组行为。`time.Time` 的 JSON 编组值是一个采用标准格式的字符串。

使用模板生成输出是一个两步过程。首先我们必须将模板解析为合适的内部表示，然后在特定输入上执行它。解析只需进行一次。下面的代码创建并解析了上面定义的模板 `templ`。请注意方法调用的链式调用：`template.New` 创建并返回一个模板；`Funcs` 将 `daysAgo` 添加到该模板可访问的函数集中，然后返回该模板；最后，在结果上调用 `Parse`。

[点击此处查看代码图片](#ch04_images.html#id114pro02_r)

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

[点击此处查看代码图片](#ch04_images.html#id114pro03_r)

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

[点击此处查看代码图片](#ch04_images.html#id115pro01_r)

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

[点击此处查看代码图片](#ch04_images.html#id115pro02_r)

gopl.io/ch4/issueshtml

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

[点击此处查看代码图片](#ch04_images.html#id115pro02_01_r)

```
$ go build gopl.io/ch4/issueshtml
$ ./issueshtml repo:golang/go commenter:gopherbot json encoder >issues.html
```

**图 4.4** 显示了该表格在 Web 浏览器中的外观。链接连接到 GitHub 上相应的网页。

![An HTML table of Go project issues relating to JSON encoding.](graphics/issues1.png)

**图 4.4.** 与 JSON 编码相关的 Go 项目问题的 HTML 表格。

**图 4.4** 中的问题没有对 HTML 构成挑战，但我们可以通过标题包含 `&` 和 `<` 等 HTML 元字符的问题更清晰地看到效果。我们为本示例选择了两个这样的问题：

[点击此处查看代码图片](#ch04_images.html#id116pro01_r)

```
$ ./issueshtml repo:golang/go 3133 10535 >issues2.html
```

**图 4.5** 显示了此查询的结果。请注意 `html/template` 包自动对标题进行了 HTML 转义，使它们按字面意思显示。如果我们错误地使用了 `text/template` 包，四字符字符串 `"&lt;"` 将被渲染为小于字符 `'<'`，而字符串 `"<link>"` 将变成一个 `link` 元素，改变 HTML 文档的结构并可能危及其安全性。

我们可以通过使用命名字符串类型 `template.HTML` 而不是 `string`，来抑制包含可信 HTML 数据的字段的这种自动转义行为。对于可信的 JavaScript、CSS 和 URL，也存在类似的命名类型。下面的程序通过使用两个具有相同值但不同类型的字段来演示这一原则：`A` 是一个 string，`B` 是一个 `template.HTML`。

![HTML metacharacters in issue titles are correctly displayed.](graphics/issues2.png)

**图 4.5.** 问题标题中的 HTML 元字符被正确显示。

[点击此处查看代码图片](#ch04_images.html#id117pro01_r)

gopl.io/ch4/autoescape

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

![String values are HTML-escaped but template.HTML values are not.](graphics/autoescape.png)

**图 4.6.** 字符串值被 HTML 转义，但 `template.HTML` 值不会。

我们这里只能展示模板系统最基本的特性。一如既往，欲了解更多信息，请参阅包文档：

