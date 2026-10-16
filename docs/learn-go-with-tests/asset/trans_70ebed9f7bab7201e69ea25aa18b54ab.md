
```
t.Errorf("got %q want %q", got, want)
}
```

- 1. 我们使用 `Post` 的 title 字段作为 URL 路径的一部分，但我们并不希望 URL 中出现空格，因此我们用连字符替换它们。
- 2. 我们为 `PostRenderer` 添加了一个 `RenderIndex` 方法，它同样接受一个 `io.Writer` 和一个 `Post` 切片。

如果我们坚持使用测试后、批准测试的方法，在受控环境中就不会回答这些问题。**测试让我们有思考的空间。**

## 尝试运行测试

```
./renderer_test.go:41:13: undefined: blogrenderer.RenderIndex
```

## 编写最少的代码使测试运行并检查失败的测试输出

```
func (r *PostRenderer) RenderIndex(w io.Writer, posts []Post) er
    return nil
}
```

上述代码应导致以下测试失败

```
=== RUN   TestRender
=== RUN   TestRenderer/it_renders_an_index_of_posts
    renderer_test.go:49:     got "" want "<ol><li><a href=\"/post/hello-world\">Hello World</a></li><li><a href=\"/post/hello-world-2\">Hello World 2</a></li></ol>"
--- FAIL: TestRender (0.00s)
```

因为我们仍然希望在锚点中向用户显示空格。

我们有几个选择。第一个我们将探索的是向模板传递一个函数。

## 向模板传递函数

