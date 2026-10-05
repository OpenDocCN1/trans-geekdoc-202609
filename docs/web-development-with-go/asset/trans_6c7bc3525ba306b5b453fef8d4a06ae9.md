

## 16.3. CSRF 保护

我们可以尝试自己编写这些代码，但根据我的经验，编写像这样经过实战检验的安全库要比编写它本身要好。否则，很容易引入 bug。而且根据我的经验，大多数 Web 开发者永远不会自己编写 CSRF 库，而是学习使用受信任的库来他们完成这些工作。

首先，我们需要安装该包。

```go
$ go get github.com/gorilla/csrf
```

一旦安装完成，你可能需要查阅一下文档。可以在此处找到文档：https://github.com/gorilla/csrf

在文档中，我们可以找到以下示例：

```
CSRF := csrf.Protect([][]byte("32-byte-long-auth-key"))
http.ListenAndServe(":8000", CSRF(r))
```

`csrf` 包为我们提供了一个 `Protect` 函数，用于创建 CSRF 中间件。然后，我们将此中间件应用到我们的路由器（或我们使用的任何顶层处理器），以便在调用任何其他处理器之前进行 CSRF 保护。通过这种方式，我们确保所有传入的请求在运行任何自定义代码之前都经过了 CSRF 令牌的验证。

在创建中间件时，我们需要一个随机的 32 字节认证密钥。这用于确保我们的应用程序不会生成可预测的 CSRF 令牌。

我们将使用这个示例作为起点，并将 CSRF 中间件添加到我们自己的应用程序中。

```go
$ atom main.go
```

我们将稍微调整一下名称，还将使用创建的 `rand` 包来生成 32 字节。

```go
csrfMw := csrf.Protect(rand.Bytes(32))
```

注意：当我们重启服务器时，这可能会导致表单中任何现有的 CSRF 令牌失效，但我还没有看到此问题频繁出现。我们并不经常重启服务器，如果你真的很担心，可以在本章介绍配置文件时，在我们的配置中添加一个静态令牌。

一旦我们有了 `csrfMw` 函数，就可以将其应用到路由器，以确保它在任何其他处理器之前运行。

```go
http.ListenAndServe(":3000", csrfMw.Apply(r))
```

现在，每当提交表单或我们的服务器接收到 HTTP POST 请求时，`csrfMw` 都会检查是否存在有效的 CSRF 令牌。如果存在，则将调用下一个处理器；否则，整个请求在到达我们的处理器之前就会被拒绝。这使得我们在编写处理器时可以假设此安全问题已经为我们实现。

我们需要对代码进行最后一次微调，即告诉 `csrf` 包我们是否在生产环境中运行。我们将使用一个临时变量来实现这一点，当我们引入配置变量时，它最终会被配置变量替换。

找到实例化 `csrfMw` 变量的行，并使用以下代码更新它。

```go
// TODO: 更新此处为配置变量
isProd := false
b, err := rand.Bytes(32)
if err != nil {
    panic(err)
}
csrMw := csrf.Protect(b, csrf.Secure(isProd))
```

`csrf` 包还为我们提供了一个为 HTML 表单生成令牌的辅助函数。该包的文档随后解释了推荐的向 HTML 表单提供此类令牌的方法：将其作为数据字段传递到模板中。例如，我们可能会将此字段添加到 `views.Data` 类型中。

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
