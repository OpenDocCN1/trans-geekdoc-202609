
`csrf` 包还为我们提供了一个为 HTML 表单生成令牌的辅助函数。该包的文档随后解释了推荐的向 HTML 表 form 提供此类令牌的方法：将其作为数据字段传递到模板中。例如，我们可能会将此字段添加到 `views.Data` 类型中。

我们将采取一种稍微不同的方法，而是将其添加为模板函数。这种方法相比推荐方法的主要优势是，我们可以在任何模板中访问它，即使没有向模板传递任何数据。这使得生成表单变得更容易，而不必担心 CSRF 令牌是否作为数据提供给表单。

为了实现这一点，我们将查看 `template` 包中的 `Funcs` 函数¹。通过它，我们可以引入在模板内部可用的新函数。

我们将该函数命名为 `csrfField`，并从开始将其添加到我们需要的所有模板中。我们假设调用 `csrfField` 函数将返回生成 CSRF 令牌隐藏输入字段所需的所有内容；也就是说，我们假设它返回的是我们需要的整个 HTML 块内容，而不仅仅是一个令牌。

```go
$ atom views/galleries/edit.gohtml
```

在编辑画廊模板中，我们需要为创建的每个表单添加此函数调用。这四个模板均如下所示，但重要的是，我们只直接在 `form` 标签之后添加 `csrfField` 函数调用。其他所有内容保持不变。

```html
{{"editGalleryForm"}}
<form action="/galleries/{{.ID}}/update" method="POST" class="form-horizontal">
<!--
  此行将返回：
  <input type="hidden">
with the CSRF token as its value.
-->
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
{{define deleteGalleryForm}}
<form action="galleries/{{.ID}}/delete" method="POST" class="form-horizontal">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
{{define uploadImageForm}}
<form action="galleries/{{.ID}}/images" method="POST" enctype="multipart/form-data" class="form-horizontal">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
{{define deleteImageForm}}
<form action="galleries/{{.GalleryID}}/images/{{.Filename}}/delete" method="POST">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
```

接下来是新的画廊表单。

```go
$ atom views/galleries/new.gohtml
```

```html
{{define galleryForm}}
<form action="/galleries" method="POST">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
```

然后是登录表单。

```go
$ atom views/users/login.gohtml
```

```html
{{define "loginForm"}}
<form action="/login" method="POST">
{{csrfField}}
<!--... remains unchanged -->
</form>
{{end}}
```

最后是注册表单。

```go
$ atom views/users/signup.gohtml
```

```html
{{define "signupForm"}}
<form action="/signup" method="POST">
{{csrfField}}
</form>
{{end}}
```

如果我们在此处尝试重启服务器，我们将看到类似的错误信息：

```
function "csrfField" not defined
```

每当我们第一次解析模板时，它们会检查所有函数是否都已定义。此时我们的 `csrfField` 函数尚未定义，但在处理 Web 请求之前我们无法真正定义它。这是因为我们需要读取用户的 CSRF 令牌，以便知道在表单中包含哪个。

为了处理这个问题，我们在解析模板之前创建一个 `csrfField` 函数的存根版本，稍后在获取 Web 请求时，在执行之前更新模板函数。

注意：这种技术稍微高级，但一旦你完全理解了它，它将非常有用，因为它允许我们创建带有用户数据的模板函数。例如，我们可以将 `views.Data` 类型的 `.User` 字段替换为 `isLoggedIn` 或 `isAdmin` 等函数，并在任何模板中使用它们，即使没有提供 `.User` 字段。

```go
$ atom views/view.go
```

我们将从新的导入开始。

```go
import (
    "errors"
    "github.com/gorilla/csrf"
)
```

之后，我们将更新 `NewView` 函数，使其提供 `csrfFieldError` 存根。如果它在没有被替换的情况下提供给我们，将导致错误，但我们在调用 `views` 的 `Render` 方法时会替换它。

