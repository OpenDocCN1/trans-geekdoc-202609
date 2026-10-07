
```go
// POST /galleries/:id/images
func (g *Galleries) ImageUpload(w http.ResponseWriter, r *http.Request) {
  // TODO: 实现此功能
}
```

然后我们将为它声明一个路由。

```
$ atom main.go
```

```go
r.HandleFunc("/galleries/:id:[0-9]+/images",
requireUserMw.ApplyFn(galleriesC.ImageUpload).
Methods("POST"))
```

现在基础工作已经完成，我们需要弄清楚将如何处理图片上传。首先，我们将编写代码，使用路径中的 ID 部分获取当前图库，并验证当前用户是否有权限编辑该图库。如果你想避免重复输入，这段代码甚至可以从 `Upload` 方法中复制。

```
$ atom controllers/galleries.go
```

```go
func (g *Galleries) ImageUpload(w http.ResponseWriter, r *http.Request) {
  gallery, err := g.galleryByID(w, r)
  if err != nil {
    return
  }
  user := context.User(r.Context())
  if gallery.UserID != user.ID {
    http.Error(w, "Gallery not found", http.StatusNotFound)
    return
  }
  // TODO: 完成此功能的实现
}
```

## 15.2. 处理图片上传

接下来我们需要解析表单。与我们过去的表单不同，此表单被编码为多部分表单（multipart form），这可以通过表单 HTML 标签的 `enctype` 属性推断出来。

```html
<form action="/galeries/{{.ID}}/images" method="POST"
ctype="multipart/form-data" class="form-horizontal">
<!-- 这是编码类型 -->
</form>
```

注意：此代码段仅用于说明；你已经编写了它。

Go 的 `net/http` 包为我们提供了 `ParseMultipartForm` 方法，用于解析编码为 `multipart/form-data` 的表单。

注意：务必花时间阅读 `ParseMultipartForm` 方法的文档。阅读代码中将使用的方法的文档是一个好习惯，这样你可以完全理解它们。

`ParseMultipartForm` 方法接收一个参数 - `maxMemory`，它告诉我们存储在内存中的文件最大字节数。如果上传了超过此大小的文件，剩余部分将存储在磁盘（硬盘）上的临时文件中，我们可以检索这些文件。

我们需要决定最大内存是多少，并将其存储在变量或常量中。使用的数字越大，应用程序使用的内存就越多，但数字越小意味着你需要频繁地从磁盘读取。在这种情况下，我们仅使用 1 兆（1048576 字节），但如果需要，你可以随时更改它。我们将将其作为一个常量。

```go
const (
  maxMultipartMem = 1 << 20 // 1 兆
)
```

> ³https://golang.org/pkg/net/http#Request.ParseMultipartForm

### 框 15.1 什么是位移？

位移是一种操作，你取一个二进制数将其位向左或右右。这通常用于对2的幂进行快速乘法或除法。

在 Go 中，我们使用 `<<` 运算符左移，使用 `>>` 运算符右移。例如，`1 << 1` 是 2，`1 << 2` 是 4。

## 15.2. 处理图片上传

```go
// 如果无法解析表单，只需在编辑页面上渲染一个错误提示。
vd.SetAlert(err)
g.EditView.Render(w, r, vd)
return
```

```go
// ...现有代码

var vd views.Data
vd.Yield = gallery
err = r.ParseMultipartForm(maxMultipartMem)
if err != nil {
```

对文件执行任何操作的权限，同时赋予他人读取和执行权限。

### Box 15.2. 文件权限

文件权限在 Linux 环境中更为常见，但无论什么操作系统，`MkdirAll` 函数都需要权限。即使你不使用 Linux，也可能需要意识到它们，因为你可能会在某个时刻将其部署到 Linux 服务器上。

关于文件权限的更多信息，我推荐以下内容：

- https://help.ubuntu.com/community/FilePermissions
- http://www.grymoire.com/Unix/Permissions.html

我们知道想要使用 `MkdirAll` 函数来创建目录，但我们仍然构建一个表示目录路径的字符串。我们将使用 `path/filepath` 包中的 `Join` 函数 ⁵，并配合 `fmt.Sprint` 将我们的 `uint` 转换为字符串。

将所有内容整合，我们得到了下面的代码：

```go
import (
  "fmt"
  "os"
  "path/filepath"
)

func (g *Galleries) ImageUpload(w http.ResponseWriter, r *http.Request) {
  // 现有代码保持不变
```

> ⁵https://golang.org/pkg/path/Join

## 15.2. 处理图片上传

