
```go
package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.updateMovieHandler)
    // Add the route for the DELETE /v1/movies/:id endpoint.
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.deleteMovieHandler)

    return router
}
```

OK，让我们重新启动 API 并通过从电影数据库中删除 *Deadpool* 来试用此功能（如果你一直跟着操作的话，它应该具有 ID 为 3）。删除操作应该不会有任何问题，你应该会收到如下确认消息：

```bash
$ curl -X DELETE localhost:4000/v1/movies/3
{
    "message": "movie successfully deleted"
}
```

如果你重复相同的请求来删除已经被删除的电影，你现在应该会收到 404 Not Found 响应和错误消息。类似这样：

```
$ curl -X DELETE localhost:4000/v1/movies/3
{
  "error": "the requested resource could not be found"
}
```

## 高级 CRUD 操作

在本书的这一节中，我们将研究一些你可能希望为 API 提供的 CRUD 端点使用的更“高级”的模式。

You’ll learn:
- 如何支持对资源的 *partial* 更新（这样客户端只需发送想要更改的数据）。
- 如何使用 *optimistic concurrency control* 来避免两个客户端同时尝试更新同一资源时发生的竞态条件。
- 如何使用 *context timeouts* 来终止长时间运行的数据库查询并防止不必要的资源使用。

## 处理部分更新

在本章中，我们将更改 `updateMovieHandler` 的行为，使其支持电影记录的 *partial updates*。从概念上讲，这比进行 *complete replacement* 稍微复杂一些，这就是为什么我们首先用那种方法打下基础的原因。

例如，假设我们注意到数据库中 *The Breakfast Club* 的发行年份是错误的（实际上应该是 1985，而不是 1986）。如果我们能够发送一个只包含需要应用的更改的 JSON 请求，而不是所有电影数据，那就太好了，像这样：

```
{"year": 1985}
```

让我们快速看看如果现在尝试发送此请求会发生什么：

```
$ curl -X PUT -d '{"year": 1985}' localhost:4000/v1/movies/4
{
  "error": {
    "genres": "must be provided",
    "runtime": "must be provided",
    "title": "must be provided"
  }
}
```

正如我们在书中前面提到的，在解码请求体时，我们的 `input` 结构体中任何 *don’t* 具有对应 JSON 键/值对的字段都将保留其 `zero-value`。我们在验证期间恰好会检查这些零值并返回你上面看到的错误消息。

在部分更新的上下文中，这会导致一个问题。我们如何区分以下两种情况：
- 客户端 *providing a key/value pair which has a zero-value value* ——像 `{"title": ""}` ——在这种情况下，我们希望返回验证错误。
- 客户端在 JSON 中 *not providing a key/value pair* ——在这种情况下，我们希望‘skip’更新该字段但不发送验证错误。

为了帮助回答这个问题，让我们快速回顾一下不同 Go 类型的零值是什么。

| Go 类型 | 零值 |
|---|---|
| `int*`, `uint*`, `float*`, `complex` | `0` |
| `string` | `""` |
| `bool` | `false` |
| `func`, `array`, `slice`, `map`, `chan` 和 `pointers` | `nil` |

这里需要注意的关键点是，指针的零值为 nil。

所以——从理论上讲——我们可以将输入结构体中的字段更改为指针。然后，要查看客户端是否在 JSON 中提供了特定的键/值对，我们只需简单检查输入结构体中对应字段是否等于 nil 即可。

```
// Use pointers for the Title, Year and Runtime fields.
var input struct {
    Title   *string        `json:"title"`   // This will be nil if there is no corresponding key in the JSON.
    Year    *int32         `json:"year"`    // Likewise...
    Runtime *data.Runtime  `json:"runtime"` // Likewise...
    Genres  []string       `json:"genres"`  // We don't need to change this because slices already have the zero-value nil.
}
```

### 执行部分更新

让我们付诸实践，并按如下方式编辑我们的 updateMovieHandler 方法以支持部分更新：

```
File: cmd/api/movies.go
```

```go
package main

...

func (app *application) updateMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        app.notFoundResponse(w, r)
        return
    }

    // Retrieve the movie record as normal.
    movie, err := app.models.Movies.Get(id)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrRecordNotFound):
            app.notFoundResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // Use pointers for the Title, Year and Runtime fields.
    var input struct {
        Title    *string        `json:"title"`
        Year     *int32         `json:"year"`
        Runtime  *data.Runtime  `json:"runtime"`
        Genres   []string       `json:"genres"`
    }

    // Decode the JSON as normal.
    err = app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }
}
```

```go
}

err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

总结一下：我们已更改 `input` 结构体，使其所有字段现在都具有零值 `nil`。在解析 JSON 请求后，我们然后遍历 `input` 结构体字段，只有当新值 *not* 为 `nil` 时才更新电影记录。

除此之外，对于执行资源 *partial updates* 的 API 端点，使用 HTTP 方法 `PATCH` 而不是 `PUT`（`PUT` 用于完全替换资源）是合适的。

因此，在尝试新代码之前，让我们快速更新 `cmd/api/routes.go` 文件，使我们的 `updateMovieHandler` 仅用于 `PATCH` 请求。

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)
}
}
```

再一次，看起来不错。我们可以看到 `year` 值已正确更新，并且 `version` 数字已递增，但其他数据字段均未更改。

让我们也快速尝试相同的请求，但包含一个空的 `title` 值。在这种情况下，更新将被阻止，你应该会收到验证错误，如下所示：

```
$ curl -X PATCH -d '{"year": 1985, "title": ""}' localhost:4000/v1/movies/4
{
  "error": {
    "title": "must be provided"
  }
}
```

## 附加信息

## JSON 中的 Null 值

需要注意的一个特殊情况是，当客户端明确 *supplies a field in the JSON request with the value* `null` 时。在这种情况下，我们的处理程序将忽略该字段并将其视为未提供。

例如，以下请求将导致电影记录没有任何更改（除版本号递增之外）：

```
$ curl -X PATCH -d '{"title": null, "year": null}' localhost:4000/v1/movies/4
{
    "movie": {
        "id": 4,
        "title": "The Breakfast Club",
        "year": 1985,
        "runtime": "96 mins",
        "genres": [
            "drama"
        ],
        "version": 3
    }
}
```

在理想世界中，此类请求应返回某种验证错误。但——除非你编写自己的自定义 JSON 解析器——否则无法区分客户端在 JSON 中未提供键/值对，还是提供了值为 null 的情况。

在大多数情况下，probably 足够在端点的客户端文档中解释这种特殊情况的行为，并说明类似“JSON items with null values will be ignored and will remain unchanged”之类的话。

