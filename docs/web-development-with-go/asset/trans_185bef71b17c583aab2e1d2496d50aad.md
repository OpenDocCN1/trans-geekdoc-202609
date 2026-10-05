

## 7.4. 处理注册表单

```
$ atom controllers/users.go
```

我们仍然想要创建 `SignupForm` 变量，但在之后我们调用 `parseForm`，检查错误，并打印我们的表单数据。这样要简单得多！

最终代码应该与列表 7.26 一致。

```
Listing 7.26: 在 Create 中使用 parseForm()
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
	var form SignupForm
	if err := parseForm(r, &form); err != nil {
		panic(err)
	}
	fmt.Fprintln(w, "Email is", form.Email)
	fmt.Fprintln(w, "Password is", form.Password)
}
```

在这段代码中我们仍然需要处理错误，但我们能够将其减少到在 `Create()` 动作内部进行一次错误检查，这稍微简化了事情。此外，我们现在有了一种方法解析任何表单，而无需重写该代码。

最后一段代码还更新了我们的打印语句，以证明我们确实可以访问 `SignupForm` 实例上的每个字段，并且它被分配了正确的值。

本章剩下的唯一工作就是清理我们的代码并尝试几个练习题。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/7.4.5
- 更改 - book.usegolang.com/7.4.5-diff

## 7.5 清理和创建静态控制器

到目前为止，我们一直在处理用户控制器，但在本节中，我们将查看如何使用控制器来处理那些并不真正映射到用户等资源的页面，而是更接近 Web 应用程序中静态页面的页面。

一个很好的例子是你的联系页面。你可能可以将其放在诸如咨询控制器（inquiries controller）之下，因为用户通过它找到如何进行咨询的方法，但这个控制器最终只有一个动作——显示你所有联系信息的页面。

与其创建许多可能导致混乱的非必要控制器，我们将创建一个控制器来持有所有不是完全静态但非常接近静态页面的页面。我们将将其命名为静态控制器（static controller），在其中我们将为首页和联系页设置动作。

### 7.5.1 创建静态控制器

就像之前我们创建用户控制器一样，我们的静态控制器将位于 `controllers` 包中。在 `controllers` 目录内创建并打开一个新的源代码文件用于你的静态控制器。

```
$ atom controllers/static.go
```

我们需要做的第一件事是声明 `Static` 类型。在其中我们需要存储两个不同的视图——首页视图和联系视图。然后，就像我们处理用户时做一样，我们将创建一个 `NewStatic` 控制器，包括初始化我们的视图。

**Listing 7.27:** 开始创建静态控制器
```go
package controllers

import "lenslocked.com/views"

func NewStatic() *Static {
	return &Static{
		HomeView: views.NewView(
			"bootstrap", "views/static/home.shtml"),
		ContactView: views.NewView(
			"bootstrap", "views/static/contact.shtml"),
	}
}

type Static struct {
	HomeView *views.View
	ContactView *views.View
}
```

接下来，我们需要将视图移动到正确的位置。我们将遵循之前的模式，因此 `home.shtml` 和 `contact.shtml`（都在 `views` 目录下）都将被移动到 `static` 目录，我们静态控制器的所有模板文件将存那里。为了这样做，我们需要创建 `views/static` 目录，然后将我们的 `.shtml` 文件移动到新目录。

**Listing 7.28:** 移动静态控制器模板
```bash
$ mkdir views/static
$ mv views/home.shtml views/static
$ mv views/contact.shtml views/static
```

接下来，我们需要在控制器内部编写处理函数，但如果我们查看 `main.go` 中的 `home` 和 `contact` 函数，你会发现这这两个函数都没有真正在做什么。

事实上，它们唯一做的事情就是设置内容类型并渲染视图。我们并不真的需要一个自定义函数来完成这些。如果我们可以直接使用来自 `views` 包的 `View` 类型作为处理函数并只需渲染视图，那就太好了。

