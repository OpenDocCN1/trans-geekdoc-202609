

## 14.7. 显示画库

代码本身实际上没有区别，但现在如果我们更改路径，只需要在代码的单处进行更新即可。

`gorilla/mux` 包的路由器已经提供了类似的功能。我们不需要为每个路径创建一个单独的函数，而是简单地使用命名路由。

```
r := mux.NewRouter()
r.HandleFunc("/dogs/id:[0-9]+", dogHandler).Name("show_dog")
```

通过为我们的路由命名，我们稍后可以使用路由器来重建此类路由。

```
url, err := r.Get("show_dog").URL("id", "34")
```

第一个方法 `Get` 用于检索命名路由。第二个方法 `URL` 用于创建一个 `url.URL`。⁶，它是由 `url` 包提供的一个类型。我们需要传递到 `URL` 方法的唯一数据是我们需要为路由提供的参数。对于每个参数，我们首先提供参数名称（例如“id”），然后为它提供一个字符串格式的值（例如“34”）。

> 注意：`URL` 方法之所以这样工作，是因为它不知道你的路由有多少个变量，但通过使用变长参数，它可以接受根据需要任意数量的参数。

学习所有这一切意味着以下几点：

- 1. 如果我们要重建查看单个画库的路径，我们需要在画库控制器内部访问路由器。
- 2. 我们需要为显示画库的路由命名，并让该名称对控制器和我们的 `main.go` 源文件可用。

⁶https://golang.org/pkg/net/url#URL

```
func main() {
// .. 我们仍然以相同的方式设置服务
// 在我们创建控制器之前添加此内容。它
// 之前是在之后编写的。
r := mux.NewRouter()
staticC := controllers.NewStatic()
```

## 14.7. 显示画库

```
usersC := controllers.NewUsers(services.User)
// 我们还需要更新此函数调用以提供
// 路由器
galleriesC := controllers.NewGalleries(services.Gallery
```

接下来，我们需要为显示画库的路由定义一个名称。我们将在画库控制器的源文件中这样做，并将其存储在名为 `ShowGallery` 的常量中。

```
$ atom controllers/galleries.go
```

```
const (
  ShowGallery = "show_gallery"
)
```

接下来，我们需要回到主源文件，在其中声明并命名路由。

```
$ atom main.go
```

在你的 `main` 函数中找到与下面代码类似的路由。

```
r.HandleFunc("/galleries/{id:[0-9]+}", galleriesC.Show).Methods("GET")
```

## 第 14 章. 创建画库资源

在创建它之后，我们将更新它到路由器。

最后，我们回到画库控制器来更新 `Create` 方法。我们将添加代码，使用 `ShowGallery` 路由创建一个 URL，然后在用户创建画库后将他们重定向到该页面。

```
// atom controllers/galleries.go
```

```
func (g *Galleries) Create(w http.ResponseWriter, r *http.Request) {
	// 保持此大部分代码不变

	// 移除任何现有的 Fprintln 语句，如下所示
	//
	fmt.Fprintln(w, gallery)

	// 然后添加以下代码，使用路由器
	// 和命名的 ShowGallery 路由创建 URL。
	url, err := r.Get(ShowGallery).URL("id",
		strconv.Itoa(int(gallery.ID)))
	// 检查创建 URL 错误
	if err != nil {
		http.Redirect(w, r, "", http.StatusFound)
		return
	}
	// 如果出错，使用我们刚刚创建的 URL 并重定向
	// 到该 URL 的路径。我们不需要
	// 整个 URL，因为你的应用程序可能托管在
	// localhost:3000，或者可能在 lensocked.com。通过
	// 只使用我们创建的路径，可以忽略这一细节。
	http.Redirect(w, r, url.Path, http.StatusFound)
}
```

注意：我们在上面的代码中使用了 `Itoa` 函数，它与我们之前看到的 `Atoi` 函数相反。`Atoi` 将字符串转换为整数，而 `Itoa` 将将整数转换为字符串。我们只需要在将其传递给函数之前，将我们的 `uint` 强制转换为整数即可。

## 14.8. 编辑画库

在对 `Create` 方法进行最后的最后的更改后，我们就完成了在控制器中引入 `Show` 操作。重启你的服务器，通过访问 `localhost:3000/galleries/new` 并提交带标题的新画库表创建一个新画库。将被重定向到显示画库页面，URL 中的 ID 部分将填充为你创建的画库的 ID。显示画库页面还将你的新画库的标题渲染为页面的标题。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

完成 - book.usegolang.com/14.7.4

更改 - book.usegolang.com/14.7.4-diff

## 14.8 编辑画库

编辑画库就像编辑任何资源一样，将要求我们创建一些东西。

首先，我们需要创建一个视图来渲染编辑画库的表单，以及一个渲染视图的操作。

首先，我们需要创建一个视图来渲染编辑画库的表单，以及一个渲染视图的操作。

注意：我们在上一节中创建的显示画库操作是因为画库目前是公开的，但只有画库的所有者才能编辑它。

之后我们需要更新数据库中的库。我们将通过在 `models` 包的 `GalleryDB` 接口中添加 `Update` 方法来实现这一点。

最后，我们需要一种方式来处理画库表单，再次验证登录用户是否有权限编辑表单，然后使用我们在上一步引入的 `Update` 方法更新数据库。

我们将在子节中执行这些步骤。

### 14.8.1 编辑画库操作

像大多数新页面一样，我们将通过创建用于渲染视图的模板开始。对于我们的编辑画库页面，我们将具有基础的 Bootstrap 布局，以及一个将数据提交到 `POST /galleries/:ID/update` 的编辑画库表单。当我们学习 REST 时得知更新通常是通过 `PUT` 完成的，但遗憾的是大多数浏览器支持并不良好。让 `PUT` 起作用的唯一方法是使用 JavaScript 技巧，但使用唯一的 URL 和 POST 你的 Web 表单通常更容易。你的 Web 服务器仍然可以支持 `POST` 路由，但你不必被迫在你的网站中引入额外的 JavaScript。

```
$ atom views/galleries/edit.html
```

```
{%define "yield"}
<div class="row">
  <div class="col-md-6 col-md-offset-3">
    <div class="panel panel-primary"
```

```
## 14.8. 编辑画库

```
<div class="panel-heading">
  <h3 class="panel-title">编辑你的画库</h3>
</div>
<div class="panel-body">
  {{template "editGalleryForm"}}
</div>
</div>
</div>
{{}}

{{define "editGalleryForm"}}
<form action="/galleries/{{.ID}}/update" method="POST">
<div class="form-group">
<label for="title">标题</label>
<input type="text" name="title" class="form-control" id="title" placeholder="画库标题是什么？">
</div>
<button type="submit" class="btn btn-primary">更新</button>
</form>
{{end}}
```

我们在 `editGalleryForm` 模板中需要说明的一点是，我们现在将画库的当前标题设置为输入字段的默认值。这是通过读取代码实现的：

```
<input value="{{.Title}}">
<!-- 这部分设置了输入的初始值 -->
```

这意味着我们需要向模板传递一个现有的画库，我们稍后会这样做。现在让我们更新画库控制器，以便它知道我们的新视图。

```
atom controllers/galleries.go

func NewGalleries(go models.GalleryService, r mux.Router) *Galleries {
  return &Galleries{
  New: views.New("bootstrap", "galleries/new"),
  ShowView: views.New("bootstrap", "galleries/show"),
  EditView: views.New("bootstrap", "galleries/edit"),
```