```go
// 创建包含我们图片的目录

// filepath Join 将返回类似下面的路径：
// images/galleries/123
// 我们使用 filepath Join 而不是在
// 斜杠和其他字符之间手动构建路径
// 因为在不同操作系统之间可能会不同。
galleryPath = filepath.Join("images", "galleries")
fmt.Printf("%v", gallery)
// 创建我们的目录（以及任何必要的父目录）
// 使用 0755 权限。
err := os.MkdirAll(galleryPath, 0755)
if err != nil {
    // 如果发生错误，重新渲染编辑画页面
    vd.SetAlert(err)
    g.EditView.Render(w, r, vd)
}
return
```

接下来，我们需要遍历所有上传的文件，并将它们存储在我们刚刚为画廊创建的目录中。我们之前调用的 `ParseMultipartForm` 会为我们解析上传的表单，但它不会对文件进行任何操作。我们仍然需要将其复制到永久位置。

为了做到这一点，我们将使用 `httpRequest` 的 `MultipartForm`⁶ 字段。在调用 `ParseMultipartForm` 之前无法使用它，但在调用解析函数后，我们可以使用 `Request` 的 `MultipartForm` 字段来访问 `multipart.Form`⁷

```go
r.MultipartForm // a *multipart.Form
```

`multipart.Form` 定义如下：

> ⁶https://golang.org/pkg/net/http/#Request
> ⁷https://golang.org/pkg/mime/multipart/#Form

```go
type Form struct {
  Value map[string][]string
  File map[string][]FileHeader
}
```

在 `multipart.Form` 提供的两个字段中，我们将使用 `File` 字段。该字段存储了一个 map，其中每个键映射到 HTML input 标签的 `name` 属性（所示），每个键的值是 `FileHeaders` 的切片，我们可以用它来访问每个上传的文件。

在我们的情况下，HTML input 标签的 `name` 设置为 `images`。

```html
<input type="file" multiple="multiple" id="images" name="images">
```

将所有内容整合在一起，如果我们想访问对应我们图片上传的 `FileHeaders` 切片，我们将使用下面的 Go 代码访问它们。

```go
files := r.MultipartForm.File["images"]
```

我们将遍历每个 `FileHeader` 值，并使用 `open()` 方法打开与该 `FileHeader` 关联的文件。这将返回返回一个 `File`10 和/或一个错误。如果发生错误，我们需要关闭文件以防止内存泄漏，因此我们可以 `defer` 该调用以确保其发生。如果发生错误，我们将重新渲染编辑页面。

> ^8https://golang.org/pkg/mime/multipart#FileHeader
> 9https://golang.org/pkg/mime/multipart#FileHeader.Open
> 10https://golang.org/pkg/mime/multipart#File

## 15.2. 处理图片上传

```go
func (g *Galleries) ImageUpload(w http.ResponseWriter, r *http.Request) {
    // ... 现有代码
```

遗憾的是，我知道这一部分涵盖了许多对你来说可能陌生的代码，如果你是 Go 的新手尤其如此。遗憾的是，我无法对这些每一个项进行非常详细的介绍，因为其中许多项都值得拥有它们自己的微型书籍，但我能告诉你的是，这一切通过练习会变得越来越简单。

如果你对我们使用的某个标准库函数或任何其他内容感到有些困惑，我首先建议查看相应代码的文档。在那里也寻找示例，因为它们通常说明了如何使用某个函数。

之后，尝试在网上搜索相关资源。如果你能找到正确的帖子，Stack overflow 和类似的网站通常会有关于某个函数如何工作的非常棒的解释。还有许多其他很棒的网站，如 Go by Example，它们尝试展示如何使用 Go 完成特定任务，在其中许多示例中，你将看到像 `io.Copy` 这样的函数被使用。

