
注意我们的余数是如何从 0 变为 1、2，然后回到 0 的，正就像我们希望将图像放置在第 1 列、2 列、第 3 列一样。我们可以利用这一点将图像放置在二维切片中正确的切片里。

打开你的画册模型。我们将为 `Gallery` 类型添加一个方法来实现这一点，这样我们就可以轻松地渲染图像。技术上讲，对于大型应用程序，将内容拆分并使用模板函数或装饰器层是有意义的，但根据我的经验，这种需求在项目运行一段时间后才才会出现。我不建议在早期就这样做。

`$ models/galleries.go`

```go
func (g *Gallery) ImagesSplit(n int) [][]string {
  // 创建二维切片
  ret := make([][]string, n)
  // 创建内部切片 - 我们需要 n 个，并且从大小为 0 的大小开始。
  for i := 0; i < n; i++ {
    ret[i] = make([]string, 0)
  }
  // 遍历我们的图像，使用索引 % n 来确定
  // 将图像添加到 ret 中的哪一个切片中。
  for i, img := range g.Images {
    bucket := i % n
    ret[bucket] = append(ret[bucket], img)
  }
  return ret
}
```

为了编写这样拆分图像的代码，我们将为 `Gallery` 类型添加一个方法来实现这一点，这样我们就可以用它来轻松地渲染图像。

（注：原文后半部分存在大量重复和逻辑错乱，此处已根据代码逻辑进行了对齐翻译）

## 15.7. 让我们删除图片

接下来，我们将添加方法来构建诸如显示在浏览器中的路径等，以及我们文件系统上的相对路径。我倾向于将这些拆分为两个方法，以防将来我们将图片移动到另一个目录时，我们可能实际上只需要更改其中一个方法，而不是两个都改。

```go
// Path 用于构建用于通过 Web 请求 
// 引用此图片的绝对路径
func (i *Image) Path() string {
    return "/" + i.RelativePath()
}

// RelativePath 用于构建该图片在本地
// 磁盘上的路径，该路径相对于我们 Go 应用程序运行的目录。
func (i *Image) RelativePath() string {
    // 将 gallery ID 转换为字符串
    galleryID := fmt.Sprintf("%v", i.GalleryID)
    return filepath.ToSlash(filepath.Join("images", "galleries", galleryID, i.Filename))
}
```

注意：`ToSlash` 可能仅在 Windows 系统上需要，因为它们使用反斜杠 `\` 来分隔目录和文件。`ToSlash` 函数的工作原理是在使用反斜杠的操作系统上将所有正斜杠替换为反斜杠。

接下来，我们将更新现有的 `ByGallery` 方法，使其返回 `Images` 切片而不是字符串。

```go
type ImageService interface {
    Create(uint, r io.Reader, filename string) error
    ByGalleryID(galleryID uint) ([]Image, error)
}
```

实现上的更改稍微复杂一些。我们不再是遍历文件并添加斜杠 `/` 前缀，现在我们现在将从字符串中删除整个路径并只保留文件名。我们将使用 `path/filepath` 包提供的 `Base` 函数¹⁹ 来实现这一点。这将返回路径中的最后一个元素，在这种情况下，它就是我们的文件名。

> ¹⁹https://golang.org/pkg/path/filepath#Base

## 第 15 章. 向相册中添加图片

```go
func (is *imageService) ByGalleryID(galleryID uint) [][]Image
```

接下来，我们需要更新 `Gallery` 类型的 `Images` 字段，以及 `ImagesSplit` 方法。

```go
type Gallery struct {
	gorm.Model
	UserID uint `gorm:"not null;index"`
	Title string `gorm:"not null"`
	Images []Image `gorm:"-"`
}
```

```go
func (g *Gallery) ImagesSplitN(n int) [][]Image {
	ret := make([][]Image, n)
	for i := 0; i < n; i++ {
		ret[i] = make([]Image, 0)
	}
	for i, img := range g.Images {
		bucket := i % n
		ret[bucket] = append(ret[bucket], img)
	}
	return ret
}
```

更新我们的模型后，我们可以继续更新 HTML 模板了。它们需要一些更新以适应我们的模型更改，以及

## 15.7. 允许用户删除图片

一些 HTML 用于渲染删除图片按钮，该按钮将位于一个 HTML 表单内。这将导致在点击按钮并提交表单时发送一个 POST 网页请求。

我们将开始更新显示相册的模板。

```bash
$ atom views/galleries/show.gohtml
```

找到包含图片的 div，并更新它以反映下面的代码。我们现在需要调用 `Image` 的 `Path` 方法来获取路径，而不能像以前那样直接使用点 `.` 运算符。

```html
<div class="row">
{{range .ImagesSplit 3}}
  <div class="col-md-4">
    {{range .}}
      <a href="{{.Path}}">
