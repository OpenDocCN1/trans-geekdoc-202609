
```
ServeHTTP(ResponseWriter, *Request)
```

这听起来就像我们的 `views.View` 类型想要的——一个接收 `http` 响应写入器和请求的函数——因此似乎我们只需要为 `views.View` 编写一个 `ServeHTTP()` 方法。

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

重启你的应用程序并验证它是否正常。你仍然应该能够首页和联系页面，但现在它们应该通过静态控制器中的 `views.View` 类型的 `ServeHTTP` 方法提供。

### 7.5.2 简化新视图的创建

打开你的两个控制器（`users.go` 和 `static.go`）并查看调用 `views` 包提供的 `NewView` 函数的代码。你发现这两段代码之间有什么共同点吗？

如果你查看传递这些函数调用的视图路径，你会发现它们有很多共同点。它们都以前缀 (`views/`) 开头，并且都以相同的文件扩展名 (`.shtml`) 结束。由于我们不打算在 `views` 目录之外视图文件，并且打算使用另一个模板扩展（使用多个将非常困惑），如果我们能稍微简化这些代码以不再需要这些信息，那就太好了。我们可能会调用：

```
views.NewView("bootstrap", "users/new")
```

为了实现这一点，我们需要更新我们的视图源代码。

我们要做的第一件事是添加一个变量，用于存储所有变量所在的目录。我们将其命名为 `TemplateDir`。相关代码见列表 7.33。

## 列表 7.33: view.go 中的模板变量

```go
var (
    LayoutDir string = "views/layouts/"
    TemplateDir string = "views/"
    TemplateExt string = ".gohtml"
)
```

我们需要一个函数，可以接收传递给 `NewView` 函数的文件，并更新它们以自动添加 `views/` 前缀并追加 `.gohtml` 后缀。我们将此函数命名为 `addTemplatePath`，它接受一个参数 - 代表我们模板文件的字符串切片。`addTemplatePath` 将遍历切片中的每一个字符串，并为切片中的每个项设置一个新值，前面加上 `views/`。相关代码见列表 7.34。

### 框 7.10. 为什么我们不需要切片指针？

大多数情况下，如果我们想修改传递给函数的数据，将需要使用指针变量，那么为什么我们在处理传入 `addTemplatePath` 函数的切片时不需要这样做呢？

在底层，切片实际上通过指针引用一个数组。当你尝试更改切片的大小时，更改将不会持久，但如果你修改切片内部的某些数据，你最终会修改所引用的数组中的数据。

## 7.5. 清理并创建静态控制器

你可以在此处阅读更多信息：https://www.calhoun.io/why-are-slices-sometimes-altered-when-passed-by-value-in-go/

## 列表 7.34: 添加 views 目录

```go
// addTemplatePath 接收一个字符串切片，
// 代表模板的文件路径，它会在切片的中的每个字符串
// 前面添加 TemplateDir
// 例如输入 ("home") 将导致输出
// ("views/home" 如果 TemplateDir == "views/
func addTemplatePath(files []string) {
  for i, f := range files {
    files[i] = TemplateDir + f
  }
}
```

接下来，我们将编写一个类似的函数，但不是添加 views 目录前缀，而是追加模板扩展名后缀。我们将此函数命名为 `addTemplateExt`。此代码见列表 7.35。

## 列表 7.35: 追加 .gohtml 扩展

```go
// addTemplateExt 接收一个字符串切片，
// 代表模板的文件路径，它会在切片的每个字符串
// 后面追加 TemplateExt 扩展
// 例如输入 ("home") 将导致输出
// ("home.gohtml" 如果 TemplateExt == ".gohtml"
func addTemplateExt(files []string) {
  for i, f := range files {
    files[i] = f + TemplateExt
  }
}
```

我们还没有使用这两个函数中的任何一个，让我们更新 `NewView` 来利用它们。此代码见列表 7.36。

## 第 7 章：创建注册页面

### 列表 7.36: 使用视图文件路径助手

