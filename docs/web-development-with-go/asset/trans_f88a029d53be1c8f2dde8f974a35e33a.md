

## 14.7. 显示画库

现在我们已经知道了要做什么，让我们从为我们的画库展示页定义路由开始。

```
$ atom main.go
```

我们将在现有的画库路由之后引入一个新的新路由。

```go
func main() {
  // 大部分内容保持不变
  r := mux.NewRouter()
  // 我们有几个现有的路由

  // 画库路由
  // 留出现有的画库路由，并在下方添加
  // 新路由。
  r.HandleFunc("/galleries/id:[0-9]+",
    galleriesC.Show).Methods("GET")

  // ... 剩余代码保持不变
}
```

这段代码告诉我们的路由器，我们希望将所有以 /galleries/ 开头并以数字 ID 结尾的网络请求映射到画库控制器的 `Show` 方法。我们还没有定义该方法，所以让我们接下来来定义它。

```
$ atom controllers/galleries.go
```

与其在事后才尝试解释这一切，我们将在下方查看完整的代码，并在几乎每一行代码之前都添加注释，以帮助解释每行代码的用途。

```go
import (
  // 添加此导入
  "strconv"
)
```

## 第 14 章节：创建画库资源

```go
// GET /galleries/:id
func (g *Galleries) Show(w http.ResponseWriter, r *http.Request) {
	// // 首先我们像之前看到的那样获取变量。这样做
	// 是为了我们可以从路径中获取变量，比如 "id"
	// 变量。
	vars := mux.Vars(r)
	// 现在我们需要从 vars 中获取 "id" 变量。
	idStr := vars["id"]
	// 我们的 idStr 是字符串，所以我们使用 strconv 包提供的
	// Atoi 函数将其转换为整数。此函数还可以返回一个错误，
	// 所以我们需要检查该错误。
	id, err := strconv.Atoi(idStr)
	if err != nil {
		// 如果发生错误，我们将返回 StatusNotFound
		// 画库 ID，因为请求的页面是无效的。
		http.Error(w, "Invalid gallery ID", http.StatusNotFound)
		return
	}
	// 这个返回只是为了防止编译器抱怨
	// 没有使用 id 参数。我们稍后会使用它。
	_ = id
	// 最后我们需要根据已有的 ID 查找画库，
	// 但我们还没有写那部分代码！目前我们将
	// 创建一个临时画库来测试我们的视图。
	gallery := models.Gallery{
		Title: "A temporary fake gallery with ID: " + idStr,
	}
	// 我们将构建 views.Data 对象并将我们的画库
	// 设置为 Yield 字段，但从技术上我们不需要
	// 这样做，可以直接将 gallery 传递给 Render
	// 方法，因为我们在 Render 方法中编写了类型切换逻辑。
	var vd views.Data
	vd.Yield = gallery
	g.ShowView.Render(w, vd)
}
```

虽然我们的代码还没有从数据库中渲染画库，但我们现在能够通过导航到类似 localhost:3000/galleries/123 的路径来查看并验证我们的画库展示是否正常工作。

在该页面上，我们将显示一个画库标题，即我们在 Show 方法中定义的那个，如果我们更改路径中的 ID，标题也会随之更新。展示页完成后，我们就准备好编写代码了，允许我们通过 ID 从数据库中检索画库。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

已完成 - book.usegolang.com/14.7.2

更改 - book.usegolang.com/14.7.2-diff

## 14.7.3 通过 ID 查找画库

我们的目标是在 GalleryService 中添加一个方法，允许我们通过 ID 查找现有的画库。这与我们为 UserService 编写 ByID 方法几乎相同，唯一的区别在于用于从数据库检索信息的资源类型。GORM 将根据该资源的类型决定使用哪个数据库表。我们首先通过向 GalleryDB 接口添加 ByID 方法。