<img src="{{.Path}}" class="thumbnail">
      </a>
    {{end}}
  </div>
{{end}}
```

# 1. 特殊字符

文件名中包含特殊字符的图片可能无法正常渲染。例如，文件名“/asjfalf/_ @1!&&.jpg”目前无法在我们应用程序中使用。

# 2. 新上传的图片不会立即渲染。

每当我们上传图片时，`ImageUpload` 处理器会渲染编辑画廊页面，而不会刷新画廊的图片列表。结果是渲染后的编辑画廊页面不会显示新上传的图片。

这里更大的问题是，现在在处理器成功后，我们有两个选择：

- 1. 带有提示框（alert）渲染视图
- 2. 重定向用户，但这样做时我们无法显示提示框

我们最终会探索如何更新代码，以便我们既能重定向用户（使其访问我们应用程序中的新 URL），同时又在该页面上显示提示框消息。

# 第 16 章

# 部署到生产环境

虽然我们的应用程序尚未完成，但我们现在已经到了可以开始准备将其部署到生产服务器的阶段。这很重要，因为部署到生产环境意味着要考虑开发中的某些在开发期间不需要过多考虑的方面。

例如，在本地开发时，我们不需要担心在代码中存储机密，但当我们开始与其他开发者合作并部署到生产环境时，我们需要一种为应用程序提供配置数据的方法。我们还需要开始考虑如果应用程序崩溃或运行的服务器重启，我们的应用程序将如何重启。

这些都不是我们在开发期间需要考虑的，因为只有我们自己在开发应用程序，如果发生任何问题，我们会在现场重启服务器或修复它。每当我们进入生产环境时，一切都改变了。没有人会坐在电脑前等待重启服务器，相反，它在我们睡觉、吃饭和做其他工作时 24 小时运行。

在本章中，我们将探索如何开始为你的应用程序准备这种不同的环境，然后我们将查看如何在 Digital Ocean 上设置和部署服务器。

# 第 16 章 部署到生产环境

注意：如果你从未使用过 Digital Ocean，请使用此链接 - `do.co/webdevgo` 来获取免费的 $10 额度，这足够免费运行我们使用的服务器一两个月。

## 16.1 错误处理

在部署到生产环境之前，最好花一点时间确保你的应用程序的错误处理处于良好状态。在开发过程中，如果我们遇到错误，通常可以多次复现它，并缓慢地添加新的日志语句来查看发生了什么，但在生产环境中，可能只有一个特定用户会看到错误消息，因此提前做好日志记录是明智的。这样你可以查看日志并找出哪里出了问题。

花一点时间查看我们的应用程序，找到那些可以更好处理的错误实例。这可能意味着任何事情，从移除 `panic` 改为返回错误，添加一些日志来打印错误内容以帮助我们调试，甚至在每次发生错误时将用户重定向到更有用的页面。如果你能想出任何想要添加日志或更改错误处理方式的原因，请尝试一下。

我不会演示如何进行这些更改，因为这些更改不会破坏你的应用程序，我相信通过仔细检查你自己的代码，你将从这一部分收获更多。这里的主要目标是理解你的代码在做什么以及它是如何处理每种情况的。

我将做的是提供我更新后的源代码，并附上详细的注释，以便你参考我选择了哪些更改。你的代码不需要与之完美匹配，但查看这些更改并考虑为什么进行它们是值得的。

注意：记住，你的 `View` 类型上的 `SetAlert` 方法也会记录任何非公开错误，因此我们不需要手动记录那些错误。

# 16.2. 提供静态资源

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异对比（diff）。

- 完成版 - `book.usegolang.com/16.1`
- 更改 - `book.usegolang.com/16.1-diff`

## 16.2 提供静态资源

我们的应用程序目前有一些样式硬编码在 HTML 模板中。这显然不是我们长期想要做的事情；相反，我们希望能够提供静态资源文件，例如 `styles.css` 文件。在本节中，我们将引入一个新的用于执行此操作的文件服务器。

我们要做的第一件事是创建样式文件。

```
$ mkdir assets
$ atom assets/styles.css
```

```css
/* LensLocked.com 样式 */
.thumbnail {
  width: 100%;
  margin-bottom: 6px;
}
.btn-delete {
  margin-bottom: 6px;
}
footer {
  padding-top: 60px;
}
```

我们需要删除任何内联样式。这些样式可以在编辑和显示画廊的模板中找到。

```
$ atom views/galleries/edit.gohtml
$ atom views/galleries/show.gohtml
```

在这些每个文件中，找到并移除 `<style>` 部分。

接下来是添加我们的文件服务器。这与我们创建图片文件服务器的方式几乎相同；我们甚至将需要使用 `StripPrefix`。

```
$ atom main.go
```

在你的路由中添加以下处理器。

```go
// Assets
assetHandler := http.FileServer(http.Dir("./assets"))
r.PathPrefix("/assets").Handler(assetHandler)
```

# 16.1 什么时候我们不需要 StripPrefix?

你可能会问自己什么时候会使用 `StripPrefix`。在上面的示例中，我们需要它是因为 `http.Dir` 是从 `assets` 开始的，但如果我们使用下面的方式，就不需要 `StripPrefix` 了：

```
# 将 styles.css 存储在这里：

