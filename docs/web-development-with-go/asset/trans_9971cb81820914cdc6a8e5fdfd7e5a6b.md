

## 14.5. 创建新画库

将 galleries 放在单独的源文件中以保持结构整洁。

```
$ atom controllers/galleries.go
```

我们将从 `Galleries` 类型开始，它将包含与画库资源相关的所有视图和处理函数。`Galleries` 类型最终需要访问 `GalleryService` 以与数据库交互，并且需要我们刚刚为创建模板的新画库页面视图。

```go
package controllers

import {
  "lenslocked.com/models"
  "lenslocked.com/views"
}

type Galleries struct {
  New +views.View
  gs models.GalleryService
}
```

接下来，我们将编写一个 `NewGalleries` 函数来简化此控制器的构造。在这里，我们将要求调用者传递一个 `GalleryService` 供我们使用，但我们将在本节开始时创建的模板自己构造 `New` 视图。

```go
func NewGalleries(gs models.GalleryService) *Galleries {
  return &Galleries{
    New: views.NewView("bootstrap", "galleries/new"),
    gs: gs,
  }
}
```

最后，我们需要更新 `main` 函数来创建一个 galleries 控制器，然后将 "/galleries/new" 路径映射到新的 galleries 视图。

## 第14章. 创建画库资源

```
$ atom main.go
```

```go
func main() {
    // ... 我们现有的设置服务的代码
    // 留在此处

    staticC := controllers.NewStatic()
    usersC := controllers.NewUsers(services.User)
    galleriesC := controllers.NewGalleries(services.Gallery)

    r := mux.NewRouter()
    // ... 我们现有的路由在这里

    // 画库路由
    r.Handle("/galleries/new"
```

重启你的 Web 应用并导航到我们的新页面 - localhost:3000/galleries/new。你应该能看到一个仅包含标题字段用于新画库的表单。

![](img/d6be51afcf11b16bf97245d05fb9e635_499_0.png)

图 14.1：我们的新画库表单

我们需要做的下一件事是解析传入的表单数据。为了做到，我们将创建一个类似于 `SignupForm` 的新结构体类型，但此类型仅解析表单中的 `Title`（标题）。

## 第14章. 创建画库资源

```go
type GalleryForm struct {
    Title string `schema:"title"`
}
```

现在，我们可以使用 `parseFunction` 将在 Web 请求中提交的数据解析为 `GalleryForm` 实例。如果解析表单出现错误，我们将使用创建的 `views.Data` 类型设置警报、渲染新画库表单并返回。否则，我们的代码将继续：

```go
func (g *Galleries) Create(w http.ResponseWriter, r *http.Request) {
    var vd views.Data
    var form GalleryForm
    if err := parseForm(r, &form); err != nil {
        vd.SetAlert(err)
        g.New.Render(w, vd)
        return
    }
    // TODO: 完成此实现
```

在 `form` 变量中有了表单数据后，我们就可以构造一个新的 `Gallery`。

```go
gallery := models.Gallery{
    Title: form.Title,
}
```

之后，我们将调用 `GalleryService` 的 `Create` 方法并传入画库，检查错误。如果发生错误，我们需要使用从错误创建的警报再次渲染 `New` 视图。否则，我们将打印成功创建的画库。

```go
func (g *Galleries) Create(w http.ResponseWriter, r *http.Request) {
    var vd views.Data
    var form GalleryForm
    if err := parseForm(r, &form); err != nil {
```

## 14.5. 创建新画库

```go
vd.SetAlert(err)
g.New.Render(w, vd)
return
}
gallery := models.Gallery{
Title: form.Title,
}
if err := g.gs.Create(&gallery); err != nil {
vd.SetAlert(err)
g.New.Render(w, vd)
return
}
fmt.Fprintln(w, gallery)
```

注意：这里缺失的一部分代码是填充画库中 `UserID` 字段的代码。我们最终将使用当前登录用户的 ID 来填充它，但目前我们将将其留空。

我们最后需要做的事是更新路由器。当 HTTP 方法为 POST 时，我们将在 /galeries 路径下处理表单。

```
$ atom main.go
```

```go
func main() {
// ... 我们的大部分代码保持不变

// 画库路由
r.Handle("/galeries/new", galleryC.New).Methods("GET")
r.HandleFunc("/galeries", galleryC.Create).Methods("POST")

fmt.Println("Starting the server on :3000...")
http.ListenAndServe(":3000", r)
}
```

虽然我们还没有实现任何逻辑，但我们现在可以使用我们的表单创建新画库了。重启你的服务器并前往新的画库页面进行测试 - localhost:3000/galeries/new。

## 第14章. 创建画库资源

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成 - book.usegolang.com/14.5.3
- 更改 - book.usegolang.com/14.5.3-diff

## 14.5.4 验证画库

就像验证用户一样，我们需要在将画库存储到数据库之前也对其进行验证。具体来说，我们想要验证 `UserID` 始终被设置，以便我们知道哪个用户创建了每个画库，并且还要求提供标题。

我们将开始为画库验证函数定义一个类型，以及一个运行这些函数的函数，就像我们之前对用户验证的那样。

```go
$ atom models/galleries.go

type galleryValFn func(*Gallery) error

func runGalleryValns(gallery *Gallery, fns ...galleryValFn) error {
	for _, fn := range fns {
		if err := fn(gallery); err != nil {
			return err
		}
	}
	return nil
}
```

现在我们可以开始为我们的画库编写验证函数了，从一个确保设置了 `UserID` 的函数开始。

## 14.5. 创建新画库

```go
const (
  ErrUserIDRequired modelError = "models: user ID is required"
)
func (gv *galleryValidator) userIDRequired(g *Gallery) error {
  if g.UserID <= 0 {
    return ErrUserIDRequired
  }
  return nil
}
```

注意：像我们刚刚创建的这样的错误不应该是公开的，因为终端用户无法控制 `UserID`。如果你想学习创建一个类似于我们的 `modelError` 类型的私有错误，请查看附录 18.4。

下一个是确保提供标题的验证。

```go
const (
  ErrTitleRequired modelError = "models: title is required"
)
func (gv *galleryValidator) titleRequired(g *Gallery) error {
  if g.Title == "" {
    return ErrTitleRequired
  }
  return nil
}
```

最后，我们需要在 `galleryValidator` 上实现 `Create` 方法，并运行我们刚刚编写的验证。

```go
func (gv *galleryValidator) Create(gallery *Gallery) error {
  err := runGalleryFns(gallery, gv.userIDRequired, gv.titleRequired)
  if err != nil {
    return err
  }
  return gv.galleryDB.Create(gallery)
}
```

如果我们现在重启服务器并尝试创建一个画库，我们将看到“User ID is required”的错误。在我们实现查找当前用户 ID 并将其设置到 `UserId` 字段的代码之前，我们将无法通过表单创建画库。

