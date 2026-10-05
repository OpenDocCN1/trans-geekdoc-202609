
[content]

## 13.3. 仅在需要时显示警告

我们将再次在 `New` 方法中添加这段代码。一旦我们创建了新类型，我们将创建一个实例，分配一些数据进行测试，然后将其传递给 `Render` 方法。

```go
func (u *Users) New(w http.ResponseWriter, r *http.Request) {
	type Alert struct {
		Level string
		Message string
	}
	type Data struct {
		Alert *Alert
		Yield interface{}
	}
	alert := &Alert{
		Level: "success",
		Message: "Successfully rendered a dynamic alert!",
	}
	data := Data{
		Alert: &alert,
		Yield: "this can be any data b/c its type is interface",
	}
	if err := u.New.Render(w, data); err != nil {
		panic(err)
	}
}
```

现在我们已经将这两部分数据分开了，让我们回到 bootstrap 布局并更新它以反映这一变化。

```bash
$ atom views/layouts/bootstrap.gohtml
```

我们只希望在模板中有一个非空的 `Alert` 参数时才渲染警告消息，所以我们从这里开始。如果它确实非空，我们将渲染警告模板并传递该部分数据。

```go
{{if .Alert}}
{{template "alert" .Alert}}
{{end}}
```

## 第 13 章.向最终用户显示错误

`Yield` 字段有点不同。即使它是空的，我们仍然想要渲染 `yield` 字段，因为它可能是一个带有静态数据的页面（例如首页）。在这种情况下，我们只需要使用正确的数据调用模板即可。

```html
<div class="container-fluid">
  {{if .Alert}}
    {{template "alert" .Alert}}
  {{end}}
  {{template "yield" .yield}}
  {{template "footer"}}
</div>
```

通过更新后的代码，我们告诉模板只向每个模板传递特定的数据。一旦进入该模板内部，所有传递的数据都可以通过点操作（例如 `{{.}}`）访问，这就像我们将单个字段作为参数传递给另一个函数一样。你可以通过更新新用户用户的模板来看到这一点。

```bash
$ atom views/users/new.gohtml
```

在模板定义之后直接添加以下 `h1` 标签。

```html
{{define "yield"}}
<h1>{{.}}</h1>
<!-- 模板的其余部分保持不变 -->
{{end}}
```

现在重启服务器并访问注册页面 `/signup`。你不仅会看到成功警告，还会看到我们设置在 `Yield` 字段中的字符串 "this can be any data b/c its type is interface"，因为我们在 `new.gohtml` 模板中通过点（`. `）访问了它。

在下一节中，我们将开始向为视图数据使用更持久的数据结构方向过渡，在此期间，本节希望能够让你初步了解我们如何开始在模板中添加和交互数据，从而影响页面的渲染方式。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/13.3
- 更改版 - book.usegolang.com/13.3-diff

## 13.4 用于视图的更持久的数据类型

在之前的章节中，我们探索了预定义数据类型在渲染视图时是非常有用的。通过它，我们仍然可以在 `Yield` 字段中放置更多动态页面特定数据，同时在我们需要向用户显示警告消息时，仍然拥有像 `Alert` 这样更常见的字段。

在本节中，我们将为渲染视图定义一个更持久的数据类型。我们将此结构体命名为 `Data`，并将其放在 `views` 包中，因为它被用于渲染我们的视图。在此过程中，我们还会在 `views` 包中创建一个 `Alert` 数据类型，用于渲染我们的警告。

让我们先从在 `views` 包中添加新的数据类型开始。我们将为这段代码创建一个新的源文件。

```bash
$ atom views/data.go
```

在该文件中，我们首先需要引入 `Data` 和 `Alert` 类型。目前，这些可以与我们之前在控制器中创建的完全相同。

## 第 13 章.向最终用户显示错误

```go
package views

// Data 是视图期望数据进入的顶层结构体
type Data struct {
	Alert *Alert
	Yield interface{}
}

// Alert 用于在模板中渲染 Bootstrap Alert 消息
type Alert struct {
	Level string
	Message string
}
```

到目前为止，我们允许数据以几乎任何格式进入视图，但从现在开始，我们将开始实施更多的严谨性。我们将开始期望所有视图如果传递了任何数据，都会接收一个 `Data` 对象。

在我们创建 `Alert` 类型时，为所有警告级别引入一些常量可能也是好主意。这样开发者就可以轻松地从我们 UI 支持的预定义警告级别中选择，而不用担心字符串中的拼写错误。

```go
const (
    AlertLvlError = "danger"
    AlertLvlWarning = "warning"
    AlertLvlInfo = "info"
    AlertLvlSuccess = "success"
)
```

现在让我们更新用户控制器中的 `New` 方法以使用我们的新数据类型。

```bash
atom controllers/users.go
```

我们不再需要在那部分代码中定义 `Data` 和 `Alert` 类型了，我们也不真的需要添加任何新代码。我们真正需要的

## 13.4 用于视图的更持久的数据类型

就是更新创建 `Alert` 和 `Data` 对象的代码，以使用在 `views` 包中定义的那些。我们还可以更新代码以使用其中一个常量警告级别。

```go
func (u *Users) New(w http.ResponseWriter, r *http.Request) {
	alert := views.Alert{
		Level: views.AlertLvlSuccess,
		Message: "Successfully rendered a dynamic alert!",
	}
	data := views.Data{
		Alert: &alert,
		Yield: "this can be any data b/c its type is interface",
	}
	if err := u.NewView.Render(w, data); err != nil {
		panic(err)
	}
}
```

此时我们可以重启服务器，我们的代码将能够工作了，但我们还有最后一件事要做。我们更新 `views` 包中的 `Render` 方法，以确保所有传递的数据都封装在 `Data` 对象中。

```go
func (v *View) Render(w http.ResponseWriter, data interface{}) error {
	w.Header().Set("Content-Type", "text/html")
	switch data.(type) {
	case Data:
		// 无操作
	default:
		data = Data{
			Yield: data,
		}
	}
	return v.Template.ExecuteTemplate(w, data)
}
```

## 第 13 章向最终用户显示错误

在更新后的代码中，我们添加了一个检查任何传递数据的底层类型的 switch。我们真正关心的情况是数据是否为 `Data` 类型。如果是 `Data` 类型，我们什么都不需要做。如果是其他类型，我们将其封装在 `Data` 对象中，并赋值给 `Yield` 字段。简而言之，这是一种便利，允许我们使用如下代码渲染视图：

```go
someView.Render(w, "this is page-specific data!")
```

## 13.5 处理表单中的错误

现在我们准备好为应用程序实现正确的错误处理了，但首先我们需要移除一些用于演示警告和视图数据代码。

打开新用户模板并删除我们在 13.3 节中添加的 `h1` 标签。

```bash
$ atom views/users/new.gohtml
```

```html
{{define "yield"}}
<!-- 删除下面的 h1 标签 -->
<!-- {{.}} -->
<!-- ... 代码的其余部分保持不变 -->
{{end}}
```

然后清理控制器包中的 `users.go` 源文件。在文件内部，我们将移除 `New` 方法中用于创建警告的代码。

```bash
$ atom controllers/users.go
```

移除代码后，你的 `New` 方法应该恢复到原始原始版本。

```go
func (u *Users) New(w http.ResponseWriter, r *http.Request) {
  if err := u.NewView.Render(w, nil); err != nil {
    panic(err)
  }
}
```
