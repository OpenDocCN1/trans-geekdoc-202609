
```go
func (g *Galleries) galleryByID(w http.ResponseWriter,
	r *http.Request) (models.Gallery, error) {
	vars := mux.Vars(r)
	idStr := vars["id"]
	id, err := strconv.Atoi(idStr)
	if err != nil {
		http.Error(w, "Invalid gallery ID", http.StatusNotFound)
		return nil, err
	}
	gallery, err := g.gs.ByID(uint(id))
	if err != nil {
		switch err {
		case models.ErrNotFound:
			http.Error(w, "Gallery not found", http.StatusNotFound)
		default:
			http.Error(w, "Whoops! Something went wrong.", http.StatusInternalServerError)
			return nil, err
		}
	}
	return gallery, nil
}
```

正如我们所看到的，`galleryByID` 中几乎所有的代码都直接来自我们的 `Show` 方法。这意味着我们可以更新 `Show` 方法来使用 `galleryByID` 方法，而不是自己完成所有这些工作。

```go
func (g *Galleries) Show(w http.ResponseWriter, r *http.Request) {
	gallery, err := g.galleryByID(w, r)
	if err != nil {
		// 对我们来说，只需要在这里返回即可。
		return
	}

	var vd views.Data
	vd.Yield = gallery
	g.ShowView.Render(w, vd)
}
```

通过将代码移动到可重用的方法，我们能够大大简化 `Show` 方法，但我们仍然需要进行快速快速检查以判断我们是否收到了画库。如果是，我们就可以渲染 `Show` 视图。否则，我们将依靠 `galleryByID` 方法来渲染错误并返回。

回到 `Edit` 方法，我们在这里也将使用 `galleryByID` 方法。在获取画库后，我们将像在 `Show` 方法中完全一样检查错误，然后从请求上下文中（request context）中获取用户，并验证该用户是否有权访问此画库。我们可以通过验证画库的 `UserID` 字段是否与用户的 ID 相同来实现，这意味着该用户拥有该画库。如果事实如此，我们将渲染一个错误，否则我们将继续。

```go
// GET /galleries/{id}/edit
func (g *Galleries) Edit(w http.ResponseWriter, r *http.Request) {
	gallery, err := g.galleryByID(w, r)
	if err != nil {
		// 对我们来说，只需要在这里返回即可。
		return
	}

	user := context.User(r.Context())
	if gallery.UserID != user.ID {
		http.Error(w, "You do not have permission to edit this gallery", http.StatusForbidden)
		return
	}

	var vd views.Data
	vd.Yield = gallery
	g.EditView.Render(w, vd)
}
```

## 14.8. 编辑画库

完成 - book.usegolang.com/14.8.2

更改 - book.usegolang.com/14.8.2-diff

### 14.8.3 更新画库模型

在本节中，我们将编写必要的代码将画库的更改推送到数据库中。我们将再次使用验证，因为我们不允许使用无效数据更新画库。

我们将从 galleries 模型源码开始，在 `GalleryDB` 接口中添加一个 `Update` 方法。

```go
$ atom models/galleries.go
```

```go
type GalleryDB interface {
  ByID(id uint) (*Gallery, error)
  Create(gallery *Gallery) error
  Update(gallery *Gallery) error
}
```

接下来我们需要编写该方法。我们将从简单的部分开始——`galleryGorm` 的实现。

```go
func (gg *galleryGorm) Update(gallery *Gallery) error {
  return gg.db.Save(gallery).Error
}
```

在新的更新中，我们使用了 GORM 提供的 `Save` 方法，并返回在此过程中遇到的任何错误。

现在，我们需要为 `Update` 方法添加验证，我们通过向 `galleryValidator` 类型添加一个 `UpdateValidator` 方法来实现。我们将使用两个已经创建的验证；第一个将验证 `UserID` 字段是否已正确设置，第二个将验证是否为画库提供了标题。

```go
func (gv *galleryValidator) Update(gallery *Gallery) error {
	err = runGalleryValidations(gallery,
		gv.userIDRequired,
		gv.titleRequired)
	if err != nil {
		return err
	}
	return gv.GalleryDB.Update(gallery)
}
```

在 `GalleryService`（通过嵌入的 `GalleryDB`）中添加 `Update` 方法后，我们可以回到 galleries 控制器，并在我们的 `Update` 操作中使用此新方法。

