

```go
package main

import (
	"net/http"
	"net/http/httptest"
	"testing"
)

func Test_HelloWorld(t *testing.T) {
	req, err := http.NewRequest("GET", "http://example.com/foo", nil)
	if err != nil {
		t.Fatal(err)
	}

	res := httptest.NewRecorder()
	HelloWorld(res, req)

	exp := "Hello World"
	act := res.Body.String()
	if exp != act {
		t.Fatalf("Expected %s got %s", exp, act)
	}
}
```

## 练习

- 1. 修改 `HelloWorld` 的输出以打印一个参数，然后测试该参数是否被正确呈现。
- 2. 创建一个 POST 请求并测试请求是否被正确处理。

## 端到端测试

端到端测试允许我们通过整个请求周期来测试应用程序。与单元测试仅用于测试特定函数不同，端到端测试将运行请求可能经过的中间件、路由器和其他组件。

```go
package main

import (
	"fmt"
	"net/http"

	"github.com/codegangsta/negroni"
	"github.com/julienschmidt/httprouter"
)

func HelloWorld(res http.ResponseWriter, req *http.Request, p httprouter.Params) {
	fmt.Fprint(res, "Hello World")
}

func App() http.Handler {
	n := negroni.Classic()

	m := func(res http.ResponseWriter, req *http.Request, next http.HandlerFunc) {
		fmt.Fprint(res, "Before...")
		next(res, req)
		fmt.Fprint(res, "...After")
	}

	n.Use(negroni.HandlerFunc(m))

	r := httprouter.New()
	r.GET("/", HelloWorld)
	n.UseHandler(r)
	return n
}

func main() {
	http.ListenAndServe(":3000", App())
}
```

这是测试文件。它应该与您的应用程序放在同一目录中，并命名为 main_test.go。

## 练习

- 1. 创建另一个可更改请求状态的中间件。
- 2. 创建一个 POST 请求并测试请求是否被正确处理。

## 控制器

控制器在其他 Web 开发社区中是一个相当熟悉的话题。由于大多数 Web 开发人员都围绕强大的 net/http 接口聚集，因此并非许多控制器实现都广受欢迎。然而，使用控制器模式有很大好处。它允许在 net/http 处理器接口所能单独提供的基础上，构建清晰、定义良好的抽象。

### 处理器依赖

在此示例中，我们将尝试使用 Go 中的一些标准特性来构建自己的控制器实现。但首先，让我们先从我们试图解决的问题开始。假设我们正在使用之前章节中讨论过的 `render` 库：

```
var Render = render.New(render.Options{})
```

如果我们希望我们的 `http.Handler` 可以访问我们的 `render.Render` 实例，我们有几种选择。

- 1. 使用全局变量：这对小型程序来说还不错，但当程序变大时，它会迅速成为维护噩梦。
- 2. 通过闭包将变量传递给 `http.Handler`：这是一个好主意，我们大多数时候都应该使用它。实现最终看起来像这样：

```
func MyHandler(r *render.Render) http.Handler {
	return http.HandlerFunc(func(rw http.ResponseWriter, r *http.Request) {
		// now we can access r
	})
}
```

### 控制器的理由

当您的程序变大时，您会开始注意到许多 `http.Handler` 将共享相同的依赖项，并且会有许多具有相同参数的这些经过闭包处理的 `http.Handler`。我喜欢通过编写一个小型基础控制器实现来清理这一点，这给我带来了几个好处：

- 1. 允许我在具有相似目标或概念的 `http.Handler` 之间共享依赖项。
- 2. 避免使用全局变量和函数，以便于测试/模拟。
- 3. 为我提供一种更集中、更符合 Go 风格的错误处理机制。

控制器的好处在于，它们无需导入外部包就能为我们提供所有这些功能！其中大部分功能来自于对 Go 特性集的巧妙利用，即 Go 结构体和嵌入。让我们来看看实现。

