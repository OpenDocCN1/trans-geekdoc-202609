
将我们的中间件应用到路由器，然后将生成的处理程序传递到我们的 `ListenAndServe` 函数调用中。

```
http.ListenAndServe(":3000", userMw.Apply(r))
```

现在，`userMw` 在路由器运行之前运行，会将用户设置到请求上下文中（如果他们登录了）。

我们需要处理的下一段代码是渲染逻辑。这样当我们渲染导航栏时，我们可以决定是否显示画库链接，无论用户访问哪个页面。

# 548 第 14 章 创建画廊资源（Gallery Resource）

```go
// 在 Create 方法中，第二个 if 块内部：
g.New.Render(w, r, vd)

// 在 Delete 方法中，一个 if 块内部：
g.EditView.Render(w, r, vd)
```

```bash
$ atom controllers/users.go
```

```go
// 在 New 方法中：
u.New.Render(w, r, nil)
// 技术上你不需要处理器，在声明路由时
// 也可以直接将 NewView 作为处理器。
```

```go
// 在 Create 方法中，一个 if 块内部：
u.New.Render(w, r, vd)
// 在 Create 方法中，第二个 if 块内部：
u.New.Render(w, r, vd)

// 在 Login 方法中，一个 if 块内部：
u.LoginView.Render(w, r, vd)
// 在 Login 方法中，第二个 if 块内部：
u.Login.Render(w, r, vd)
// 在 Login 方法中，第三个 if 块内部：
u.LoginView.Render(w, r, vd)
```

我们终于准备好更新模板了。我们将从更新引导布局模板（bootstrap layout template）开始，告诉它将其拥所有数据传递给导航栏（navbar）模板。

```bash
$ atom views/layouts/bootstrap.gohtml
```

找到调用 navbar 模板的行，并更新它将点 (`.`) 作为最后一个参数添加。

## 14.11. 改进用户体验与清理

```html
{{template "navbar" }}
```

现在我们需要更新导航栏模板，如果用户字段（User Field）已设置，则显示画廊链接。

```bash
$ atom views/layouts/navbar.gohtml
```

找到包含首页和联系页面链接的 `<ul>` 标签。使用以下 HTML 更新该代码。

```html
<ul class="nav navbar-nav">
  <li><a href="/">首页</a></li>
  <li><a href="/contact">联系</a></li>
  {{if .User}}
    <li><a href="/galleries">画廊</a></li>
  {{end}}
</ul>
```

重启你的服务器并回到任何页面。现在只要我们登录了，就能看到画廊链接。删除 cookie 后，它将会消失，因为我们不再处于登录状态。

> 注意：我们还没有注销按钮，所以如果你想测试此功能，需要手动删除 cookie。出于这个原因，我建议在开发中使用 Chrome 的 EditThisCookie 插件。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 已完成 - book.usegolang.com/14.11.2
- 更改 - book.usegolang.com/14.11.2-diff

# 第 15 章：向画廊添加图像

接下来的议程是向我们的画廊添加图像。这将涉及添加新表单、处理这些表单的处理器函数，甚至在我们的 models 包中添加一个新的服务。

图像资源的独特之处在于，它将赋予我们一个机会去查看一个不一定映射到数据库中项的资源，而是映射到存储在我们硬盘上的图像（未来也可能是像 Amazon S3 之类的服务）。许多开发者，即使是经验丰富的开发者，也会开始认为每个模型都直接映射到数据库中的一个项，因为通常确实如此。虽然模型通常会在数据库中存储一些数据（即使只是元数据），但你也可以为应用程序引入一个完全不与数据库交互的模型。

在本章中，我们将做的正是此——添加一个完全不持久化到数据库的图像资源。相反，我们将把用户上传的图像存储在我们的硬盘上，并学习如何处理。

## 15.1 图像表单

我们将引入的第一个代码是用于上传的表单。过去，我们总是受限于单个表单，但对于图像，这并不合理。考虑到这一点，我们将为画廊页面添加上传表单，以便用户可以管理图像。这将允许用户可以处理多张图像。

我们将通过修改 `yield` 模板来开始工作。

```bash
$ atom views/galleries/edit
```

我们将对输入的第一个更改是引入用于上传的表单。

```html
{{define "uploadForm"}}
<form action="galleries/{{ID}}/images" method="POST" enctype="multipart/form-data" class="form-horizontal">
  <div class="form-group">
    <label for="images" class="col-md-1">添加图像</label>
    <div class="col-md-10">
      <input type="file" id="images" name="images" class="form-control" multiple>
      <p class="help-block">请使用 jpg、jpeg 和 png。</p>
    </div>
  </div>
  <button type="submit" class="btn btn-default">上传</button>
</form>
{{end}}
```

我们在输入字段中添加了 `multiple` 属性，这是告诉用户可以选择多张图像而不仅仅是一个。

另一个值得注意的是，这个表单使用了 `form-horizontal` 类，这是 Bootstrap 提供的另一种样式，看起来有点不同。

```html
{{define editGalleryForm}}
<form action="galleries/{{ID}}/update" method="POST" class="form-horizontal">
  <div class="form-group">
    <label for="title" class="col-md-1">标题</label>
    <div class="col-md-10">
      <input type="text" id="title" name="title" class="form-control" placeholder="画廊的标题是什么?" value="{{.Title}}">
    </div>
  </div>
  <button type="submit" class="btn btn-default">保存</button>
</form>
{{end}}

{{define deleteGalleryForm}}
<form action="galleries/{{ID}}/delete" method="POST" class="form-horizontal">
  <div class="form-group">
    <div class="col-md-10">
      <button type="submit" class="btn btn-danger">删除</button>
    </div>
  </div>
</form>
{{end}}
```

最后，我们将更新 `yield` 模板。之前我们将表单在中等或更大的屏幕上限制为 6 列，但根据我们的新设计，我们将提升到使用整个屏幕，并将内容划分为几行。

```html
{{yield}}
<div class="row">
  <div class="col-md-10 col-md-offset-1">
    <h2>编辑你的画廊</h2>
    <hr>
  </div>
  <div class="col-md-12">
    {{template editGalleryForm .}}
  </div>
</div>
<div class="row">
  <div class="col-md-1">
    <label class="col-md-10 control-label pull-right">图像</label>
  </div>
  <div class="col-md-10">
    {{template "galleryImages" .}}
  </div>
</div>
<div class="row">
  <div class="col-md-12">
    {{template "uploadImageForm" .}}
  </div>
</div>
```

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

### 源代码

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
