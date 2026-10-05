

## 15.1. 图片上传表单

```
<hr>
</div>
<div class="col-md-12">
{{template "deleteGalleryForm" }}
</div>
</div>>
{{end}}
```

我们在上面引用了“galleryImages”模板，但还没有添加它，所以接下来我们可以添加它。这在接下来的几个章节中将会变化，包含图库中每张图片的预览缩略图以及从图库中删除图片的方法，但目前我们只使用占位文本。

```
{{define "galleryImages"}}
<p>即将上线...</p>
{{end}}
```

我们目前还没有处理图片上传表单的代码，但如果我们重启服务器，我们的编辑图库页面看起来将比之前更实用得多。

## 第 15 章：向图库添加图片

![](img/d6be51afcf11b16bf97245d05fb9e635_581_0.png)

图 15.1：编辑图库页面

注意：如果你不喜欢这个页面的外观，欢迎重新设计它。只需确保保留相似的表单，否则我们的处理器在接下来的几个章节中可能无法工作。

## 源代码

下面的链接包含了完整的源代码以及本章节中所有更改代码的差异。

[完成 - book.usegolang.com/15.1]

[更改 - book.usegolang.com/15.1-diff]

## 15.2. 处理图片上传

在本章节中，我们将重点关注处理图库的图片上传。我们将直接在控制器动作中编写大部分代码，然后在接下来的章节中，我们将对代码进行一些重构，将相关部分移动到图片服务中。我们现在还不会编写显示这些图片的代码，而将在未来的章节中编写。

通常我们会为图片引入一个新的控制器，但在这种情况下我们不会这样做。每当用户上传图片时，这些图片总是与某个图库关联，因为图片是图库的子资源。没有图库，用户无法上传新图片。这就是为什么路由的图片上传请求会包含图库 ID。

```
POST /galleries/:id/images
```

除了知道图片是图库的子资源外，我们知道图片不需要很多操作。用户对图片真正可以执行的操作只有上传新图片或删除现有的图片。

考虑到这一切，将图片上传的处理器添加到图库控制器中更合合理。这样我们就可以访问所有与图库相关的方法，例如通过路径中存储的 ID 查找图库，而无需重新创建它们。

> 注意：像许多设计决策一样，这完全是基于偏好和经验。你可能会发现你更倾向于为所有处理器函数采用完全不同的设计。

让我们从编写处理器函数的存根并为它创建一个路由开始。我们将从存根方法开始。

## 第 15 章：向图库添加图片

```
$ atom controllers/galleries.go
```

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

## 框 15.1 什么是位移？

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

