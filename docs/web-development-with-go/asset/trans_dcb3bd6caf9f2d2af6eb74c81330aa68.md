

## 第 14 章：创建画库资源

```go
gs: r,
}
type Galleries struct {
	New       *views.View
	ShowView *views.View
	EditView *views.View
	gs      models.GalleryService
	r       *mux.Router
}
```

现在我们可以开始创建一个动作，用于查找画库并用它渲染编辑视图。为了实现这一点，我们需要从路径中获取用户尝试编辑的画库 ID。我们将像在 `Show` 动作中那样使用 `gorilla/mux` 来完成这一操作。事实上，我们所有用于获取 ID 并使用 `GalleryService` 查找画库的代码几乎完全相同，那么为什么我们不将其移动到一个可重用的函数中呢？

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

正如我们所看到的，galleryByID` 中几乎所有的代码都直接来自我们的 `Show` 方法。这意味着我们可以更新 `Show` 方法来使用 `galleryByID` 方法，而不是自己完成所有这些工作。

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