```go
func NewView(layout string, files ...string) *View {
    addTemplatePath(files)
    addTemplateExt(files)
    files = append(files, layoutFiles()...)
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

最后，我们需要更新控制器，以便它们在创建视图时不传递不必要的数据。

```bash
$ atom controllers/users.go
```

更新用户控制器中的 `NewUsers` 函数，使得对 `NewView` 函数的调用不再传递 views 前缀或 `.gohtml` 扩展。这见列表 7.37。

## 列表 7.37: 清理 NewUsers() 函数

```go
func NewUsers() *Users {
    return &Users{
        NewView: views.NewView("bootstrap", "users/new")
    }
}
```

我们需要对静态控制器中的视图执行相同的操作。

## 7.5. 清理并创建静态控制器

```bash
$ atom controllers/static.go
```

这次我们将更新 `NewStatic` 函数。首页和联系页面视图都需要。相关代码见列表 7.38。

## 列表 7.38: 清理 NewStatic() 函数

```go
func NewStatic() *Static {
  return &Static{
    Home: views.NewView("bootstrap", "static/home"),
    Contact: views.NewView("bootstrap", "static/contact"),
  }
}
```

我们的代码应该处于良好状态，可以重启服务器并测试一切了，所以尽管去这样做。

```bash
$ go run main.go
```

如果有错误，你可能会在服务器启动时立即看到错误，但请访问首页、联系和注册页面以验证它们是否正常工作。如果页面是空白，请检查服务器日志是否有任何错误。

### 框 7.11. 潜在错误

如果你收到类似“no such file or directory”的错误信息，这可能意味着你没有更新在控制器中创建的所有视图，或者你的 `view.go` 源文件中存在 bug。

查看你的代码尝试打开的文件，这应该会给你提供关于哪里出错的线索。例如，如果它尝试访问的文件以 `views/views/...`（重复的“views”目录）开头，可能意味着你调用 `NewView` 时传递了 `views/` 前缀，然后 `NewView` 函数调用了 `addTemplatePath` 前缀，导致了前缀重复。

同样，如果文件以 `.gohtml` 结尾，可能意味着你在传递文件时带了扩展名，然后 `NewView` 函数又追加了一个扩展名。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/7.5.2

## 7.6 练习

我们在这一章中涵盖了很多内容，但在最后我们开始重复许多在本章开头学过的东西。例如，创建一个静态控制器与创建一个用户控制器并没有多大。虽然我们从技术上说没有使用框架，但我们所做的事情与使用框架非常相似。

基于此，我们将专注于一些可以帮助你巩固所学内容的练习。对于每个任务，你需要修改几个文件，但不需要进行大量的更改。相反，你应该完成一些简单的任务。

### 7.6.1 练习1 - 为静态控制器添加 FAQ 页面

就像许多应用程序都有联系页面一样，我们的应用程序可能需要一个 FAQ 页面。为 FAQ 页面创建一个模板（html），然后将其添加到静态控制器。

一旦将其添加到静态控制器，请更新你的 `main.go` 代码，使路由器在访问 `/faq` 路径时引导用户进入该页面。

### 7.6.2 练习2 - 为画廊创建一个新控制器

我们最终创建一个画廊资源，包括它的控制器，但在此期间我们将画廊控制器作为一个练习。

创建一个新的画廊控制器，它有一个动作，即由 `New` 方法表示的动作。

你首先需要创建一个声明画廊控制器的文件。在该文件中，你想为画廊控制器创建一个类型，然后创建一个用于创建画廊控制器的函数。

之后，你需要为你创建的类型创建 `New()` 方法。你从技术上可以像我们处理 FAQ 页面那样只用视图来实现，但我希望你写一个方法，以便也能获得一些练习。

在 `New` 方法内部，你需要渲染一个视图，因此你需要创建一个。我建议使用新用户模板作为指南。

最后，你需要将 `New` 方法注册到路由器中。使用路径 `/galleries/new` 和 HTTP GET 方法。

### 7.6.3 练习清理

此后我们将不再使用练习中的任何代码，因此在完成练习后，可以自由删除所有内容。这些练习只是为了帮助我们巩固所学的内容。

## 第 8 章

## 数据库简介

一个不保存任何数据的 Web 应用程序将毫无趣味，因此我们需要讨论如何在不同的 Web 请求之间实际持久化数据的方法。

从技术上讲，我们可以使用任何工具来存储数据，但每种方法都有其独特的优缺点。这意味着并没有一个真正的“最佳”选项，相反，我们需要根据特定的需求找到最佳的整体解决方案。

例如，如果我们想要一个非常简单的数据存储方案，可以将所有数据存储在一个 JSON 文本文件中。如果数据量不多，这种方法会非常快，并允许我们使用文本编辑器轻松地手动读取和编辑数据。

这种方法的缺端是，如果我们开始存储过多的数据，它可能会变慢；而且，如果两个应用程序尝试同时写入该文件，我们很容易遇到写入冲突。

使用 JSON 文件来持久化我们的数据可能是一个坏主意，但它有助于说明：每种选项在某些情况下是有效的，而在另一些情况下是不行的。数据库也是如此。没有什么是所谓的“万灵银弹”，无论别人怎么告诉你，单一的数据库都无法适用于所有情况。

## 第 8 章：数据库简介

即使是像 Google 和 Facebook 这样的公司，也必须根据其需求利用多种不同的数据存储策略。

## 8.1 我们的 Web 应用将使用 PostgreSQL

我们的 Web 应用程序将使用 SQL¹ 数据库。具体来说，我们将使用 PostgreSQL²，但请记住，这并不意味着以后所有的应用程序都需要使用 SQL。事实上，一旦你读完这本书，我鼓励你查看其他几个数据库，以便对世界上还有什么有所直；；SQL 通常是我的首选。

我选择在本书中使用 SQL 是出于几个原因的。首先，它是一个非常受欢迎的数据库，因此有大量的资源可用。这很重要，因为本书的重点是教你使用 Go 进行 Web 开发，尽管我很想说在本书内同时也教 SQL，但现实中这是不可行的。相反，如果你不熟悉 SQL，我建议你查看第 8.1 框。它将为你提供几个不同的资源，旨在帮助你熟悉 SQL。

框 8.1。学习 SQL 的资源。

如果你不熟悉 SQL，我建议查看以下资源。你不需要读完它们，也不需要成为 SQL 专家。相反，你的目标应该是学习足够的知识，以理解如何在数据库内部创建、更新和查询数据。

- 使用 Golang 使用 PostgreSQL - 这是一个系列教程，涵盖了在各种操作系统上安装 PostgreSQL、SQL 的基础知识，然后解释了如何用 Go 代码访问 SQL 数据库的基础。你可以在此处找到课程：http://www.calhoun.io/using-postgresql-with-golang/

- Codecademy 的 Learn SQL 课程 - 这是一个交互式课程，包含一些小项目和小测试，让你熟悉 SQL。你可以在此处找到：https://www.codecademy.com/lrm/learn-signup

- w3schools 有一个 SQL 课程，涵盖了 SQL 的几乎每一个方面。与 Codecademy 类似，大多数资源允许你尝试代码示例以查看它们的实际作用。你可以在此处找到 SQL 课程：http://www.w3schools.com/sql/

- 汗达学院（Khan Academy）也提供 SQL 课程，可以在此处找到：https://www.khanacademy.org/computing/computer-programming/sql

- 如果没有人发布，Quora 上有一个题为“我如何学习 SQL？”的问题，它有 100+ 多个答案以及大量的潜在资源列表，可以在此处查看：https://www.quora.com/How-do-I-learn-SQL

我们使用 SQL 的第二个原因是它在扩展性和可用性的平衡。虽然其他数据库在处理十亿用户时可能表现更好，但那是以复杂性为代价的。另一方面，PostgreSQL 兼顾了良好的扩展性和可用性，且不会在使用或设置时变得过于复杂。虽然它可能无法轻松地扩展到十亿用户，但可以相对容易地扩展到数百万用户，并且非常容易适应几乎任何用例。这意味着我们可以安全地选择，因为知道在规模变得非常大之前，我们不太遇到任何重大问题。到那时，我们将对自己的局限性有更好的了解，并能够就哪个数据库满足我们的需求做出明智的决策。

最后，我们选择使用 SQL 是因为它在 Go 社区中得到了很好的支持。标准库提供了官方的 `database/sql` 包，还有许多构建在 SQL 之上的第三方包，它们简化了读取、写入和迁移数据等操作。

虽然我们不会使用标准库的 `database/sql` 包，而是将选择 GORM，但书中的代码设置方式允许你相对容易地将所有 GORM 代码替换为 `database/sql` 包，所以如果你希望使用更原始的 SQL，请不要灰馁。