```
package main

import "net/http"

// Action defines a standard function signature for us to use when creating
// controller actions. A controller action is basically just a method attached to
// a controller.
type Action func(rw http.ResponseWriter, r *http.Request) error

// This is our Base Controller
type AppController struct{}

// The action function helps with error handling in a controller
func (c *AppController) Action(a Action) http.Handler {
	return http.HandlerFunc(func(rw http.ResponseWriter, r *http.Request) {
		if err := a(rw, r); err != nil {
			http.Error(rw, err.Error(), 500)
		}
	})
}
```

就这样！这就是我们拥有控制器强大功能所需的全部实现。我们剩下要做的就是实现一个示例控制器：

```
package main

import (
    "net/http"

    "gopkg.in/unrolled/render.v1"
)

type MyController struct {
    AppController
    *render.Render
}

func (c *MyController) Index(rw http.ResponseWriter, r *http.Request) error {
    c.JSON(rw, 200, map[string]string{"Hello": "JSON"})
    return nil
}

func main() {
    c := &MyController{Render: render.New(render.Options{})}
    http.ListenAndServe(":8080", c.Action(c.Index))
}
```

### 练习

- 1. 扩展 MyController，为应用程序中的不同路由添加多个操作。
- 2. 尝试更多控制器实现，发挥创造力。
- 3. 重写 MyController 上的 Action 方法以呈现错误 HTML 页面。

## 数据库

关于 Go Web 开发，我被问得最多的问题之一是如何连接到 SQL 数据库。幸运的是，Go 的标准库中有一个出色的 SQL 包，允许我们使用大量针对不同 SQL 数据库的驱动程序。在此示例中，我们将连接到 SQLite 数据库，但语法（除去一些微小的 SQL 语义）对于 MySQL 或 PostgreSQL 数据库也是相同的。

```
package main

import (
	"database/sql"
	"fmt"
	"log"
	"net/http"

	_ "github.com/mattn/go-sqlite3"
)

func main() {
	db := NewDB()
	log.Println("Listening on :8080")
	http.ListenAndServe(":8080", ShowBooks(db))
}

func ShowBooks(db *sql.DB) http.Handler {
	return http.HandlerFunc(func(rw http.ResponseWriter, r *http.Request) {
		var title, author string
		err := db.QueryRow("select title, author from books").Scan(&title, &author)
		if err != nil {
			panic(err)
		}

		fmt.Fprintf(rw, "The first book is '%s' by '%s'", title, author)
	})
}

func NewDB() *sql.DB {
	db, err := sql.Open("sqlite3", "example.sqlite")
	if err != nil {
		panic(err)
	}

	_, err = db.Exec("create table if not exists books(title text, author text)")
	if err != nil {
		panic(err)
	}

	return db
}
```

### 练习

- 1. 利用我们 `sql.DB` 实例上的 `query` 函数提取一组行并将其映射到结构体。
- 2. 通过使用 HTML 表单，添加向数据库插入新记录的功能。
- 3. 执行 `go get github.com/jmoiron/sqlx` 并观察相对于标准库中现有 database/sql 包的改进。

## 技巧与窍门

### 包装 http.HandlerFunc 闭包

有时您希望在初始化时向 http.HandlerFunc 传递数据。这可以通过创建 `http.HandlerFunc` 的闭包来轻松实现：

```go
func MyHandler(database *sql.DB) http.Handler {
	return http.HandlerFunc(func(rw http.ResponseWriter, r *http.Request) {
		// you now have access to the *sql.DB here
	})
}
```

### 使用 gorilla/context 处理请求特定数据

我们经常需要存储和检索特定于当前 HTTP 请求的数据。使用 `gorilla/context` 来映射值并稍后检索它们。它包含一个对请求对象映射的全局互斥锁。

```go
func MyHandler(w http.ResponseWriter, r *http.Request) {
	val := context.Get(r, "myKey")

	// returns ("bar", true)
	val, ok := context.GetOk(r, "myKey")

	// ...
}
```