/public/styles.css
```

因为我们的文件服务器是从 `public` 开始的，其中包含 `assets` 目录，所以我们不需要路径映射。

```go
assetHandler := http.FileServer(http.Dir("./public"))
r.PathPrefix("/assets/").Handler(assetHandler)
```

有了新的路由，我们终于准备好更新 bootstrap 模板以包含我们的 css。注意：在本课程中不会涵盖资源管道（asset pipelines），但如果你想使用，你需要将 CSS 和 JS 文件输出到我们创建的 assets 目录。

```
$ atom views/layouts/bootstrap.gohtml
```

找到模板中的 `<head>` 部分并添加以下链接。

```html
<head>
<title>LensLocked.com</title>
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
<!-- 添加此行以包含我们的样式 -->
<link href="assets/styles.css" rel="stylesheet">
</head>
```

恭喜，你的服务器现在能够提供静态资源！你可以通过直接访问 `styles.css` 文件来验证这一点。

```
localhost:3000/assets/styles.css
```

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异对比（diff）。

- 完成版 - `book.usegolang.com/16.2`
- 更改 - `book.usegolang.com/16.2-diff`

## 16.3 CSRF 保护

我们在讨论身份验证系统和 Cookie 时提到过 CSRF。CSRF 保护将帮助防止其他网站创建提交到我们服务器的表单，并欺骗用户执行他们不想的操作。

基本思想是我们的服务器为每个用户生成特定的令牌并以可以恢复的方式存储。例如，将 CSRF 令牌存储在用户的 Cookie 中是常见的，因为只有我们的服务器可以读取。之后在创建表单时，我们将 CSRF 令牌作为隐藏字段嵌入 HTML 表单中。

当用户提交表单时，他们提交的表单和 Cookie 都包含此 CSRF 令牌。如果缺少其中任何，任何表单提交都将被拒绝。这将防止其他网站创建伪造表单，因为它们不知道用户 Cookie 中的 CSRF 令牌是什么，无法进行伪造。

我们将使用 `gorilla/csrf` 包来实现它。技术上我们

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

```
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
