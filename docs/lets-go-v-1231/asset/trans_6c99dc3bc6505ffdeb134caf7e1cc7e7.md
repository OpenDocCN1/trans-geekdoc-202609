

在继续之前，我应该说明：自定义模板函数（例如我们的 humanDate() 函数）可以接受尽可能多的参数，但它们 *必须* 只返回一个值。唯一的例外是，如果你想将错误作为第二个值返回，那也是可以的。

现在，我们可以像使用内置模板函数一样使用我们的 humanDate() 函数：

```
File: ui/html/pages/home.tmpl

{{define "title"}}Home{{end}}

{{define "main"}}
<h2>Latest Snippets</h2>
{{if .Snippets}}
<table>
<tr>
<th>Title</th>
<th>Created</th>
<th>ID</th>
</tr>
{{range .Snippets}}
<tr>
<td><a href='/snippet/view/{{.ID}}'>{{.Title}}</a></td>
<!-- Use the new template function here -->
<td>{{humanDate .Created}}</td>
<td>#{{.ID}}</td>
</tr>
{{end}}
</table>
{{else}}
<p>There's nothing to see here... yet!</p>
{{end}}
{{end}}
```

```
File: ui/html/pages/view.tmpl

{{define "title"}}Snippet #{{.Snippet.ID}}{{end}}

{{define "main"}}
{{with .Snippet}}
<div class='snippet'>
<div class='metadata'>
<strong>{{.Title}}</strong>
<span>#{{.ID}}</span>
</div>
<pre><code>{{.Content}}</code></pre>
<div class='metadata'>
<!-- Use the new template function here -->
<time>Created: {{humanDate .Created}}</time>
<time>Expires: {{humanDate .Expires}}</time>
</div>
</div>
{{end}}
{{end}}
```

做完这些之后，重启应用程序。如果你在浏览器中访问 http://localhost:4000 和 http://localhost:4000/snippet/view/1，你应该能看到使用了新的、格式良好的日期。

![](img/c3e650db0d8dfdecc0f8e34a67719f65_171_0.png)

![](img/c3e650db0d8dfdecc0f8e34a67719f65_172_0.png)

## 补充信息

## 管道化

在上面的代码中，我们是这样调用自定义模板函数的：

```
<time>Created: {{humanDate .Created}}</time>
```

另一种方法是使用 | 字符将值管道化到函数中。这有点像在 Unix 终端中将一个命令的输出管道化到另一个命令。我们可以将上面的代码重写为：

```
<time>Created: {{.Created | humanDate}}</time>
```

管道化的一个好处是，你可以创建任意长的模板函数链，每个函数的输出作为下一个函数的输入。例如，我们可以将 humanDate 函数的输出管道化到内置的 printf 函数，如下所示：

```
<time>{{.Created | humanDate | printf "Created: %s"}}</time>
```

## 中间件

在构建 Web 应用程序时，你可能希望为许多（甚至所有）HTTP 请求使用某些共享功能。例如，你可能希望记录每个请求、压缩每个响应，或在将请求传递给处理程序之前检查缓存。

组织这些共享功能的常见方法是将其设置为中间件。这本质上是一些自包含的代码，它在正常的应用程序处理程序之前或之后独立处理请求。

在本书的这一部分中，你将学习：

- 一种用于构建和使用自定义中间件的惯用模式，该模式与 net/http 及许多第三方包兼容。
- 如何创建在每个 HTTP 响应上设置常见 HTTP 标头的中间件。
- 如何创建记录应用程序接收到的请求的中间件。
- 如何创建恢复 panic 的中间件，以便由你的应用程序优雅地处理。
- 如何创建和使用可组合的中间件链，以帮助管理和组织你的中间件。

### 中间件的工作原理

在本书前面，我说过一段话，我想在本章中对其进行展开：

> “你可以把 Go Web 应用程序看作是一个接一个地被调用的 ServeHTTP() 方法链。”

目前，在我们的应用程序中，当服务器收到新的 HTTP 请求时，它会调用 servemux 的 ServeHTTP() 方法。该方法根据请求方法和 URL 路径查找相关处理程序，并反过来调用该处理程序的 ServeHTTP() 方法。

中间件的基本思想是将另一个处理程序插入到这个链中。中间件处理程序执行一些逻辑，例如记录请求，然后调用链中下一个处理程序的 ServeHTTP() 方法。

事实上，我们的应用程序中实际上已经在使用一些中间件了——即来自提供静态文件的 http.StripPrefix() 函数，它在将请求传递给文件服务器之前，从请求的 URL 路径中删除特定前缀。

