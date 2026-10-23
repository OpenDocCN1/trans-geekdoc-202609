

```
"^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\\.
[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$"
```

在你的代码中，这个正则表达式模式应该全部在同一行，且没有空白字符。

## 执行验证检查

好了，让我们开始使用 Validator 类型吧！

我们需要做的第一件事是更新我们的 `cmd/api/errors.go` 文件，添加一个新的 `failedValidationResponse()` 辅助函数，该函数会写出 `422 Unprocessable Entity` 状态码，并将我们新的 `Validator` 类型中 errors map 的内容作为 JSON 响应体。

```
File: cmd/api/errors.go

package main

...

// Note that the errors parameter here has the type map[string]string, which is exactly
// the same as the errors map contained in our Validator type.
func (app *application) failedValidationResponse(w http.ResponseWriter, r *http.Request, errors map[string]string) {
    app.errorResponse(w, r, http.StatusUnprocessableEntity, errors)
}
```

完成之后，回到你的 createMovieHandler，更新它以对输入结构体执行必要的验证检查。如下所示：

```
File: cmd/api/movies.go

package main

import (
    "fmt"
    "net/http"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator" // New import
)

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title    string       `json:"title"`
        Year     int32        `json:"year"`
        Runtime  data.Runtime `json:"runtime"`
        Genres   []string     `json:"genres"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    // Initialize a new Validator instance.
    v := validator.New()
```

```
// Use the Check() method to execute our validation checks. This will add the
// provided key and error message to the errors map if the check does not evaluate
// to true. For example, in the first line here we "check that the title is not
// equal to the empty string". In the second, we "check that the length of the title
// is less than or equal to 500 bytes" and so on.
v.Check(input.Title != "", "title", "must be provided")
v.Check(len(input.Title) <= 500, "title", "must not be more than 500 bytes long")

v.Check(input.Year != 0, "year", "must be provided")
v.Check(input.Year >= 1888, "year", "must be greater than 1888")
v.Check(input.Year <= int32(time.Now().Year()), "year", "must not be in the future")

v.Check(input.Runtime != 0, "runtime", "must be provided")
v.Check(input.Runtime > 0, "runtime", "must be a positive integer")

v.Check(input.Genres != nil, "genres", "must be provided")
v.Check(len(input.Genres) >= 1, "genres", "must contain at least 1 genre")
v.Check(len(input.Genres) <= 5, "genres", "must not contain more than 5 genres")
// Note that we're using the Unique helper in the line below to check that all
// values in the input.Genres slice are unique.
v.Check(validator.Unique(input.Genres), "genres", "must not contain duplicate values")

// Use the Valid() method to see if any of the checks failed. If they did, then use
// the failedValidationResponse() helper to send a response to the client, passing
// in the v.Errors map.
if !v.Valid() {
```

```
app.failedValidationResponse(w, r, v.Errors)
    return
}

    fmt.Fprintf(w, "%+v\n", input)
}
...
```

完成这些后，我们应该可以尝试一下了。重启 API，然后向 POST /v1/movies 端点发出一个包含无效数据的请求。类似如下：

```
$ BODY='{"title":"","year":1000,"runtime":"-123 mins","genres":["sci-fi","sci-fi"]}'
$ curl -i -d "$BODY" localhost:4000/v1/movies
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json
Date: Wed, 07 Apr 2021 10:33:57 GMT
Content-Length: 180

{
  "error": {
    "genres": "must not contain duplicate values",
    "runtime": "must be a positive integer",
    "title": "must be provided",
    "year": "must be greater than 1888"
  }
}
```

看起来很棒。我们的验证检查正在工作，并阻止了请求被成功执行——甚至更好——客户端会得到一个格式良好的 JSON 响应，其中包含清晰、信息丰富的错误消息，指出了每个问题。

如果你愿意，也可以尝试发送一个有效的请求。你会发现所有检查都成功通过，`input` 结构体会像之前一样被输出到 HTTP 响应中：

```
$ BODY='{"title":"Moana","year":2016,"runtime":"107 mins","genres":["animation","adventure"]}'
$ curl -i -d "$BODY" localhost:4000/v1/movies
HTTP/1.1 200 OK
Date: Wed, 07 Apr 2021 10:35:40 GMT
Content-Length: 65
Content-Type: text/plain; charset=utf-8