```go
func (g *Galleries) ImageUpload(w http.ResponseWriter, r *http.Request) {
    // ... 现有代码

    // 创建包含我们图片的目录
    // filepath Join 将返回类似下面的路径：
    // images/galleries/123
    // 我们使用 filepath Join 而不是在
    // 斜杠和其他字符之间手动构建路径
    // 因为在不同操作系统之间可能会不同。
    galleryPath = filepath.Join("images", "galleries")
    fmt.Printf("%v", gallery)
    // 创建我们的目录（以及任何必要的父目录）
    // 使用 0755 权限。
    err := os.MkdirAll(galleryPath, 0755)
    if err != nil {
        // 如果发生错误，重新渲染编辑画页面
        vd.SetAlert(err)
        g.EditView.Render(w, r, vd)
        return
    }

    // 接下来我们需要遍历所有上传的文件，并将它们存储在我们刚刚为画廊创建的目录中。之前调用的 ParseMultipartForm 会为我们解析上传的表单，但它不会对文件进行任何操作。我们仍然需要将其复制到永久位置。
    // 为了做到这一点，我们将使用 httpRequest 的 MultipartForm⁶ 字段。在调用 ParseMultipartForm 之前无法使用它，但在调用解析函数后，我们可以使用 Request 的 MultipartForm 字段来访问 multipart.Form⁷
    // r.MultipartForm // a *multipart.Form

    // multipart.Form 定义如下：
    // type Form struct {
    //   Value map[string][]string
    //   File map[string][]FileHeader
    // }
    // 在 multipart.Form 提供的两个字段中，我们将使用 File 字段。
    // 该字段存储了一个 map，其中每个键映射到 HTML input 标签的 name 属性（所示），
    // 每一个键的值是 FileHeaders 的切片，我们可以用它来访问每个上传的文件。
    // 在我们的情况下，HTML input 标签的 name 设置为 images。
    // <input type="file" multiple="multiple" id="images" name="images">

    // 将所有内容整合在一起，如果我们想访问对应我们图片上传的 FileHeaders 切片，我们将使用下面的 Go 代码访问它们。
    // files := r.MultipartForm.File["images"]

    //我们将遍历每个 FileHeader 值，并使用 open() 方法打开与该 FileHeader 关联的文件。
    // 这将返回一个 File10 和/或一个错误。如果发生错误，我们需要关闭文件以防止内存泄漏，
    // 所以我们可以 defer 该调用以确保其发生。如果发生错误，我们将重新渲染编辑页面。
    // 我们将遍历每个 FileHeader 值，并使用 open() 方法打开与该 FileHeader 关联的文件。
    // 这将返回一个 File10 和/或一个错误。如果发生错误，我们需要关闭文件以防止内存泄漏，
    // 所以我们可以 defer 该调用以确保其发生。如果发生错误，我们将重新渲染编辑页面。

    // 遍历每个 FileHeader 值
    for _, f := range r.MultipartForm.File["images"] {
        file, err := f.Open()
        if err != nil {
            vd.SetAlert(err)
            g.EditView.Render(w, r, vd)
            return
        }
        defer file.Close()

        // 现在我们有了文件，想要将其复制到目标地。
        // 我们将使用 io.Copy 来完成。
        dst, err := os.Create(filepath.Join(galleryPath, f.Filename))
        if err != nil {
            vd.SetAlert(err)
            g.EditView.Render(w, r, vd)
            return
        }
        defer dst.Close()

        _, err = io.Copy(dst, file)
        if err != nil {
            vd.SetAlert(err)
            g.EditView.Render(w, r, vd)
            return
        }
    }

    vd.Alert = &views.Alert{
        Level:   views.AlertSuccess,
        Message: "Images successfully uploaded!",
    }
    g.EditView.Render(w, r, vd)
}
```

## 15.2. 处理图片上传

如果一切按计划进行，我们将打印出一个成功提示并重新渲染编辑页面。我们可以访问计算机上的图片来验证图片是否已写入那里。在继续之前，测试这段代码是重要的，如果这部分不起，我们接之后的大部分代码将无法工作。

![](img/dbe51afcf1116bf97245d05fb9e635_592_0.png)

图 15.2：一张上传的图片

### Box 15.3. 如果感到困惑

在继续之前，值得注意的是这一部分涵盖了许多对你来说可能陌生的代码，如果你是 Go 的新手尤其如此。遗憾的是，我无法对这些每一个项进行非常详细的介绍，因为其中许多项都值得拥有它们自己的微型书籍，但我能告诉你的是，这一切通过练习会变得越来越简单。

如果你对我们使用的某个标准库函数或任何其他内容感到有些困惑，我首先建议查看相应代码的文档。在那里也寻找示例，因为它们通常说明了如何使用某个函数。

之后，尝试在网上搜索相关资源。如果你能找到正确的帖子，Stack overflow 和类似的网站通常会有关于某个函数如何工作的非常棒的解释。还有许多其他很棒的网站，如 Go by Example，它们尝试展示如何使用 Go 完成特定任务，在其中许多示例中，你将看到像 `io.Copy` 这样的函数被使用。

### Box 15.4. 如果你在使用 git

如果你在使用 git，你可能不想提交我们创建的图片，因此建议将 images 目录添加到你的 .gitignore 文件中。这将告诉 git 不要将该目录中的任何文件添加到你的仓库中。

```
images/**
```

## 15.3 创建图片服务

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。