```go
func NewView(layout string, files ...string) +View {
    addTemplatePath(files)
    addTemplateFiles(files)
    files = append(files, layoutFiles)
    // 我们正在给出如何创建一个可以添加函数的模板
    // New("")
    // 最后传递文件作为模板的一部分进行解析
    // 就像我们之前做的那样
    t, err := template.New("layout").Funcs(template.FuncMap{
        csrfFieldError: func() error {
            // 如果此函数在没有被替换为正确实现的情况下被调用
            // 作为第二个参数返回错误会导致模板包
            // 在执行时返回错误。
            return errors.New("csrfFieldError is not implemented")
        },
        // 一旦我们有了带有函数的模板，我们将传递文件
        // 进行解析，就像我们之前做的那样。
    }).ParseFiles(files...)
    if err != nil {
```

## 16.3. CSRF保护

```go
panic(err)
}
return &View{
    Template: t,
    Layout: layout,
}
```

接下来，我们需要在最终渲染视图时，将此 `csrf` 函数替换为实际实现。

```go
func (v *View) Render(w http.ResponseWriter, r *http.Request, data interface{}) {
    // ... 用于设置 header 和 Data 的代码保持不变
    vd.User = context.User(r.Context())
    var buf bytes.Buffer
    // 我们需要使用当前的 http 请求创建 csrf。
    csrffield := csrf.IntegerField(r)
    tpl := v.Template.Funcs(template.FuncMap{
        // 我们也可以更改你函数的返回类型，因为我们不再
        // 需要再担心错误了。
        "csrfField": func() template.HTML {
            // 我们可以创建这个闭包，为任何需要
            // 访问它的模板返回 csrf。
            return csrffield
        },
    })
    // 然后我们像以前一样继续执行模板。
    err := tpl.ExecuteTemplate(&buf, v.Layout, vd)
    if err != nil {
        http.Error(w, "发生了一些错误。如果问题 " +
            "持续存在，请邮件至 support@lenslocked.com",
            http.StatusInternalServerError)
        return
    }
    io.Copy(w, &buf)
}
```

在继续之前，还有一个最后一个问题需要解决。我们用于解析表单的 gorilla 包默认设置为：如果提交了任何我们未尝试解码的格式的键，就会报错。对于非 CSRF 令牌来说，这不是糟糕糟糕默认设置，但现在我们已经引入了它们

# 第 16 章 部署到生产环境

这就有问题了，因为我们在表单中添加了一个永远不想手动解码的新键，这会导致 `schema.Decoder` 在解码表单时报错。

要更改此设置，我们将调用 `IgnoreUnknownKeys` 函数，它会告诉解码器直接忽略我们没有要求它解码的键。

```go
$ controllers/helpers.go
```

```go
func parseForm(r *http.Request, dst interface{}) error {
  if err := r.ParseForm(); err != nil {
    return err
  }
  dec := schema.NewDecoder()
  // 调用 IgnoreUnknownKeys 函数告诉 schema 的解码器
  // 忽略 CSRF 令牌键
  if err := dec.Decode(dst, r.PostForm); err != nil {
    return err
  }
  return nil
}
```

这是为了实现 CSRF 保护。重启你的服务器并验证你的表单是否仍然正常工作。务必刷新任何已打开的页面，否则 HTML 将不会更新，你的 HTML 中将没有 CSRF 字段。你也可以检查服务器生成的 HTML 源代码，以验证 CSRF 输入字段是否已添加到每个表单中。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

> ²http://www.gorillatoolkit.org/pkg/schema#Decoder.IgnoreUnknownKeys

## 16.4. 限制静态资源的中间件

已完成 - book.usegolang.com/16.3

已更改 - book.usegolang.com/16.3-diff

## 16.4 限制静态资源的中间件

我们的 `Users` 中间件目前每次用户请求公共图像或资源时都会检查用户是否已登录。虽然如果我们有私有图像，这可能有用，但我们并没有，这最终导致了额外的数据库查询。防止这种情况的一种简单方法是更新中间件，使其不在特定路由上运行。

```go
$ atom middleware/require_user.go
```

我们将获取网络请求的当前路径并检查它是否以 `/assets/` 或 `/images/` 开头。如果是，我们将调用下一个中间件并返回，而不查找用户。

