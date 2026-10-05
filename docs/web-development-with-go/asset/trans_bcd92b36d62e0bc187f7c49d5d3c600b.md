

```
$ atom views/contact.gohtml
```

我们在这里做的同样的事情——如列表 6.17 所示，为我们的模板 yield 命名。

## 列表 6.17：将 contact.gohtml 转换为命名模板。

```go
{{define "yield"}}
如需与我们联系，请发送邮件至：
<a href="mailto:support@lenslocked.com">support@lenslocked.com</a></a></a>
{{///}}

{{template "footer"}}
{{end}}
```

接下来，我们需要更新我们的 bootstrap 布局以渲染 yield 模板。

```
$ atom views/layouts/bootstrap.gohtml
```

然后我们用“内容将显示在这里”的注释部分更新为列表 6.18 所示的代码。列表中显示了整个 `div`，但你实际上只需要添加模板行即可。

## 列表 6.18：在 bootstrap.gohtml 中使用 yield。

```html
<div class="container-fluid">
{{template "yield" .}}
</div>
```

注意：在列表 6.18 中，我们在模板名称之后添加了 `.`，是为了告诉程序，我们希望将传递给 bootstrap 模板的任何数据传递给 yield 模板。如果没有这个，yield 模板将无法访问我们传递到模板中的任何数据。

## 6.3. 创建可重用的 BOOTSTRAP 布局

如果我们现在尝试运行代码，最终将得到一个空白页面。为什么会发生这种情况呢？

既然我们已经将首页和联系页模板都命名为 `yield`，我们需要告诉模板在渲染内容之前执行这些命名的模板。实现此点的一种方法是使用 `Template` 类型提供的 `ExecuteTemplate` 方法。

```go
// 注意：我们不会在应用中使用这段代码，所以你
// 不需要将其添加到你的应用中。
homeView.Template.ExecuteTemplate(w, "yield", nil)
```

这将告诉我们的模板，我们想要执行一个名为“yield”的模板，将结果写入 `w`，并使用数据 `nil`。

我们将更新代码来执行类似的操作的操作，但我们将把想要执行的模板名称存储在稍早创建的 `View` 类型中。

为了做到这一点，我们需要对 `View` 类型进行一些更改。首先，我们将存储视图想要执行的模板。我们可以随心所欲地命名，因为我们知道这通常指的是布局模板（bootstrap），我们将此字段命名为 `Layout`。

打开 `views.go` 并通过添加 `Layout` 字段来更新 `View` 类型，如列表 6.19 所示。

列表 6.19：向 NewView 中添加 Layout
```go
type View struct {
    Template *template.Template
    Layout string
}
```

³://golang.org/pkg/html/template/#Template.ExecuteTemplate

## 第 6 章：创建我们的第一个视图

我们需要更新首页和联系函数，以便在 `main.go` 中执行此布局，并参考列表 6.20 来执行此操作。

## 列表 6.20：在 handlers 中使用 Layout。

```go
func home(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html")
	err := homeView.Template.ExecuteTemplate(w,
	homeView.Layout, nil)
	if err != nil {
		panic(err)
	}
}
func contact(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html")
	err := contactView.Template.ExecuteTemplate(w,
	contactView.Layout, nil)
	if err != nil {
		panic(err)
	}
}
```

虽然我们的代码现在可以编译，但我们还没有完成更改。我们仍然没有为任何视图设置 `Layout` 字段，因此如果我们尝试运行代码，它仍然不知道我们想要渲染哪个布局，并且很可能会在某处发生 panic（恐崩溃）。

为了解决这个问题，我们将更新 `view.go` 文件中的 `NewView` 函数。我们在这里要做做两处更改：

- 1. 我们将接受一个 layout 参数，以便我们可以在创建的视图上设置它。
- 2. 我们将把 bootstrap 布局添加到正在解析的模板文件切片中，以便它可以用于渲染。

这些更改的代码在列表 6.21 中。

## 6.3. 创建可重用的 BOOTSTRAP 布局

列表 6.21：向 NewView() 添加 Layout。
```go
func NewView(layout string, files ...string) *View {
	files = append(files,
	"views/layouts/footer.gohtml",
	"views/layouts/bootstrap.gohtml")
	t, err := template.ParseFiles(files...)
	if err != nil {
		panic(err)
	}

	return &View{
	Template: t,
	Layout: layout,
	}
}
```

再次，我们做了一个导致代码破坏的更改。糟糕！

由于我们更新了 `NewView` 函数，我们需要更新任何调用该函数的代码。我们在 `main` 函数中调用了 `NewView`，所以我们来到 `main.go` 并参考列表 6.22 更新 `main` 函数。

我们将为所有视图使用刚刚创建的“bootstrap”布局，这就是为什么它被添加进去的原因，我们在调用时使用了它。

列表 6.22：传递 layout 给 NewView。
homeView = NewView("bootstrap", "views/home.gohtml")
contactView = NewView("bootstrap", "views/contact.gohtml")
```

最后，完成这些更改后，停止并重启服务器。

```
$ go run main.go
```

在完成这些更改后，我们的代码应该正常运行。