### 模式

创建自己的中间件的标准模式如下：

```go
func myMiddleware(next http.Handler) http.Handler {
    fn := func(w http.ResponseWriter, r *http.Request) {
        // TODO: Execute our middleware logic here...
        next.ServeHTTP(w, r)
    }
    return http.HandlerFunc(fn)
}
```

代码本身相当简洁，但其中有很多内容需要理解。

- myMiddleware() 函数本质上是对下一个处理程序的包装器，我们将其作为参数传递给它。
- 它建立了一个函数 fn，该函数对下一个处理程序形成闭包。当 fn 运行时，它执行我们的中间件逻辑，然后通过调用其 ServeHTTP() 方法将控制权转移给下一个处理程序。

- 无论你对闭包做什么，它始终可以访问其创建所在作用域中的局部变量——在此例中，这意味着 fn 始终可以访问 next 变量。
- 在代码的最后一行，我们将此闭包转换为 http.Handler，并使用 http.HandlerFunc() 适配器返回它。

如果这让你感到困惑，可以简单地这样理解：myMiddleware() 是一个接受链中下一个处理程序作为参数的函数。它返回一个处理程序，该处理程序执行一些逻辑，然后调用下一个处理程序。

### 简化中间件

对这一模式的一种改进是在 myMiddleware() 中间件内部使用匿名函数，如下所示：

```go
func myMiddleware(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		// TODO: Execute our middleware logic here...
		next.ServeHTTP(w, r)
	})
}
```

这种模式在实际开发中非常常见，如果你阅读其他应用程序或第三方包的源代码，可能会最常看到这种模式。

### 中间件的位置

重要的是要说明，中间件在处理程序链中的位置会影响应用程序的行为。

如果在链中将中间件放在 servemux 之前，那么它将作用于应用程序接收到的每个请求。

```
myMiddleware -> servemux -> application handler
```

一个很好的例子是请求日志中间件——因为通常你希望对所有请求都执行此操作。

或者，你可以通过包装特定的应用程序处理程序，将中间件放在链中 servemux 之后。这将导致你的中间件仅针对特定路由执行。

```
servemux → myMiddleware → application handler
```

这的一个示例是授权中间件，你可能只希望在特定路由上运行它。

随着我们深入本书，我们将演示如何在实践中实现这两种方法。

### 设置常见标头

让我们使用上一章学到的模式，创建一些中间件，它会自动向每个响应添加我们的 Server: Go 标头，以及以下 HTTP 安全标头（符合当前 OWASP 指南）。

```
Content-Security-Policy: default-src 'self'; style-src 'self' fonts.googleapis.com; font-src fonts.gstatic.com
Referrer-Policy: origin-when-cross-origin
X-Content-Type-Options: nosniff
X-Frame-Options: deny
X-XSS-Protection: 0
```

如果你不熟悉这些标头，我将简要说明它们的作用。

- Content-Security-Policy（通常缩写为 CSP）标头用于限制网页资源（例如 JavaScript、图像、字体等）的加载来源。设置严格的 CSP 策略有助于防止各种跨站点脚本、点击劫持和其他代码注入攻击。

CSP 标头及其工作原理是一个庞大的主题，如果你之前没有接触过它们，我建议阅读这个入门指南。但是，在我们的例子中，该标头告诉浏览器可以从 fonts.gstatic.com 加载字体，从 fonts.googleapis.com 和 self（我们自己的来源）加载样式表，然后其他所有内容仅从 self 加载。内联 JavaScript 默认被阻止。

- Referrer-Policy 用于控制当用户从你的网页导航离开时，Referer 标头中包含哪些信息。在我们的例子中，我们将值设置为 origin-when-cross-origin，这意味着对于同源请求将包含完整的 URL，但对于所有其他请求，诸如 URL 路径和查询字符串值等信息将被剥离。

- X-Content-Type-Options: nosniff 指示浏览器不要对响应的内容类型进行 MIME 类型嗅探，从而有助于防止内容嗅探攻击。

- X-Frame-Options: deny 用于帮助防止旧版浏览器中的点击劫持攻击，这些浏览器不支持 CSP 标头。

- X-XSS-Protection: 0 用于禁用跨站点脚本攻击的阻止。以前，将此标头设置为 X-XSS-Protection: 1; mode=block 是良好做法，但当你使用像我们这样的 CSP 标头时，建议禁用此设置。

