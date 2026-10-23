
```
app.requireActivatedUser(app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.requireActivatedUser(app.updateMovieHandler))
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requireActivatedUser(app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

    return app.recoverPanic(app.rateLimit(app.authenticate(router)))
}
```

## 演示

好吧，让我们试试这些更改！

我们将开始以匿名用户身份调用 GET /v1/movies/:id 端点。执行此操作时，你现在应该会收到 401 Unauthorized 响应，如下所示：

```
$ curl -i localhost:4000/v1/movies/1
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 15:59:33 GMT
Content-Length: 66

{
"error": "you must be authenticated to access this resource"
}
```

接下来，让我们尝试以拥有账户但尚未激活的用户身份发出请求。如果你一直跟着做，你应该能够使用 `alice@example.com` 用户来执行此操作，如下所示：

```
$ BODY='{"email": "alice@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
    "authentication_token": {
        "token": "204YHHWDHVWWDNKN2UZR722BU",
        "expiry": "2021-04-17T18:03:09.598843181+02:00"
    }
}

$ curl -i -H "Authorization: Bearer 204YHHWDHVWWDNKN2UZR722BU"
localhost:4000/v1/movies/1
HTTP/1.1 403 Forbidden
Content-Type: application/json
Vary: Authorization
Date: Fri, 16 Apr 2021 16:03:45 GMT
Content-Length: 76

{
    "error": "your user account must be activated to access this resource"
}
```

太好了，我们可以看到这现在会从我们新的 `inactiveAccountResponse()` 辅助函数返回 `403 Forbidden` 响应。

最后，让我们尝试以已激活用户身份发出请求。

如果你正在跟随编码，你可能想快速连接到你的 PostgreSQL 数据库并 double-check 哪些用户已经激活。

```
$ psql $GREENLIGHT_DB_DSN
psql (13.2 (Ubuntu 13.2-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT email FROM users WHERE activated = true;
        email
--------------------
 faith@example.com
(1 row)
```

在我的例子中，唯一已激活的用户是 faith@example.com，所以让我们以他们的身份尝试发出请求。当以已激活用户身份发出请求时，我们 requireActivatedUser() 中间件中的所有检查都会通过，你应该会得到成功的响应。类似于这样：

```
$ BODY='{"email": "faith@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
  "authentication_token": {
    "token": "ZFIKQ344EYM5KEP6JL2RHL RPJQ",
    "expiry": "2021-04-17T18:04:57.513348573+02:00"
  }
}

$ curl -H "Authorization: Bearer ZFIKQ344EYM5KEP6JL2RHL RPJQ"
localhost:4000/v1/movies/1
{
  "movie": {
    "id": 1,
    "title": "Moana",
    "year": 2016,
    "runtime": "107 mins",
    "genres": [
      "animation",
      "adventure"
    ],
    "version": 1
  }
}
```

## 分割中间件

目前我们有一个中间件执行两项检查：首先检查用户是否已通过身份验证（不是匿名），其次检查他们是否已激活。

但可以想象一种场景，你只想检查用户是否已通过身份验证，而不关心他们是否已激活。为此，你可能希望引入额外的 requireAuthenticatedUser() 中间件以及当前的 requireActivatedUser() 中间件。

然而，这两个中间件之间会存在一些重叠，因为它们都会检查用户是否已通过身份验证。避免这种重复的一种巧妙方法是

如果你只有几个端点需要执行授权检查，那么与其使用中间件，通常在相关处理器内部执行检查会更容易。例如：

```
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    user := app.contextGetUser(r)

    if user.IsAnonymous() {
        app.authenticationRequiredResponse(w, r)
        return
    }

    if !user.Activated {
        app.inactiveAccountResponse(w, r)
        return
    }

    // The rest of the handler logic goes here...
}
```

| 方法 | URL 模式 | 所需权限 |
|---|---|---|
| GET | /v1/movies/:id | movies:read |
| PATCH | /v1/movies/:id | movies:write |
| DELETE | /v1/movies/:id | movies:write |
| POST | /v1/users | - |
| PUT | /v1/users/activated | - |
| POST | /v1/tokens/authentication | - |

## 权限与用户之间的关系

权限与用户之间的关系是 *多对多* 关系的绝佳示例。一个用户可能拥有 *许多权限*，同一个权限也可能属于 *许多用户*。

在像 PostgreSQL 这样的关系数据库中管理多对多关系的经典方法是创建两个实体之间的 *连接表*。我会快速解释其工作原理。

假设我们将用户数据存储在 `users` 表中，其结构如下：

| id | email | ... |
|---|---|---|

| id | email | ... |
|---|---|---|
| 1 | alice@example.com | ... |
| 2 | bob@example.com | ... |

我们的权限数据存储在 `permissions` 表中，如下所示：

| id | code |
|---|---|
| 1 | movies:read |
| 2 | movies:write |

然后我们可以创建一个名为 `users_permissions` 的连接表来存储有关 *哪些用户拥有哪些权限* 的信息，如下所示：

| user_id | permission_id |
|---|---|
| 1 | 1 |
| 2 | 1 |
| 2 | 2 |

在上面的示例中，用户 `alice@example.com`（用户 ID `1`）仅拥有 `movies:read`（权限 ID `1`）权限，而 `bob@example.com`（用户 ID `2`）同时拥有 `movies:read` 和 `movies:write` 权限。

就像我们在书中前面看到的一对多关系一样，你可能希望在数据库模型中从两侧查询这种关系。例如，在你的数据库模型中，你可能希望创建以下方法：

```
PermissionModel.GetAllForUser(user)      → Retrieve all permissions for a user
UserModel.GetAllForPermission(permission) → Retrieve all users with a specific permission
```

## 创建 SQL 迁移

让我们将此付诸实践，并创建一个 SQL 迁移，在我们的数据库中创建新的 `permissions` 和 `users_permissions` 表，遵循我们刚才描述的模式。

继续运行以下命令来创建迁移文件：

```
$ migrate create -seq -ext .sql -dir ./migrations add_permissions
/home/alex/Projects/greenlight/migrations/000006_add_permissions.up.sql
/home/alex/Projects/greenlight/migrations/000006_add_permissions.down.sql
```

然后将以下 SQL 语句添加到‘up’迁移文件中：

```
File: migrations/000006_add_permissions.up.sql
```

```
CREATE TABLE IF NOT EXISTS permissions (
    id bigserial PRIMARY KEY,
    code text NOT NULL
);

CREATE TABLE IF NOT EXISTS users_permissions (
    user_id bigint NOT NULL REFERENCES users ON DELETE CASCADE,
    permission_id bigint NOT NULL REFERENCES permissions ON DELETE CASCADE,
    PRIMARY KEY (user_id, permission_id)
);

-- Add the two permissions to the table.
INSERT INTO permissions (code)
VALUES
    ('movies:read'),
    ('movies:write');
```

这里有几件重要的事情需要指出：

- PRIMARY KEY (user_id, permission_id) 行在我们的 users_permissions 表上设置了一个复合主键，其中主键由 users_id 和 permission_id 两列组成。将此设置为主键本质上意味着相同的用户/权限组合在表中只能出现一次且不能重复。
- 在创建 users_permissions 表时，我们使用 REFERENCES user 语法来针对 users 表的主键创建外键约束，这确保 user_id 列中的任何值在 users 表中都有对应的条目。同样，我们使用 REFERENCES permissions 语法