```go
import (
	// 添加此导入
	"strings"
)
func (u *User) ApplyFn(next http.HandlerFunc) http.HandlerFunc {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		path := r.URL.Path
		// 如果用户请求静态资源或图像
		// 我们不需要查找当前用户，所以跳过
		if strings.HasPrefix(path, "/assets/") ||
			strings.HasPrefix(path, "/images/") {
			next(w, r)
			return
		}
		// 其他所有保持不变
	})
}
```

# 第 16 章 部署到生产环境

注意：处理此问题的另一种方法是仅应用需要的中间件路由，就像我们对 `RequireUser` 中间件所做的那样。这会导致更多的代码，但减少了我们的中间件和路由之间的耦合性。在你自己的应用程序中，你必须决定哪种路由最合理。

重启你的服务器并访问带有图像的页面，例如你创建的画廊。在进行这些更改之前，你可能看到许多这样的日志信息：

```sql
SELECT * FROM "users" WHERE ...
```

现在我们已经更新了代码，你应该会发现这些信息出现的频率降低了，因为我们的应用程序不再查询数据库。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/16.4

已更改 - book.usegolang.com/16.4-diff

## 16.5 修复 bug

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

### 16.5.1 URL 编码路径

我们需要查看的第一个 bug 是可能发生的。如果用户上传了包含某些字符的图像，我们的应用程序目前将无法正确处理它。

我们可以在创建一个包含斜杠名称的文件时看到这一点。

```
# 某些操作系统可能不喜欢这个
/asfjalf/_!&?.jpg
```

这个文件名之所以有趣，是因为它其中包含特殊字符。因此，用户不太可能拥有带有斜杠的文件名，但他们可能有问号或其他字符。这些字符在 URL 路径中具有特殊含义，因此我们需要在创建 `<img>` HTML 标签的 `src` 属性之前对它们进行编码。

我们将首先更新在我们的 `Image` 类型上定义的 `Path` 函数。

## 16.5 修复 BUGS

```go
$ atom models/images.go
```

为了创建一个正确编码的 URL 路径，我们将使用 `url.URL` 类型。我们将创建一个新的 URL，将 `Path` 字段设置为我们自己的路径，然后调用 URL 提供的 `String` 方法，输出编码后的 URL。由于我们从未定义域名（例如 "abc.com"）或协议（例如 "https"），输出将只包含 URL 的路径。

```go
import (
	// 添加此导入
	"net/url"
)
func (i *Image) Path() string {
	temp := url.URL{
		Path: "/" + i.RelativePath(),
	}
	return temp.String()
}
```

现在，在我们的模板或其他代码中调用 `Path` 方法的地方，我们不再需要担心对路径进行 URL 编码——它已经为你完成了。

最后，我们需要更新编辑画廊的模板。在其中手动构建了删除画廊图像的路径，我们将通过这个实例学习如何向我们的模板添加另一个函数，帮助我们正确地转义路径。

首先，打开视图源文件。

```go
$ atom views/view.go
```

## 16.5. 修复 Bug

幸运的是，`net/url` 包为我们提供了一个 `PathEscape` 函数，它的功能正是如此——对字符串进行适当的路径转义。

为了将此功能添加到我们的模板中，我们将更新 `NewView` 函数，像之前处理 `csrfField` 函数一样添加该函数，但这次我们将直接实现它。

```go
import (
    // 添加这个包
    "net/url"
)
func NewView(layout string, files ...string) *View {
    addTemplatePath(files)
    addTemplateExt(files)
    files = append(files, template.layoutFiles()...)
    t, err := template.New("").FuncMap{
        "csrfField": func (template.HTML, error) {
            return "", errors.New("csrfField is not implemented")
        },
        "pathEscape": func (s string) string {
            return url.PathEscape(s)
        },
    }).ParseFiles(files...)
    // 其他部分保持不变
}
```

现在我们可以更新编辑模板来使用这个函数。

```go
views/galleries/edit.html
```

在我们的 `deleteImage` 模板中，我们将更新代码以匹配以下内容。

```html
{{define "deleteImage"}}
