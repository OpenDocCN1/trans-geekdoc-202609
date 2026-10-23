
*姓名、电子邮件或密码。*

我们还在 `User` 结构体上实现了 `IsAnonymous()` 方法，因此每当我们有一个 `User` 实例时，就可以轻松检查它是否是 `AnonymousUser` 实例。 例如：

```go
data.AnonymousUser.IsAnonymous() // → Returns true

otherUser := &data.User{}
otherUser.IsAnonymous()           // → Returns false
```

## 读取和写入请求上下文

在创建 `authenticate()` 中间件本身之前，另一个设置步骤与 *在请求上下文中存储用户详细信息* 有关。

我们在 *Let’s Go* 中详细讨论了请求上下文是什么以及如何使用它，如果其中任何内容让你感到不熟悉，我建议在继续之前重新阅读书中的该部分。 但作为快速提醒：

- 我们的应用程序处理的每个 `http.Request` 都嵌入了 `context.Context`，我们可以在请求的生命周期内使用它来存储包含任意数据的键/值对。 在这种情况下，我们希望存储包含当前用户信息的 `User` 结构体。
- 存储在请求上下文中的任何值都具有 `interface{}` 类型。 这意味着在从请求上下文检索值后，在使用它之前需要将其断言回原始类型。
- 使用自己的自定义类型作为请求上下文键是良好的实践。 这有助于防止你的代码与也使用请求上下文存储信息的任何第三方包之间的命名冲突。

为此，让我们创建一个新的 `cmd/api/context.go` 文件，其中包含一些用于从请求上下文读取/写入 `User` 结构体的辅助方法。

如果你跟着操作，请继续创建新文件：

```bash
$ touch cmd/api/context.go
```

然后添加以下代码：

```go
File: cmd/api/context.go

package main

import (
    "context"
    "net/http"

    "greenlight.alexedwards.net/internal/data"
)
```

```go
type contextKey string

// Convert the string "user" to a contextKey type and assign it to the
userContextKey
// constant. We'll use this constant as the key for getting and setting user
information
// in the request context.
const userContextKey = contextKey("user")

// The contextSetUser() method returns a new copy of the request with the
provided
// User struct added to the context. Note that we use our userContextKey
constant as the
// key.
func (app *application) contextSetUser(r *http.Request, user *data.User) *http.Request {
    ctx := context.WithValue(r.Context(), userContextKey, user)
    return r.WithContext(ctx)
}

// The contextGetUser() retrieves the User struct from the request context.
The only
// time that we'll use this helper is when we logically expect there to be
User struct
// value in the context, and if it doesn't exist it will firmly be an
'unexpected' error.
// As we discussed earlier in the book, it's OK to panic in those
circumstances.
func (app *application) contextGetUser(r *http.Request) *data.User {
    user, ok := r.Context().Value(userContextKey).(*data.User)
    if !ok {
        panic("missing user value in request context")
    }

    return user
}
```

```go
http.ResponseWriter, r *http.Request) {
    w.Header().Set("WWW-Authenticate", "Bearer")

    message := "invalid or missing authentication token"
    app.errorResponse(w, r, http.StatusUnauthorized, message)
}
```

> **注意：** 我们在这里包含 `WWW-Authenticate: Bearer` 头是为了帮助通知或提醒客户端，我们期望他们使用 bearer token 进行身份验证。

最后，我们需要在处理器链中添加 `authenticate()` 中间件。 我们希望在 *所有* 请求上使用此中间件 —— 在我们的 panic 恢复和速率限制中间件之后，但在路由器之前。

请相应地更新 `cmd/api/routes.go` 文件：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)
}
```

**提示：** 如果你在此处收到错误响应，请确保在第二次请求中使用来自第一次请求的正确身份验证令牌。

相比之下，你也可以尝试发送一些带有无效身份验证令牌或格式错误的 Authorization 头的请求。 在这些情况下，你应该会收到 401 Unauthorized 响应，如下所示：

```
$ curl -i -H "Authorization: Bearer XXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
localhost:4000/v1/healthcheck
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 10:23:06 GMT
Content-Length: 56

{
  "error": "invalid or missing authentication token"
}

$ curl -i -H "Authorization: INVALID" localhost:4000/v1/healthcheck
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 10:23:26 GMT
Content-Length: 56

{
  "error": "invalid or missing authentication token"
}
```

## 需要用户激活

正如我们刚才提到的，就授权而言，我们要做的第一件事是限制对我们的 `/v1/movies**` 端点的访问 —— 这样只有经过身份验证（非匿名）的用户并且已激活其账户的用户才能访问。

执行这类检查是某些中间件的理想任务，因此让我们开始创建一个新的 `requireActivatedUser()` 中间件方法来处理此事。 在此中间件中，我们希望从请求上下文中提取 `User` 结构体，然后检查 `IsAnonymous()` 方法和 `Activated` 字段以确定请求是否应继续。

具体来说：

- 如果用户是匿名的，我们应发送 `401 Unauthorized` 响应并显示错误消息说 “`you must be authenticated to access this resource`”。
- 如果用户不是匿名的（即他们已成功通过身份验证，我们知道他们是谁），但他们未 *激活*，我们应发送 `403 Forbidden` 响应并显示错误消息说 “`your user account must be activated to access this resource`”。

文件: cmd/api/middleware.go

```go
package main

...

func (app *application) requireActivatedUser(next http.HandlerFunc) http.HandlerFunc {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Use the contextGetUser() helper that we made earlier to retrieve the user
        // information from the request context.
        user := app.contextGetUser(r)

        // If the user is anonymous, then call the authenticationRequiredResponse() to
        // inform the client that they should authenticate before trying again.
        if user.IsAnonymous() {
            app.authenticationRequiredResponse(w, r)
            return
        }

        // If the user is not activated, use the inactiveAccountResponse() helper to
        // inform them that they need to activate their account.
        if !user.Activated {
            app.inactiveAccountResponse(w, r)
            return
        }

        // Call the next handler in the chain.
        next.ServeHTTP(w, r)
    })
}
```

这里请注意，我们的 `requireActivatedUser()` 中间件与其他我们在本书中构建的中间件的签名略有不同。 而不是接受和返回 `http.Handler`，它接受和返回 `http.HandlerFunc`。

这是一个小的改动，但它使得可以直接用此中间件包装我们的 `/v1/movie**` 处理器函数，而无需进行任何进一步的转换。

请按如下方式更新 `cmd/api/routes.go` 文件以执行此操作：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)

    // Use the requireActivatedUser() middleware on our five /v1/movies**
endpoints.
    router.HandlerFunc(http.MethodGet, "/v1/movies",
app.requireActivatedUser(app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies",
app.requireActivatedUser(app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
