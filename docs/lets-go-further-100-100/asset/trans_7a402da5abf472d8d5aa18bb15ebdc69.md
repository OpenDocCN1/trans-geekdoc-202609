

返回这个新的、递增后的 `version` 值。

和之前一样，这个查询返回单行数据，因此我们也需要使用 Go 的 `QueryRow()` 方法来执行它。如果你在跟着做，请回到你的 `internal/data/movies.go` 文件，并按如下方式填写 `Update()` 方法：

```
File: internal/data/movies.go

package data

...

func (m MovieModel) Update(movie *Movie) error {
    // Declare the SQL query for updating the record and returning the new version
    // number.
    query := `
        UPDATE movies
        SET title = $1, year = $2, runtime = $3, genres = $4, version =
        version + 1
        WHERE id = $5
        RETURNING version`

    // Create an args slice containing the values for the placeholder parameters.
    args := []interface{}{
        movie.Title,
        movie.Year,
        movie.Runtime,
        pq.Array(movie.Genres),
        movie.ID,
    }

    // Use the QueryRow() method to execute the query, passing in the args
    // slice as a variadic parameter and scanning the new version value into the movie
    // struct.
    return m.DB.QueryRow(query, args...).Scan(&movie.Version)
}
...
```

需要强调的是——就像我们的 Insert() 方法一样——Update() 方法将指向 Movie 结构体的指针作为输入参数，并再次就地修改它——这次仅更新新的版本号。

## 创建 API 处理器

现在让我们回到 cmd/api/movies.go 文件，并更新它，以包含全新的 updateMovieHandler 方法。

| 方法 | URL 模式 | 处理器 | 操作 |
|--------|-------------|---------|--------|
| PUT | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |

这个处理器的优点在于，我们已经为它打好了所有基础——我们在这里的工作主要就是把已经写好的代码和辅助函数连接起来，以处理请求。

具体来说，我们需要：

- 1. 使用 `app.readIDParam()` 辅助函数从 URL 中提取电影 ID。
- 2. 使用我们在上一章中编写的 `Get()` 方法从数据库中获取相应的电影记录。
- 3. 将包含更新后电影数据的 JSON 请求体读取到 `input` 结构体中。
- 4. 将数据从 `input` 结构体复制到电影记录中。
- 5. 使用 `data.ValidateMovie()` 函数检查更新后的电影记录是否有效。
- 6. 调用 `Update()` 方法将更新后的电影记录存储到数据库中。
- 7. 使用 `app.writeJSON()` 辅助函数将更新后的电影数据写入 JSON 响应。

那么，让我们直接开始吧：

```
File: cmd/api/movies.go

package main

...

func (app *application) updateMovieHandler(w http.ResponseWriter, r *http.Request) {
    // Extract the movie ID from the URL.
    id, err := app.readIDParam(r)
    if err != nil {
        app.notFoundResponse(w, r)
        return
    }
}

// Fetch the existing movie record from the database, sending a 404 Not Found
// response to the client if we couldn't find a matching record.
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

// Declare an input struct to hold the expected data from the client.
var input struct {
    Title    string       `json:"title"`
    Year     int32        `json:"year"`
    Runtime  data.Runtime `json:"runtime"`
    Genres   []string     `json:"genres"`
}

// Read the JSON request body data into the input struct.
err = app.readJSON(w, r, &input)
if err != nil {
    app.badRequestResponse(w, r, err)
    return
}

// Copy the values from the request body to the appropriate fields of the movie
// record.
movie.Title = input.Title
movie.Year = input.Year
movie.Runtime = input.Runtime
movie.Genres = input.Genres

// Validate the updated movie record, sending the client a 422 Unprocessable Entity
// response if any checks fail.
v := validator.New()

if data.ValidateMovie(v, movie); !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

// Pass the updated movie record to our new Update() method.
err = app.models.Movies.Update(movie)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Write the updated movie record in a JSON response.
err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

最后，为了收尾，我们还需要更新应用路由，以包含新的端点。如下所示：

```
File: cmd/api/routes.go

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
// Add the route for the PUT /v1/movies/:id endpoint.
router.HandlerFunc(http.MethodPut, "/v1/movies/:id",
app.updateMovieHandler)

return router
}
```

## 使用新的端点

至此，我们现在可以尝试一下了！

为了演示，让我们继续使用本章开头给出的示例，将 *黑豹* 的记录更新为包含 `sci-fi` 类型。提醒一下，当前记录看起来像这样：

```
$ curl localhost:4000/v1/movies/2
{
    "movie": {
        "id": 2,
        "title": "Black Panther",
        "year": 2018,
        "runtime": "134 mins",
        "genres": [
            "action",
```

你还应该能够通过再次发出 GET `/v1/movies/2` 请求来验证更改是否已持久化，如下所示：

```
$ curl localhost:4000/v1/movies/2
{
  "movie": {
    "id": 2,
    "title": "Black Panther",
    "year": 2018,
    "runtime": "134 mins",
    "genres": [
      "sci-fi",
      "action",
      "adventure"
    ],
    "version": 2
  }
}
```

## 删除电影

在本章中，我们将添加最后一个 CRUD 端点，以便客户端可以从我们的系统中 *删除特定电影*。

| 方法 | URL 模式 | 处理器 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PUT | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |

与我们 API 中的其他端点相比，我们在这里要实现的行为相当直接。

- 如果 URL 中提供的 `id` 对应的电影存在于数据库中，我们希望删除相应的记录，并向客户端返回成功消息。
- 如果电影 `id` 不存在，我们希望向客户端返回 `404 Not Found` 响应。

```go
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.notFoundResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

// Return a 200 OK status code along with a success message.
err = app.writeJSON(w, http.StatusOK, envelope{"message": "movie successfully deleted"}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
```

注意：你可能更倾向于在这里发送一个空响应体和 `204 No Content` 状态码，而不是 `"movie successfully deleted"` 消息。这实际上取决于你的客户端是谁——如果它们是人类，那么发送一条类似上面的消息是一种很好的用户体验；如果它们是机器，那么 `204 No Content` 响应可能就足够了。

最后，我们需要在我们的 `cmd/api/routes.go` 文件中接入新路由：

```
File: cmd/api/routes.go
```

