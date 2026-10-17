
```go
wantUser: nil,

wantError: models.ErrNoError,

},

{

name: "Non-existent ID",

userID: 2,

wantUser: nil,

wantError: models.ErrNoRows,

},

}

for _, tt := range tests {

t.Run(tt.name, func(t *testing.T) {

// 初始化连接池并清理

db, teardown := newDB(t)

defer teardown()

m := &UserModel{DB: db}

user, err := m.Get(tt.userID)

if err != tt.wantError {

t.Errorf("UserModel.Get() error = %v, want %v", err, tt.wantError)

}

if !reflect.DeepEqual(user, tt.wantUser) {

t.Errorf("UserModel.Get() user = %v, want %v", user, tt.wantUser)

}

})

}

}
```

```
PASS: TestSignupUser/Dopticate_ematt (0.00s)
PASS: TestSignupUser/Invalid_CSRF_Token (0.00s)

=== RUN TestSecureHeaders
-- PASS: TestSecureHeaders (0.00s)

=== RUN TestHumanDate
=== RUN TestHumanDate/UTC
=== RUN TestHumanDate/Empty
=== RUN TestHumanDate/CET
-- PASS: TestHumanDate (0.00s)
-- PASS: TestHumanDate/UTC (0.00s)
-- PASS: TestHumanDate/Empty (0.00s)
-- PASS: TestHumanDate/CET (0.00s)

PASS
ok alexewards.net/snippetbox/cmd/web 0.053s

? alexewards.net/snippetbox/pkg/forms [no test files]
? alexewards.net/snippetbox/pkg/models [no test files]
? alexewards.net/snippetbox/pkg/models/mock [no test files]

=== RUN TestUserModelGet
-- SKIP: TestUserModelGet (0.00s)
users_test.go:15: mysql: skipping integration

PASS
ok alexewards.net/snippetbox/pkg/models/mysql 0.003s
```

否则，如果你没有使用 `-short` 标志，则测试将正常执行。

## 测试覆盖率概分析

`go test` 工具的一个非常强大的特性是它为测试覆盖率提供的指标和可视化。

请尝试使用 `-cover` 标志运行我们项目中的测试，如下所示：

```
$ go test -cover /...
alexwards.net/snippetbox/cmd/web (cached) coverage: 48.3% of st
? alexewards.net/snippetbox/pkg/forms [no test files]
? alexewards.net/snippetbox/pkg/models [no test files]
alexwards.net/snippetbox/pkg/models/mock [no test files]
ok alexwards.net/snippetbox/pkg/models/mysql (cached) coverage: 10
```

从结果中我们可以看到，`cmd/web` 包中 48.3% 的语句在测试期间被执行了，而对于 `pkg/models/mysql`，这个数字是 10.9。

我们可以通过使用 `-coverprofile` 标志来按方法和函数获取更详细的测试覆盖率细分，如下所示：

```
$ go test -coverprofile=/tmp/profile.out /../
```

这将正常执行你的测试，并且——如果所有测试都通过——则会将覆盖率分析文件写入特定位置（在我们的案例中为 `/tmp/profile.out`）。

然后你可以使用 `go tool` 命令查看覆盖率分析文件，如下所示：

```
$ go tool cover -func=/tmp/profile.out
alexwards.net/snippetbox/cmd/web/handlers.go:12:
alexwards.net/snippetbox/cmd/web/handlers.go:24:
alexwards.net/snippetbox/cmd/web/handlers.go:45:
alexwards.net/snippetbox/cmd/web/handlers.go:51:
alexwards.net/snippetbox/cmd/web/handlers.go:79:
alexwards.net/snippetbox/cmd/web/handlers.go:85:
alexwards.net/snippetbox/cmd/web/handlers.go:117:
alexwards.net/snippetbox/cmd/web/handlers.go:123:
alexwards.net/snippetbox/cmd/web/handlers.go:146:
alexwards.net/snippetbox/cmd/web/handlers.go:152:
alexwards.net/snippetbox/cmd/web/helpers.go:15:
alexwards.net/snippetbox/cmd/web/helpers.go:22:
alexwards.net/snippetbox/cmd/web/helpers.go:26:
alexwards.net/snippetbox/cmd/web/helpers.go:30:
alexwards.net/snippetbox/cmd/web/helpers.go:42:
alexwards.net/snippetbox/cmd/web/helpers.go:60:
alexwards.net/snippetbox/cmd/web/main.go:41:
alexwards.net/snippetbox/cmd/web/main.go:94:
alexwards.net/snippetbox/cmd/web/middleware.go:13:
alexwards.net/snippetbox/cmd/web/middleware.go:22:
alexwards.net/snippetbox/cmd/web/middleware.go:30:
alexwards.net/snippetbox/cmd/web/middleware.go:43:
alexwards.net/snippetbox/cmd/web/middleware.go:54:
alexwards.net/snippetbox/cmd/web/middleware.go:65:
alexwards.net/snippetbox/cmd/web/routes.go:10:
alexwards.net/snippetbox/cmd/web/templates.go:22:
alexwards.net/snippetbox/cmd/web/templates.go:34:
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:13:
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:30:
```