```go
func (r *PostRenderer) RenderIndex(w io.Writer, posts []Post) er
    indexTemplate := `<ol>{{range .}}<li><a href="/post/{{sanitis

    templ, err := template.New("index").Funcs(template.FuncMap{
        "sanitiseTitle": func(title string) string {
            return strings.ToLower(strings.Replace(title, " ", ".
        },
    }).Parse(indexTemplate)
    if err != nil {
        return err
    }

    if err := templ.Execute(w, posts); err != nil {
        return err
    }

    return nil
}
```

*在解析模板之前* 你可以向模板添加一个 `template.FuncMap`，这允许你定义可以在模板内调用的函数。在这种情况下，我们创建了一个 `sanitiseTitle` 函数，然后在模板中使用 `{{sanitiseTitle .Title}}` 调用它。

这是一个强大的功能，能够向模板发送函数将允许你做一些很酷的事情，但是，应该这样做吗？回到 Mustache 和无逻辑模板的原则，为什么它们提倡无逻辑？**模板中的逻辑有什么问题？**

正如我们所展示的，为了测试我们的模板，我们不得不 *引入一种完全不同类型的测试。*

想象一下你向模板中引入一个函数，该函数具有几种不同的行为排列和边缘情况，**你将如何测试它？** 在当前设计下，你测试这种逻辑的唯一手段是通过 *渲染 HTML 并比较字符串*。这不是一种容易或明智的测试逻辑的方式，绝对不是你想要的 *重要* 业务逻辑的方式。

即使批准测试技术降低了维护这些测试的成本，它们仍然比你编写的大多数单元测试更昂贵。它们仍然对你可能进行的任何微小标记更改敏感，只是我们让管理变得更容易了。我们仍然应该努力设计我们的代码，以便不必围绕模板编写许多测试，并尝试分离关注点，以便任何不需要存在于渲染代码中的逻辑都能得到适当的分离。

受 Mustache 影响的模板引擎赋予你的是一种有用的约束，不要太频繁地试图规避它；**不要逆势而行**。相反，要接受 [视图模型](view models) 的想法，即构建包含你需要渲染的数据的具体类型，以模板语言方便的方式。

这样，你用来生成该数据包的任何重要业务逻辑都可以单独进行单元测试，远离 HTML 和模板的混乱世界。

## 分离关注点

那么我们还能做什么呢？

## 向 `Post` 添加一个方法然后在模板中调用它

我们可以在模板代码中对发送的类型调用方法，因此我们可以向 `Post` 添加一个 `SanitisedTitle` 方法。这将简化

模板，我们也可以轻松地单独对该逻辑进行单元测试，如果我们愿意的话。这可能是最简单的解决方案，尽管不一定是最简单的。

这种方法的一个缺点是这仍然是 *视图* 逻辑。它对系统的其余部分并不有趣，但它现在成为核心域对象的 API 的一部分。随着时间的推移，这种方法可能会导致你创建上帝对象。

## 创建一个专门的视图模型类型，例如 `PostViewModel`，其中包含我们需要的数据

而不是让渲染代码与域对象 `Post` 耦合，它改为接受一个视图模型。

```go
type PostViewModel struct {
    Title, SanitisedTitle, Description, Body string
    Tags []string
}
```

我们代码的调用者将不得不从 `[]Post` 映射到 `[]PostView`，生成 `SanitizedTitle`。保持干净的一种方法是拥有一个 `func NewPostView(p Post) PostView`，它将封装映射。

这将使我们的渲染代码保持无逻辑，并且可能是我们能做到的最严格的关注点分离，但代价是获取帖子渲染的过程稍微复杂一些。

这两个选项都很好，在这种情况下我倾向于选择第一个。随着系统的演进，你应该注意不要添加越来越多的临时方法只是为了让渲染更顺畅；当域对象与视图之间的转换变得更加复杂时，专门的视图模型会更有用。

所以我们可以向 `Post` 添加我们的方法

```go
func (p Post) SanitisedTitle() string {
    return strings.ToLower(strings.Replace(p.Title, " ", "-", -1))
}
```

然后我们可以回到渲染代码中的更简单世界

```
func (r *PostRenderer) RenderIndex(w io.Writer, posts []Post) er
    indexTemplate := `<ol>{{range .}}<li><a href="/post/{{.Sanit:

    templ, err := template.New("index").Parse(indexTemplate)
    if err != nil {
        return err
    }

    if err := templ.Execute(w, posts); err != nil {
        return err
    }

    return nil
}
```

## 重构

最后测试应该通过了。我们现在可以将模板移动到文件中（templates/index.gohtml）并在构造渲染器时一次性加载它。

```
package blogrenderer

import (
    "embed"
    "html/template"
    "io"
)

var (
    //go:embed "templates/*"
    postTemplates embed.FS
)
```

```go
type PostRenderer struct {
    templ *template.Template
}

func NewPostRenderer() (*PostRenderer, error) {
    templ, err := template.ParseFS(postTemplates, "templates/*.g
    if err != nil {
        return nil, err
    }

    return &PostRenderer{templ: templ}, nil
}

func (r *PostRenderer) Render(w io.Writer, p Post) error {
    return r.templ.ExecuteTemplate(w, "blog.gohtml", p)
}

func (r *PostRenderer) RenderIndex(w io.Writer, posts []Post) er
    return r.templ.ExecuteTemplate(w, "index.gohtml", posts)
}
```

通过将多个模板解析到 templ 中，我们现在必须调用 ExecuteTemplate 并指定我们希望适当地渲染哪个模板，但希望你会同意我们得到的代码看起来很棒。

如果有人重命名其中一个模板文件，会引入一个小风险，这会引入一个错误，但我们快速运行的单元测试会很快捕获到这一点。

现在我们对包的 API 设计感到满意，并且通过 TDD 驱动了一些基本行为，让我们更改测试以使用批准。

```go
t.Run("it renders an index of posts", func(t *testing.T) {
    buf := bytes.Buffer{}
    posts := []blogrenderer.Post{{Title: "Hello World"}, {Ti

    if err := postRenderer.RenderIndex(&buf, posts); err != i
        t.Fatal(err)
    }
}
```

```
approvals.VerifyString(t, buf.String())
}
```

记得运行测试使其失败，然后批准更改。

最后我们可以向我们的索引页面添加页面装饰：

```
{{template "top" .}}
<ol>{{range .}}<li><a href="/post/{{.SanitisedTitle}}">{{.Title}}
{{template "bottom" .}}
```

重新运行测试，批准更改，我们就完成了索引！

## 渲染 Markdown 正文

我鼓励你自己尝试，这里是我最终采用的方法。

```
package blogrenderer

import (
    "embed"
    "github.com/gomarkdown/markdown"
    "github.com/gomarkdown/markdown/parser"
    "html/template"
    "io"
)

var (
    //go:embed "templates/*"
    postTemplates embed.FS
)

type PostRenderer struct {
    templ    *template.Template
    mdParser *parser.Parser
}
```