{Title:Moana Year:2016 Runtime:107 Genres:[animation adventure]}
```

## 使验证规则可重用

在大型项目中，你很可能希望在多个地方重用一些相同的验证检查。在我们的例子中——例如——当客户端*编辑*电影数据时，我们以后会用到许多相同的检查。

为了避免重复，我们可以将电影的验证检查收集到一个独立的 `ValidateMovie()` 函数中。理论上，这个函数几乎可以存在于我们代码库的任何地方——位于 `cmd/api/movies.go` 文件中的处理器旁边，或者可能在 `internal/validators` 包中。但就个人而言，我喜欢将验证检查放在 `internal/data` 包中，靠近相关的领域类型。

如果你在跟着做，请重新打开 `internal/data/movies.go` 文件，并添加一个 `ValidateMovie()` 函数，其中包含如下检查：

```
File: internal/data/movies.go

package data

import (
    "time"

    "greenlight.alexedwards.net/internal/validator" // New import
)

type Movie struct {
    ID        int64     `json:"id"`
    CreatedAt time.Time `json:"-"`
    Title     string    `json:"title"`
    Year      int32     `json:"year,omitempty"`
    Runtime   Runtime   `json:"runtime,omitempty"`
    Genres    []string  `json:"genres,omitempty"`
    Version   int32     `json:"version"`
}

func ValidateMovie(v *validator.Validator, movie *Movie) {
    v.Check(movie.Title != "", "title", "must be provided")
    v.Check(len(movie.Title) <= 500, "title", "must not be more than 500 bytes long")

    v.Check(movie.Year != 0, "year", "must be provided")
    v.Check(movie.Year >= 1888, "year", "must be greater than 1888")
    v.Check(movie.Year <= int32(time.Now().Year()), "year", "must not be in the future")
}
```

Title    string      `json:"title"`
Year     int32       `json:"year"`
Runtime  data.Runtime `json:"runtime"`
Genres   []string    `json:"genres"`
}

err := app.readJSON(w, r, &input)
if err != nil {
    app.badRequestResponse(w, r, err)
    return
}

// Copy the values from the input struct to a new Movie struct.
movie := &data.Movie{
    Title:    input.Title,
    Year:     input.Year,
    Runtime:  input.Runtime,
    Genres:   input.Genres,
}

// Initialize a new Validator.
v := validator.New()

// Call the ValidateMovie() function and return a response containing the errors if
// any of the checks fail.
if data.ValidateMovie(v, movie); !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

fmt.Fprintf(w, "%+v\n", input)
}
...

当你看到这段代码时，脑海中可能会出现几个问题。

首先，你可能想知道为什么我们在处理器中初始化 `Validator` 实例并将其传递给 `ValidateMovie()` 函数——而不是在 `ValidateMovie()` 中初始化它并将其作为返回值传递回来。

这是因为随着应用程序变得越来越复杂，我们需要从处理器调用*多个*验证辅助函数，而不是像上面那样只调用一个。因此，在处理器中初始化 `Validator` 并进行传递，为我们提供了更大的灵活性。

你可能还会想，为什么我们要将 JSON 请求解码到 `input` 结构体中，然后复制数据，而不是直接解码到 `Movie` 结构体中。

直接解码到 `Movie` 结构体的问题是，客户端可能会在其 JSON 请求中提供 `id` 和 `version` 键，并且相应的值会*毫无差错地*被解码到 `Movie` 结构体的 `ID` 和 `Version` 字段中——即使我们不希望如此。我们*可以*在事后检查 `Movie` 结构体中必要的字段，以确保它们是空的，但这感觉有点 hacky，而解码到一个中间结构体（就像我们在处理器中所做的那样）是一种更干净、更简单、更健壮的方法——尽管稍显冗长。

好了，这些解释说完后，你应该能够再次启动应用程序，并且从客户端角度来看，一切应该和以前一样工作。如果你发出无效请求，

