
> 注意：使用 `Apply` 还是 `ApplyFn` 取决于我们的参数是 `http.Handler` 还是 `http.HandlerFunc`。

我们将 `Apply`（或 `ApplyFn`）函数的结果传递到路由器中，之前我们是在那里传递原始处理器的。

```go
r.Handle("/galleries/new", newGallery).Methods("GET")

r.Handle("/galleries", createGallery).Methods("POST")
```

> 注意：在最终代码中，我们没有将 `Apply` 函数的结果存储在中间变量中，但结果是相同的。

### 源代码

下面的链接包含了源代码以及本节中更改的所有代码的差异。

完成 - book.usegolang.com/14.6.1

更改 - book.usegolang.com/14.6.1-diff

## 14.6.2 使用 context 存储请求作用域数据

虽然我们的中间件目前会验证用户是否登录，但它并没有帮助我们确定是哪个用户登录了。在中间件通过其记忆令牌（remember token）查找用户后，结果被丢弃了。如果我们能重用这些数据并避免每次请求中多次从数据库查找同一个用户，那就太好了。Go 在 1.7 版本中为 `http.Request` 对象增加了 `context` 包，这为我们提供了这种。

### Box 14.1 Context 争议

在 context 中存储数据（特别是在中间件或网络请求期间）可能会引起争议。这存在类型安全丢失的潜在问题，尽管它在某些方面可以让代码测试变得更容易，但在另一些方面会变得更困难。

例如，测试处理程序可能会变得更容易，因为你不再需要关注生成记忆令牌以及测试由我们中间件处理的所有用户查找代码了。相反，我们可以将单个用户附加到 context 中，我们的处理程序就能按预期工作。

测试可能会变得更困难，因为对数据的预期并不总是清晰的。当我们定义这样的方法时：

```go
func doStuff(user User, years int)
```

我们明确表达了预期的数据。但通过将数据放在 context 包中，我们掩盖了其中一些需求。

## 14.6. 通过中间件要求用户

在实践中，我发现这种方式的 context 值几乎总是双赢的，而且有方法可以应对类型安全的丢失（我们将在本节中看到），也有方法可以应对隐藏的复杂性（这些在下面的链接中进行了详细讨论）。

book.usegolang.com/context

你也可以通过以下两个资源了解更多关于 `context` 包的通用信息：

- *blog.golang.org/context* - Go 官方博客
- *youtube.com/watch?v=LSzROVeraWw* - Francesc Campoy 在 justforfunc 节目中关于 context 包的介绍

`context` 包在 Go 中已经存在了很久，在 Go 1.7 之前它并不是标准库的一部分。相反，它是 `/x/packages`¹ 的一部分，这些包本质上是由 Go 核心团队创建的一系列子仓库，但在较宽松的兼容性要求下开发。

在 Go 1.7 中，该包被加入了标准库，同时 `http.Request` 对象也附加了 context，以便更方便地向请求中添加额外数据。

`context` 包旨在用于取消、截止日期以及存储请求作用域的值。我们不会将它用于前两种情况，但如果你想阅读更多关于它们的内容，我建议查看 Box 14.1 底部的链接。

我们将使用 `context` 包是为了存储请求作用域的值。具体来说，我们将在 `RequireUser` 中间件查找当前登录用户后使用它来存储该用户，然后我们就有办法在随后的处理程序中重用该数据，而无需再次进行数据库查询。

> ¹https://github.com/golang/go/wiki/SubRepositories

## 第 14 章. 创建 GALLERY 资源

当我们想要从 http 请求中获取 context 时，通过编写以下代码来实现：

```go
func someHandler(w http.ResponseWriter, r *http.Request) {
  // 这是我们获取请求 context 的方式
  ctx := r.Context()
}
```

一旦我们有了 context，就可以像处理任何其他 context 对象一样与之交互。这里需要注意的一个重要点是，当你与 context 交互时，可以创建一个派自原始 context 的 context，而不是修改原始 context。例如，如果我们想向 context 添加一个值，我们将使用 context 包提供的 `WithValue`² 函数，该函数接收一个现有的 context、一个键和一个值，然后返回一个存储了该键值的新 context。