```
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:47: Latest
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:17: Get
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:58: Authenticate
```

这将打开一个包含内容的浏览器：

```go
package main

import (
    "alexwards.net/snippetbox/pkg/forms"
    "alexwards.net/snippetbox/pkg/models"
)

func ( * *))
```

```
alexwards.net/snippetbox/cmd/web/handlers.go:1:
alexwards.net/snippetbox/cmd/web/handlers.go:2:
alexwards.net/snippetbox/cmd/web/handlers.go:20:
alexwards.net/snippetbox/cmd/web/handlers.go:4:
alexwards.net/snippetbox/cmd/web/handlers.go:..
alexwards.net/snippetbox/cmd/web/handlers.go:2:
alexwards.net/snippetbox/cmd/web/handlers.go:12:
alexwards.net/snippetbox/cmd/web/handlers.go:24:
alexwards.net/snippetbox/cmd/web/handlers.go:45:
alexwards.net/snippetbox/cmd/web/handlers.go:51:
alexwards.net/snippetbox/cmd/web/handlers.go:79:
alexwards.net/snippetbox/cmd/web/handlers.go:85:
alexwards.net/snippetbox/cmd/web/handlers.go:17:
alexwards.net/snippetbox/cmd/web/handlers.go:123:
alexwards.net/snippetbox/cmd/web/handlers.go:146:
alexwards.net/snippetbox/cmd/web/handlers.go:152:
alexwards.net/snippetbox/cmd/web/helpers.go:15:
alexwards.net/snippetbox/cmd/web/helpers.go:22:
alexwards.net/snippetbox/cmd/web/helpers.go:26:
alexwards.net/snippetbox/cmd/web/helpers.go:30:
alexwards.net/snippetbox/cmd/web/helpers.go:42:
alexwards.net/snippetbox/cmd/web/helpers.go:60:
alexwards.net/snippetbox/cmd/web/main.go:41:
alexwards.net/snippetbox/cmd/web/main.go:94:
alexwards.net/snippetbox/cmd/web/middleware.go:13:
alexwards.net/snippetbox/cmd/web/middleware.go:22:
alexwards.net/snippetbox/cmd/web/middleware.go:30:
alexwards.net/snippetbox/cmd/web/middleware.go:43:
alexwards.net/snippetbox/cmd/web/middleware.go:54:
alexwards.net/snippetbox/cmd/web/middleware.go:65:
alexwards.net/snippetbox/cmd/web/routes.go:10:
alexwards.net/snippetbox/cmd/web/templates.go:22:
alexwards.net/snippetbox/cmd/web/templates.go:34:
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:13:
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:30:
```

这将打开一个包含内容的浏览器：

```go
package main

import (
    "alexwards.net/snippetbox/pkg/forms"
    "alexwards.net/snippetbox/pkg/models"
)

func ( * *))
```

```
alexwards.net/snippetbox/cmd/web/handlers.go:1
:
..net/snippetsnippet/cmd/web/handlers..::
:
alexwards.net/snippetbox/cmd/web/handlers.go:12:
alexwards.net/snippetbox/cmd/web/handlers.go:24:
alexwards.net/snippetbox/cmd/web/handlers.go:45:
alexwards.net/snippetbox/cmd/web/handlers.go:51:
alexwards.net/snippetbox/cmd/web/handlers.go:79:
alexwards.net/snippetbox/cmd/web/handlers.go:85:
alexwards.net/snippetbox/cmd/web/handlers.go:117:
alexwards.net/snippetbox/cmd/web/handlers.go:123:
alexwards.net/snippetbox/cmd/web/handlers.go:146:
alexwards.net/snippetbox/cmd/web/handlers.go:152:
alexwards.net/snippetbox/cmd/web/helpers.go:15:
alexwards.net/snippetbox/cmd/web/helpers.go:22:
alexwards.net/snippetbox/cmd/web/helpers.go:26:
alexwards.net/snippetbox/cmd/web/helpers.go:30:
alexwards.net/snippetbox/cmd/web/helpers.go:42:
alexwards.net/snippetbox/cmd/web/helpers.go:60:
alexwards.net/snippetbox/cmd/web/main.go:41:
alexwards.net/snippetbox/cmd/web/main.go:94:
alexwards.net/snippetbox/cmd/web/middleware.go:13:
alexwards.net/snippetbox/cmd/web/middleware.go:22:
alexwards.net/snippetbox/cmd/web/middleware.go:30:
alexwards.net/snippetbox/cmd/web/middleware.go:43:
alexwards.net/snippetbox/cmd/web/middleware.go:54:
alexwards.net/snippetbox/cmd/web/middleware.go:65:
alexwards.net/snippetbox/cmd/web/routes.go:10:
alexwards.net/snippetbox/cmd/web/templates.go:22:
alexwards.net/snippetbox/cmd/web/templates.go:34:
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:13:
alexwards.net/snippetbox/pkg/models/mysql/snippets.go:30:
```

这将打开一个包含内容的浏览器：

```go
package main

import (
    "alexwards.net/snippetbox/pkg/forms"
    "alexwards.net/snippetbox/pkg/models"
)

func ( * *))
```