```go
$ atom controllers/galleries.go
```

我们只修改 `Update` 方法的最后部分（我们之前在那里放置了 TODO），该方法的前半部分为了简洁起见而留了空白。

```go
func (g *Galleries) Update(w http.ResponseWriter, r *http.Request) {
	// ... 这前半部分保持不变

	gallery.Title = form.Title
	err = g.gs.Update(gallery)
	// 如果有错误提示，它将是一个错误。否则
	// 我们仍然会渲染一个提示，但它将是
	// 一个成功消息。
	if err != nil {
		vd.SetAlert(err)
	} else {
		vd.Alert = views.Alert{
			Level:   views.AlertLvSuccess,
			Message: "Gallery successfully updated!",
		}

		// 无论是否有错误，我们都要使用更新后的信息
		// 渲染 EditView。
		g.EditView.Render(w, vd)
	}
}
```

522 第14章 创建画库资源

现在我们的代码支持编辑画库了！重启服务器并进行测试运行。然后返回查看画库页面，验证在提交编辑画库表单时，它是否确实持久化新标题。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

- 完成 - book.usegolang.com/14.8.3

- 更改 - book.usegolang.com/14.8.3-diff

## 14.9 删除画库

就像 `Update` 操作一样，为我们的画库实现删除功能将涉及我们的 models 包、galleries 控制器和一个视图模板。与我们的更新操作不同，我们不会创建一个创建一个视图；相反，我们将在编辑画库页面上添加一个删除按钮，因为如果你想删除资源，编辑页面是一个相当常见的地方。

这次，我们将从在 models 包中实现 `Delete` 方法开始。

```go
$ atom models/galleries.go
```

首先，我们向 `GalleryDB` 接口中引入该方法。

```go
type GalleryDB interface {
  ByID(id uint) (*Gallery, error)
  Create(gallery *Gallery) error
```

## 14.9. 删除画库

```go
Update(gallery *Gallery) error
Delete(id uint) error
}
```

然后，我们在 `galleryGorm` 类型上实现它。

```go
func (gg *galleryGorm) Delete(id uint) error {
	gallery := Gallery(Model: gorm.Model{ID: id})
	return gg.db.Delete(&gallery).Error
}
```

并且我们编写了一个验证函数，确保我们不会尝试用无效 ID（为 0 的 ID）进行删除。

```go
func (gv *galleryValidator) nonZeroID(gallery *Gallery) error {
	if gallery.ID <= 0 {
		return ErrIDInvalid
	}
	return nil
}

func (gv *galleryValidator) Delete(id uint) error {
	var gallery Gallery
	gallery.ID = id
	if err := runGalleryValidations(&gallery, gv.nonZeroID); err != nil {
		return err
	}
	return gv.galleryDB.Delete(gallery.ID)
}
```

接下来，我们将引入一个控制器来处理删除请求。

```go
$ atom controllers/galleries.go
```

我们将处理方法命名为 `Delete`，在我们的方法中，我们需要查找画库，验证用户是否有权限删除它，然后使用我们 GalleryService 提供的方法。

524 第14章 创建画库资源

```go
import (
	"fmt"
)

// POST /galleries/:id
func (g *Galleries) Delete(w http.ResponseWriter, r *http.Request) {
	gallery, err := g.gs.ByID(id)
	if err != nil {
		// 如果有错误提示，它将是一个错误。否则
		// 我们仍然会渲染一个提示，但它将是
		// 一个成功消息。
		vd.SetAlert(err)
	} else {
		vd.Alert = views.Alert{
			Level:   views.AlertLvSuccess,
			Message: "Gallery successfully updated!",
		}

		// 无论是否有错误，我们都要使用更新后的信息
		// 渲染 EditView。
		g.EditView.Render(w, vd)
	}

	// TODO: 我们最终重重到到
	// 现在我们使用：
	fmt.Fprintf(w, "Gallery successfully deleted!")
}
```

接下来，将在路由器中添加一个路由来映射我们的删除代码。

```go
$ atom main.go
```

在画库路由附近添加以下路由。

```go
r.HandleFunc("/galleries/{id:[0-9]+}/delete",
    requireMw.Apply(galleriesC.Delete)).Methods("POST")
```

