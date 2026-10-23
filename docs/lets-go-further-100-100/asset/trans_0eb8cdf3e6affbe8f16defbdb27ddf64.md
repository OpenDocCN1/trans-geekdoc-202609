
这个方法的好处在于返回的实体与模型的主要职责保持一致：`UserModel` 方法返回的是用户，而 `TokenModel` 方法返回的是令牌。

## 创建 activateUserHandler

现在我们已经对如何在数据库模型中查询用户 ↔ 令牌关系有了一个非常高层次的想法，让我们开始构建激活用户的代码。

为此，我们需要在 API 中添加一个新的 `PUT /v1/users/activated` 端点：

| 方法 | URL 模式 | 处理程序 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| GET | /v1/movies | listMoviesHandler | 显示所有电影的详细信息 |
| POST | /v1/movies | createMovieHandler | 创建一部新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PATCH | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |
| POST | /v1/users | registerUserHandler | 注册新用户 |
| PUT | /v1/users/activated | activateUserHandler | 激活特定用户 |

工作流程如下：

- 1. 用户提交明文激活令牌（他们刚刚通过电子邮件收到的）到 `PUT /v1/users/activated` 端点。
- 2. 我们验证明文令牌以检查其是否符合预期格式，如有必要则向客户端发送错误消息。
- 3. 然后我们调用 `UserModel.GetForToken()` 方法来检索与提供的令牌关联的用户的详细信息。如果找不到匹配的令牌或已过期，我们向客户端发送错误消息。
- 4. 我们通过将用户记录上的 `activated = true` 来激活关联的用户并在数据库中更新它。
- 5. 我们从 `tokens` 表中删除用户的所有激活令牌。我们可以使用之前创建的 `TokenModel.DeleteAllForUser()` 方法来完成此操作。
- 6. 我们在 JSON 响应中发送更新后的用户详细信息。

让我们在 `cmd/api/users.go` 文件中开始并创建新的 `activateUserHandler` 来逐步完成这些步骤：

```
File: cmd/api/users.go
```

```
args := []interface{}{tokenHash[:], tokenScope, time.Now()}

var user User

ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
defer cancel()

// Execute the query, scanning the return values into a User struct. If
// no matching
// record is found we return an ErrRecordNotFound error.
err := m.DB.QueryRowContext(ctx, query, args...).Scan(
    &user.ID,
    &user.CreatedAt,
    &user.Name,
    &user.Email,
    &user.Password.hash,
    &user.Activated,
    &user.Version,
)
if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

// Return the matching user.
return &user, nil
}
```

现在设置完成，接下来需要做的最后一件事是将 PUT /v1/users/activated 端点添加到 cmd/api/routes.go 文件中。如下所示：

File: cmd/api/routes.go

```go
package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies", app.listMoviesHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.updateMovieHandler)
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.deleteMovieHandler)

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    // Add the route for the PUT /v1/users/activated endpoint.
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    return app.recoverPanic(app.rateLimit(router))
}
```

顺便说一下，我应该快速解释一下我们为什么对该端点使用 PUT 而不是 POST，因为它具有幂等性。

如果客户端多次发送相同的 PUT /v1/users/activated 请求，第一次请求会成功（假设令牌有效），然后任何后续请求都会导致向客户端发送错误（因为令牌已被使用并从数据库中删除）。但重要的是，*在第一次请求之后，我们应用程序的状态（即数据库）不会发生变化。*

基本上，客户端多次发送相同请求不会产生应用程序状态的副作用，这意味着该端点是幂等的，使用 PUT 比 POST 更合适。

好吧，让我们重新启动 API 然后试试。

首先，尝试向 PUT /v1/users/activated 端点发送包含一些无效令牌的请求。你应该会得到相应的错误消息响应，如下所示：

```
$ curl -X PUT -d '{"token": "invalid"}' localhost:4000/v1/users/activated
{
  "error": {
    "token": "must be 26 bytes long"
  }
}

$ curl -X PUT -d '{"token": "ABCDEFGHIJKLMNOPQRSTUVWXYZ"}'
localhost:4000/v1/users/activated
{
  "error": {
    "token": "invalid or expired activation token"
  }
}
```

```
enter the following code:

--------------------
Y3QMGX3PJ3WLRL2YRTQGQ6KRHU
--------------------

Please note that this code will expire in 3 days and can only be used once.

Thanks,

The Greenlight Team
```

这种方法从根本上来说是简单且安全的——本质上你的网站只需提供一个表单来代表用户执行 PUT 请求，而不是让他们使用 curl 或其他工具手动执行。

注意：创建电子邮件中的链接时，不要依赖 r.Host 中的 Host 头来构造 URL，因为这会容易受到主机头注入攻击。URL 域名应硬编码或作为命令行标志在启动应用程序时传入。

另外，如果你不想让用户复制粘贴令牌，你可以让他们点击包含令牌的链接，该链接会带他们到你网站上的页面。类似于这样：

```
Hi,
```

```
Thanks for signing up for a Greenlight account. We're excited to have you on board!

For future reference, your user ID number is 123.

To activate your Greenlight account please click the following link:

h_t_t_p_s_:__/_e_x_a_m_p_l_e_._c_o_m/_u_s_e_r_s/_a_c_t_i_v_a_t_e?_t_o_k_e_n=_Y_3_Q_M_G_X_3_P_J_3_W_L_R_L_2_Y_R_T_Q_G_Q_6_K_R_H_U_

Please note that this link will expire in 3 days and can only be used once.

Thanks,

The Greenlight Team
```

此页面随后应显示一个按钮，上面写着类似“确认您的账户激活”的内容，并且网页上的一些 JavaScript 可以从 URL 中提取令牌，并在用户点击按钮时将其提交到你的 PUT /v1/users/activate API 端点。

如果你选择第二个选项，你还需要采取措施避免令牌在用户导航到不同站点时通过引用标头泄露。你可以使用 Referrer-Policy: Origin 头或 <meta name="referrer" content="origin"> HTML 标签来缓解此问题，尽管你应该意识到它并非被所有网络浏览器都支持（目前支持率约为 ~96%）。

不过，在所有情况下，无论电子邮件和工作流程在前端和用户体验方面看起来如何，我们已实现的后端 API 端点都是相同的且无需更改。

## SQL 查询时序攻击

值得指出的是，我们在 `UserModel.GetForToken()` 中使用的 SQL 查询理论上容易受到时序攻击，因为 PostgreSQL 对 `tokens.hash = $1` 条件的评估不是以恒定时间执行的。

```
SELECT users.id, users.created_at, users.name, users.email,
users.password_hash, users.activated, users.version
FROM users
INNER JOIN tokens
ON users.id = tokens.user_id
WHERE tokens.hash = $1      --<-- This is vulnerable to a timing attack
AND tokens.scope = $2
AND tokens.expiry > $3
```

虽然操作起来有点棘手，但理论上攻击者可以向我们的 `PUT /v1/users/activated` 端点发出数千个请求并分析平均响应时间中的微小差异，以构建数据库中哈希激活令牌值的图像。

但是，在我们的情况下，即使时序攻击成功，它也只会泄露数据库中的 *哈希* 令牌值——而不是明文