```
$ atom models/galleries.go
// GalleryDB 用于与画库数据库交互。
// 对于大多数单个画库查询：
// 如果找到了画库，我们将返回 nil
// 如果没有找到画库，我们将返回 ErrNotFound
// 如果发生其他错误，我们将返回一个关于错误的详细信息。
// 这可能由 models 包生成。

type GalleryDB interface {
    ByID(id uint) (*Gallery, error)
    Create(gallery *Gallery) error
}
```

我们的 ByID 方法接受一个无符号整数作为 id 参数，然后返回请求的画库或错误。可能的错误与 UserDB 接口中的相同，但在这里进行记录也是一个好主意。接下来我们需要在 galleryGorm 类型上实现此方法。

```go
func (gg *gallerygorm) ByID(id uint) (*Gallery, error) {
    var gallery Gallery
    db := gg.Where("id = ?", id)
    err := db.First(&gallery)
    if err != nil {
        return nil, err
    }
    return &gallery, nil
}
```

正如早期提到的，ByID 方法与我们为 userGorm 类型实现的几乎相同，但这里使用的是 Gallery 变量而不是 User。当我们调用 first 方法时（它随后调用 GORM 提供的 First 方法），该变量的类型将用于确定我们要访问的数据库表。由于我们没有看到那部分代码，因为它发生在 gorm 包内部。

我们在这一节中要做的最后一件事是更新画库控制器的 Show 方法，以查找并渲染真实的画库。

```
$ atom controllers/galleries.go
```

```go
func (g *Galleries) Show(w http.ResponseWriter, r *http.Request) {
	vars := mux.Vars(r)
	idStr := vars["id"]
	id, err := strconv.Atoi(idStr)
	if err != nil {
		http.Error(w, "Invalid gallery ID", http.StatusNotFound)
		return
	}
	// 我们的新代码从这里开始
	gallery, err := g.gs.ByID(uint(id))
	if err != nil {
		switch err {
			case models.ErrNotFound:
				http.Error(w, "Gallery not found", http.StatusNotFound)
			default:
				http.Error(w, "Woops! Something went wrong.", http.StatusInternalServerError)
		}
		return
	}
	var vd views.Data
	vd.Yield = gallery
	g.ShowView.Render(w, vd)
}
```

现在不是自己构建画库，而是使用我们的画库服务来检索。ByID 方法期望一个无符号整数，但我们的 id 存储为有符号整数（int），因此在传递给 ByID 方法之前我们需要将其转换为 uint。

一旦从 ByID 调用返回结果，我们就会检查是否有错误。如果发生错误且为 ErrNotFound，我们将渲染一个找不到画库的消息并返回 404 (StatusNotFound) 状态码。如果错误是其他内容，目前我们将渲染一个通用错误消息，因为我们没有相应的备用视图。

用于渲染 ShowView 的其余代码保持不变，但请记住，只有提供有效的画库 ID，我们的新 Show 方法才能工作！这意味着你需要使用新的画库表单创建一个画库，并在访问画库页时使用该 ID。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/14.7.3

更改 - book.usegolang.com/14.7.3-diff

## 14.7.4 生成参数 URL

在本节中，我们将学习如何在用户创建画库后自动将其重定向到该画库。例如，在用户创建一个画库并被分配 ID 34 后，我们可能通过下面的代码手动将他们重定向到那里。

```go
gallery := ...
path := fmt.Sprintf("/galleries/%d", gallery.ID)
http.Redirect(w, r, path, http.StatusFound)
```

这是因为 Sprint 函数会将 %d 替换为画库 ID，为我们生成一个类似 "/galleries/34" 的路径。这种方法的缺点是，如果我们以后将路径更改为类似 "/albums/34"，我们就必须找到所有这样的代码并更新它。

与其以这种方式编写代码，不如编写一个简单的函数来创建这些路径并在整个代码中使用它们。例如，我们可能使用以下代码来创建我们的画库路径。

```go
func galleryPath(id uint) string {
  return fmt.Sprintf("/galleries/%d", id)
}
```