```go
import "context"
newCtx := context.Value(ctx, "my-key", "my-value")
```

这样做之后，我们可以使用 context 对象提供的 `Value` 方法获取我们的值。

```go
// 获取存储在 "my-key" 中的值
myKey := newCtx.Value("my-key")
```

这种方法的缺点是，`context` 包将其所有数据都以空接口类型（interface{}）的形式返回。这意味着在使用返回的值之前，我们需要先将它们转换为正确的数据类型。

> ²https://golang.org/pkg/context/#WithValue

## 14.6. 通过中间件要求用户

```go
myKeyStr, ok := myKey.(string)
if !ok {
    // 类型转换失败！
}
// 否则 myKeyStr 将具有 myKey 中
    // 值的字符串表示
```

这种对类型安全的缺失是涉及 `context` 包争议的来源之一。通过在 context 中存储值，我们丢失了一些必须预期的编译时类型安全。例如，如果我们在示例中 context 中存储一个整数而不是字符串，那么尝试将其转换为字符串的类型断言将失败，我们的代码随后必须手动从从中恢复，而这通常是不可能的，因为我们不知道如何处理无效数据继续进行。

```go
newCtx := context.WithValue(ctx, "my-key", 123)
myKey := newCtx.Value("my-key")
if myKeyStr, ok := myKey.(string); !ok {
    // 我们这里有一个问题，因为 myKey 是 int，不是
    // string！我们现在必须在代码中尝试恢复
    // 而不是让编译器为我们捕获！
    // 在此处继续的方法通常是返回错误
}
```

幸运的是，有一种方法可以应对这个问题，这涉及到创建一个自己的 context 包，它封装了现有 context 包的一些函数并使用私有键。如果有代码配合，这会容易理解得多，因此从今起我们将编写自己的 context 包。我们将首先为该包创建目录和一个源文件。

```bash
$ mkdir context
$ atom context/context.go
```

我们将从导入和包声明开始。

```go
package context

import (
    "context"
    "lenslocked.com/models"
)
```

我们将同时导入 context 包和 models 包，因为我们要编写一个函数，接受现有的 context、一个用户，然后返回一个存储了该值的新 context。

```go
func WithUser(ctx context.Context, user *models.User) context.Context {
    return context.WithValue(ctx, "user", user)
}
```

只要开发者只调用 `WithUser` 函数为 "user" 键分配值，我们就永远不必担心无效数据。这意味着我们无法检索任何存储在这些键中的值，因此我们需要提供一个函数从给定的 context 中查找用户。

```go
func User(ctx context.Context) *models.User {
    if temp := ctx.Value(userKey); temp != nil {
        if user, ok := temp.(*models.User); ok {
            return user
        }
    }
    return nil
}
```

```go}
  return nil
}
```

现在我们的类型断言应该是始终正确的，但为了安全起见，我们仍然需要进行检查。我们应该验证上下文中之前是否存储了用户，这正是我们第一个“temp != nil”检查的作用。

如果出现其中任何一个问题，我们将返回 `nil`。否则，我们将使用类型断言返回存储在上下文中的用户。

在完成 `context` 包后，我们将把 `RequireUser` 中间件更新到该包中。在中间件内部，我们将从请求中获取上下文，创建一个存储了该用户的用户的新上下文，然后使用更新后的上下文创建一个新请求。

```bash
$ atom middleware/require_user.go
```

将我们的新包添加到导入项中。

```go
import (
  // 添加此行
  "lenslocked.com/context"
)
```

然后进入我们编写的 `ApplyFn` 函数。在该函数的末尾，我们将像之前在本节中看到的那样从请求中获取上下文。一旦获取了上下文，将其传递给我们编写的 `WithUser` 函数，以及我们想要设置的用户，然后将返回值赋给 `ctx` 变量。最后，我们使用现有的请求和我们的新上下文创建一个新请求。就像我们不修改修改对象而是派生一个新的对象一样，我们也需要使用现有请求和新上下文派生一个新的请求。然后，我们将新请求传递给下一个处理器。

