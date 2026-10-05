

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

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

> ²http://www.gorillatoolkit.org/pkg/schema#Decoder.IgnoreUnknownKeys

## 16.4. 限制静态资源的中间件

已完成 - book.usegolang.com/16.3

已更改 - book.usegolang.com/16.3-diff

# 16.4 限制静态资源的中间件

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

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/16.4

已更改 - book.usegolang.com/16.4-diff

# 16.5 修复 bug

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

## 16.5.1 URL 编码路径

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

