

```go
$ atom views/users/new.gohtml
```

密码字段和邮箱地址字段将保持不变。我们只需要为名称字段添加一个类型为 text 的新字段。

```go
{{define signupForm}}
<form action="/signup" method="POST">
  <div class="form-group">
    <label for="name">Name</label>
    <input type="text" name="name" class="form-control" id="name" placeholder="Your full name">
  </div>
  <!-- ... 其他部分保持不变 -->
</form>
{{end}}
```

完成后，你应该启动（或重启）服务器，以验证表单已更新并正确包含了该字段。这如图 9.1 所示。

```go
$ go run main.go
```

## 9.7 连接用户服务与控制器

![](img/d6be51afcf11b16bf97245d05fb9e635_258_0.png)

图 9.1: 带有名称字段的注册表单

接下来，我们需要更新用户控制器的 `SignupForm` 字段，让它感知新的名称字段。

```go
$ atom controllers/users.go
```

得益于我们正在使用的 `schema` 包，代码更改仅需新增一行。

## 第 9 章：创建用户模型

```go
type Signup struct {
  Name     string `schema:"name"`
  Email    string `schema:"email"`
  Password string `schema:"password"`
}
```

你也可以更新用户控制器中的 `Create` 处理器，以打印名称，以确保它被正确解析。

```go
fmt.Fprintln(w, "Name is", form.Name)
```

在继续之前，请重启服务器并验证一切运行正常。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/9.7.1
- 差异 - book.usegolang.com/9.7.1-diff

## 9.7.2 在我们的 Web 应用中设置用户服务

我们的下一步是在应用程序启动时设置用户服务，这样我们就可以为 Web 应用中任何需要该服务的部分提供支持。

虽然将此逻辑推送到需要用户服务的组件中可能很有吸引力，但这样做会产生一些副作用。首先，几处代码将需要知道如何构建 Postgres 连接字符串，必须编写自定义逻辑在完成后关闭用户服务，而且我们会有多个到数据库的连接而没有任何实际收益。

相反，我们将创建一个用户服务的单例，推迟关闭操作直到整个应用程序关机，并将该用户服务与我们的用户控制器以及任何需要访问权限的其它代码部分共享。

我们现在将在 Web 应用的 `main` 包中工作，因此打开源文件。

```go
$ atom main.go
```

我们尚未向此源文件添加任何与数据库相关的变量，因此我们将从实验性的 `main.go` 源文件中拷贝已有的常量。以后我们将探索如何将这些内容移动到配置文件，但目前这样运行足够了。这如列表 9.5 所示，但你可能需要微调某些值。

列表 9.5：将你的数据库信息添加到 main.go
```go
const (
host = "localhost"
port = 5432
user = "postgres"
password = "your-password"
dbname = "lenslocked_dev"
)
```

> **框 9.6。不要在代码中硬编码密码发布到生产环境**
> 到此为止，我们将密码以及连接 Postgres 需要的其他信息作为常量存储在应用程序中，虽然对于开发应用程序没有问题，但你不应该以这种方式存储密码发布到生产服务器或提交到 git。

## 第 9 章：创建用户模型

最终我们将把这些常量从代码中提取出来，并在启动应用程序时通过标志（flags）提供它们，但在此期间，请意识到这不是一种很好的方法，我们这样做是为了在开始讨论如何准备生产环境之前稍微简化我们的代码。

接下来，我们需要创建连接字符串。同样，你可以从之前的实验性代码中拷贝它。这将放在 `main` 函数内部。

```go
func main() {
//// 准备一个 DB 连接字符串，然后使用它来
// 创建我们的模型服务。
psqlInfo := fmt.Sprintf("host=%s port=%d user=%s " + 
"password=%s dbname=%s sslmode=disable",
host, port, user, password, dbname)
// ... 控制器和路由代码保持不变
}
```

之后，我们需要使用此连接字符串创建一个用户服务。在创建用户服务时，我们还想要检查错误，推迟关闭直到 `main` 函数退出，并调用我们之前编写的 `AutoMigrate` 函数，以确保数据库已正确迁移。

```go
import (
"fmt"
"net/http"

"lenslocked.com/controllers"
"lenslocked.com/models"

"github.com/gorilla/mux"
)
// ...

func main() {
// ... 首先是 psqlInfo 代码
```

## 9.7 连接用户服务与控制器

```go
us, err := models.NewUserService(psqlInfo)
if err != nil {
    panic(err)
    deferdefer us.Close()
    us.AutoMigrate()
}
// ... 控制器和路由代码保持不变
}
```

我们暂时不会使用这个用户服务的设置，但请先确保你的代码可以编译并运行。在下一节中，我们将查看如何在用户控制器内部使用。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/9.7.2
- 差异 - book.usegolang.com/9.7.2-diff

## 9.7.3 在用户控制器中使用用户服务

我们将更新用户控制器，使其在构造时接受一个 `UserService` 实例，然后我们将在 `Create` 方法内部使用该用户服务，以实际创建一个由数据库支持的用户。

让我们从打开用户控制器源代码开始。

```go
$ atom controllers/users.go
```

## 第 9 章：创建用户模型

接下来我们将在 `Users` 类型中添加 `UserService`，以便我们的处理器方法在需要时访问用户服务。我们还需要在导入中添加 `models` 包。

```go
import (
    "fmt"
    "net/http"

    "lenslocked.com/models"
    "lenslocked.com/views"
)

// ...

type Users struct {
    NewView *views.View
    us *models.UserService
}
```

我们的 `NewUsers` 函数目前没有给该字段赋值，让我们下一步修复它。与其构造服务，不如将其作为参数传递给函数。

```go
func NewUsers(us *models.UserService) *Users {
    return &Users{
        NewView: views.View("bootstrap", "new"),
        us: us,
    }
}
```

接下来我们需要更新 `main.go` 源代码。现在它在调用 `NewUsers` 时没有传递任何参数，但我们刚刚更新了函数使其要求一个用户服务。

```go
$ atom main.go
```

## 9.7 连接用户服务与控制器

```go
func main() {
// ... 大部分内容不变

// 找到这一行，并更新它
usersC := controllers.NewUsers(us)
// ...
}
```

我们现在可以继续更新用户控制器。具体来说，我们将在 `Create` 处理器中使用用户服务来实际在数据库中存储用户。

- $ atom controllers/users.go

接下来我们更新代码，使用注册表单创建一个 `models.User`。我们暂时不会使用密码输入，因为我们还没有合适的存储密码的方法，但将在接几个章节中修复。在此期间，我们将只存储用户的名称和邮箱，以验证一切都按预期工作。

```go
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
var form SignUp
if err := parseForm(r, &form); err != nil {
	panic(err)
}
user := models.User{
	Name: form.Name,
	Email: form.Email,
}
if err := u.Create(&user); err != nil {
	http.Error(w, err.Error(), http.StatusInternalServerError)
	return
}
fmt.Fprintln(w, "User is ", user)
}
```

如果我们在创建用户时遇到错误，我们还将返回一个状态码，表示我们的服务器出现了问题。通常我不会