## 14.6. 通过中间件要求用户

```go
func (mw *RequireUser) ApplyFn(next http.HandlerFunc) http.HandlerFunc {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
	// ... cookie 查找和用户验证保持不变
		// 从请求中获取上下文
		ctx := r.Context()
		// 从现有的上下文创建一个新上下文，
		// 并使用私有用户键存储了我们的用户
		ctx = context.WithContext(ctx, user)
		// 从现有的请求创建一个新请求，
		// 附加我们的上下文并将其赋值回 'r'
		r = r.WithContext(ctx)
		next(w, r)
	})
}
```

最后，我们需要更新 `galleries` 控制器中的 `Create` 方法，为我们正在创建的画廊获取适当的 `UserID`。

```bash
$ atom controllers/galleries.go
```

找到 `Create` 方法。我们将在解析表单之后更新它，并查找用户。我们将从上下检索用户，然后使用该用户的 ID 作为我们构建的 `Gallery` 模型的 `UserID` 字段。

```go
func (g *Galleries) Create(w http.ResponseWriter, r *http.Request) {
	// ... 使用现有代码解析表单
	// 这是我们的新代码
	user := context.User(r.Context())
	// 然后我们更新构建 Gallery 模型的方式
	gallery := models.Gallery{
		Title: form.Title,
		UserID: user.ID,
	}
	// 然后我们像以前一样创建画廊，使用
	// g.gs.Create(...) 方法调用。
}
```

## 第 14 章：创建画廊资源

我们现在能够使用我们的表单创建画廊了，并且每个画廊的创建都应该由当前登录的用户自动分配一个 `UserId`。你可以通过通过创建新账户（或登录现有账户）并使用每个账户创建一个画廊来测试这一点。然后检查你的日志以验证每个画廊都是使用适当的相应 ID 创建的。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

- 已完成 - [book.usegolang.com/14.6.2](https://book.usegolang.com/14.6.2)
- 更改 - [book.usegolang.com/14.6.2-diff](https://book.usegolang.com/14.6.2-diff)

## 14.7 显示画廊

我们将实现的下一个处理器是用于在画廊创建后渲染它的处理器。现在这可能很无聊，因为我们的画廊中还没有图像，但一旦我们实现了上传功能，稍后就可以进行更新。现在我们想要关注显示画廊的标题并在用户创建新画廊后重定向他们。

我们将从创建一个视图并将其添加到控制器开始。之后，我们将更新路由并查看如何使用 `gorilla/mux` 解析 URL 参数。一旦我们获取了要渲染的画廊 ID，我们需要编写一些代码从数据库中检索它，最后，我们将查看如何使用我们的路由器、命名路由和画廊 ID 为现有的画廊生成 URL。然后，我们将使用生成的 URL 在用户创建新画廊后重定向用户。

## 14.7 显示画廊

### 14.7.1 创建显示画廊视图

我们需要的第一个部分是用于渲染我们画廊的模板。现在我们对画廊可以访问的数据只有它的标题，所以这极地简化了我们的视图。

```bash
$ atom views/galleries/show.shtml
```

```html
{(define "yield")}
<div class="row">
  <div class="col-md-12">
    <h1>
      {{Title}}
    </h1>
    <p>Images coming...</p>
  </div>
</div>
{{end}}
```

此模板将渲染画廊的标题。我们需要向控制器添加一条消息。

```bash
$ atom controllers/galleries.go
```

```go
type Galleries struct {
	Title  string
	UserID int
}
```

在这种情况下，我们规定 id 只能是数字字符。

## 14.7. 显示画库

现在我们已经知道了要做什么，让我们从为我们的画库展示页定义路由开始。

```bash
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

```bash
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
```