为了实现这一点，我们需要弄清楚 `views.View` 类型需要实现什么接口，以便我们能够直接将 `views.View` 类型传递给我们的路由器。这意味着我们需要再次查看 `gorilla/mux` 的文档。

快速浏览此列表，我们正在寻找一个具有 `mux.Router` 类型的方法（因为这就是我们路由器的类型），该方法允许我们传递一个接口实现。

嗯，只有两个看起来合理的方法是 `Handle` 和 `HandleFunc`，但我们知道 `HandleFunc` 不是我们要的，因为我们一直在使用它，让我们检查 `Handle` 方法。

`Handle()` 方法似乎接收一个路径，然后是一个 `http.Handler` 对象。这意味着我们需要查看 `net/http` 文档并查找 `http.Handler` 类型。

`http.Handler` 是一个只需要一个方法的接口：

```
ServeHTTP(ResponseWriter, *Request)
```

这听起来就像我们的 `views.View` 类型想要的——一个接收 http 响应写入器和请求的函数——因此似乎我们只需要为 `views.View` 编写一个 `ServeHTTP()` 方法。

打开 `views.go`。

```
$ atom views.go
```

在视图源代码中，我们将为 `views.View` 编写 `ServeHTTP` 方法，这看起来就像我们在 `main.go` 中的 `home` 和 `contact` 函数一样。

**Listing 7.29:** 实现 Handler 接口
```go
func (v *View) Render(w http.ResponseWriter, data interface{}) error {
	w.Header().Set("Content-Type", "text/html")
	return v.Template.ExecuteTemplate(w, v.Layout, data)
}

func (v *View) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	if err := v.Render(w, nil); err != nil {
		panic(err)
	}
}
```

由于 `views.View` 实现了接口，我们可以更新 `main.go` 来直接使用视图。

**Listing 7.30:** main.go
```go
package main

import (
	"net/http"

	"lenslocked.com/controllers"

	"github.com/gorilla/mux"
)

func main() {
	r := mux.NewRouter()
	staticC := controllers.NewStatic()
	usersC := controllers.NewUsers()

	r.Handle("/", staticC.Home).Methods("GET")
	r.Handle("/contact", staticC.Contact).Methods("GET")
	r.HandleFunc("/signup", userC.Create).Methods("POST")

	http.ListenAndServe(":3000", r)
}
```

最后，由于我们不计划为静态控制器创建 Home 或 Contact 方法，我们可以将 `HomeView` 和 `ContactView` 重命名为 `Home` 和 `Contact`。在此之后你将需要更新 `main.go`。

**Listing 7.31:** 重命名 controllers/static.go
```go
package controllers

import "lenslocked.com/views"

func NewStatic() *Static {
	return &Static{
		Home: views.NewView(
			"bootstrap", "views/static/home.shtml"),
		Contact: views.NewView(
			"bootstrap", "views/static/contact.shtml"),
	}
}

type Static struct {
	Home *views.View
	Contact *views.View
}
```

**Listing 7.32:** 重命名 main.go
```go
r.Handle("/", staticC.Home).Methods("GET")
r.Handle("/contact", staticC.Contact).Methods("GET")
```

重启你的应用程序并验证它是否正常。你仍然应该能够首页和联系页面，但现在它们应该通过静态控制器中的 `views.View` 类型的 ServeHTTP 方法提供。

### 7.5.2 简化新视图的创建

打开你的两个控制器（users.go 和 static.go）并查看调用 `views` 包提供的 `NewView` 函数的代码。你发现这两段代码之间有什么共同点吗？

如果你查看传递这些函数调用的视图路径，你会发现它们有很多共同点。它们都以前缀 (views/) 开头，并且都以相同的文件扩展名 (.shtml) 结束。由于我们不打算在 views 目录之外视图文件，并且打算使用另一个模板扩展（使用多个将非常困惑），如果我们能稍微简化这些代码以不再需要这些信息，那就太好了。我们可能会调用：

```
views.NewView("bootstrap", "users/new")
```

为了实现这一点，我们需要更新我们的视图源代码。