最后，我们需要更新我们的编辑页面模板，并使用以下代码更新它。

```go
$ atom views/galleries/edit.html
```

```html
{{define "editForm"}}
<form action="/galleries/{{ID}}/update" method="POST">
<div class="form-group">
<label for="title">Title</label>
<input type="text" name="title" class="form-control" id="title" placeholder="What is the title?" />
</div>
<button type="submit" class="btn btn-primary">Update</button>
</form>
<!-- 这是我们新的删除按钮，它向
/galleries/{{ID}}/delete 提交 POST
请求。 -->
<form action="/galleries/{{ID}}/delete" method="POST">
<button type="submit" class="btn btn-danger">Delete</button>
</form>
{{end}}
```

## 14.10. 查看所有拥有的画廊

在最后一步中，我们将实现一个用于渲染索引页的新视图；在此过程中，我们将学习如何使用 Go 模板中的 range 动作来遍历数据切片并逐个渲染每一个项。

### 14.10.1 按用户 ID 查询画廊

为了使用用户 ID 查询画廊，我们再次需要向 `GalleryDB` 接口添加一个方法，以便在用于与数据库交互的 `GalleryService` 中可以使用。

```go
$ models/galleries.go
```

我们知道，当方法执行成功时需要返回画廊切片，因为一个用户可能有很多画廊。我们也知道在与数据库交互时可能会遇到错误，无论是因为我们的失误还是因为数据库崩溃，我们可以从一个接受用户 ID 并返回两个部分数据的方法开始。

```go
type GalleryDB interface {
	ByID(userID uint) (*Gallery, error)
	ByUserID(userID uint) ([]Gallery, error)
	Create(gallery *Gallery) error
	Update(gallery *Gallery) error
	Delete(id uint) error
}
```

接下来我们将在 `galleryGorm` 类型上实现此方法。这样做实际上与我们目前编写的代码非常相似，但我们不是在我们的 *gorm.DB 类型*上调用 `First` 方法，而是将调用 `Find` 方法。这两个方法之间的主要区别是：`First` 用于检索单个资源（第一个！），而 `Find` 旨在返回该资源的多个实例。因此，`First` 期望传入单个资源，而 `Find` 期望一个切片。

```go
func (gg *galeryGorm) ByUserID(userID uint) ([]Gallery, error) {
	var galleries []Gallery
	// 我们构建此查询的方式与我们构建
	// 单个用户查询的方式完全一样。
	db := gg.db.Where("user.id = ?", userID)
	// 真正的区别在于使用 Find 而不是 First
	// 并且传递的是切片而不是单个画廊作为
	// 参数。
	if err := db.Find(&galleries).Error; err != nil {
		return nil, err
	}
	return galleries, nil
}
```

注意：从长期来看，可能需要引入分页等功能，但当用户拥有数百个画廊时，这通常会变成问题。我通常倾向于先启动应用程序，然后再回来添加这些功能，这正是我们在本书中将做的。

我们现在不会对 `ByUserID` 方法添加任何验证，因为目前没有太大需求。如果你想，可以使用之前创建的 `nonZeroID` 验证，但与没有该验证的 `Delete` 方法不同，这样做是不必要的，因为它没有破坏性。它只会返回没有正确设置 UserID 的画廊，由于现在我们已经在 `Create` 和 `Update` 方法中有了验证，这种情况不应该发生。

如果你想验证代码是否运行正常，可以更新你的 `main.go` 源文件进行测试查询并打印结果，我们不会提交这段代码。

```go
// 这是不会提交的测试代码
tUserID := 1 // 选择一个映射到数据库中某个用户的 ID
galleries, _ := services.Gallery.ByUserID(userID)
fmt.Println(galleries)
```

## 14.10. 查看所有拥有的画廊

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/14.10.1

- 差异版 - book.usegolang.com/14.10.1-diff

### 14.10.2 添加索引处理器

接下来我们需要引入一个函数来处理指向索引页的传入 Web 请求。我们还需要该页面准备一个视图，但在下一节之前不会实现它。现在我们只需编写一个占位符（stub）。

```go
$ atom views/galleries/index.gohtml

{{define "yield"}}
TODO: 实现索引视图。
提供的数据: {{.}}
{{end}}
```

接下来我们需要将此视图添加到画廊控制器中。

```go
$ atom controllers/galleries.go
```
