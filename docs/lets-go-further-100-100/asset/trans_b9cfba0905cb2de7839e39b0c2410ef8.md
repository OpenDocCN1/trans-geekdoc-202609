
例如，如果我们希望将 Runtime 字段的值表示为 JSON 字符串（而不是数字），可以使用 string 指令，如下所示：

```
type Movie struct {
    ID          int64       `json:"id"`
    CreatedAt   time.Time   `json:"-"`
    Title       string      `json:"title"`
    Year        int32       `json:"year,omitempty"`
    Runtime     int32       `json:"runtime,omitempty,string"` // Add the string directive
    Genres      []string    `json:"genres,omitempty"`
    Version     int32       `json:"version"`
}
```

而生成的 JSON 输出将如下所示：

```
{
    "id": 123,
    "title": "Casablanca",
    "runtime": "102",     ← This is now a string
    "genres": [
        "drama",
        "romance",
        "war"
    ],
    "version": 1
}
```

请注意，`string` 指令仅适用于类型为 `int*`、`uint*`、`float*` 或 `bool` 的结构体字段。对于其他任何类型的结构体字段，该指令将不起作用。

## 第 3.4 章

## 格式化与封装响应

到目前为止，在本书中，我们通常使用 Firefox 向 API 发起请求，得益于内置 JSON 查看器提供的“美化打印”，JSON 响应很容易阅读。

但是，如果你尝试使用 curl 发起一些请求，你会看到实际的 JSON 响应数据都挤在一行，没有空白字符。

```
$ curl localhost:4000/v1/healthcheck
{"environment":"development","status":"available","version":"1.0.0"}

$ curl localhost:4000/v1/movies/123
{"id":123,"title":"Casablanca","runtime":102,"genres":["drama","romance","war"],"version":1}
```

我们可以使用 `json.MarshalIndent()` 函数（而不是常规的 `json.Marshal()` 函数）来编码响应数据，从而让它们在终端中更易读。该函数会自动为 JSON 输出添加空白字符，将每个元素放在单独的行上，并为每一行添加可选的*前缀*和*缩进*字符。

让我们更新 `writeJSON()` 辅助函数来使用这个功能：

注意：在幕后，`json.MarshalIndent()` 的工作方式是正常调用 `json.Marshal()`，然后通过独立的 `json.Indent()` 函数处理 JSON 以添加空白字符。还有一个反向函数 `json.Compact()` 可用，你可以使用它从 JSON 中移除空白字符。

## 封装响应

接下来，让我们更新响应，使 JSON 数据始终*封装*在父级 JSON 对象中。类似于这样：

```
{
  "movie": {
    "id": 123,
    "title": "Casablanca",
    "runtime": 102,
    "genres": [
      "drama",
      "romance",
      "war"
    ],
    "version":1
  }
}
```

注意这里电影数据是如何嵌套在键 "movie" 下的，而不是作为顶层的 JSON 对象本身？

```
package main

...

// Define an envelope type.
type envelope map[string]interface{}

// Change the data parameter to have the type envelope instead of interface{}.
func (app *application) writeJSON(w http.ResponseWriter, status int, data envelope, headers http.Header) error {
    js, err := json.MarshalIndent(data, "", "\t")
    if err != nil {
        return err
    }

    js = append(js, '\n')

    for key, value := range headers {
        w.Header()[key] = value
    }

    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(status)
    w.Write(js)

    return nil
}
```

然后我们需要更新 showMovieHandler，创建一个包含电影数据的 envelope 映射实例，并将它传递给 writeJSON() 辅助函数，而不是直接传递电影数据。

就像这样：

```go
package main

...

func (app *application) showMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        http.NotFound(w, r)
        return
    }

    movie := data.Movie{
        ID:         id,
        CreatedAt:  time.Now(),
        Title:      "Casablanca",
        Runtime:    102,
        Genres:     []string{"drama", "romance", "war"},
        Version:    1,
    }

    // Create an envelope{"movie": movie} instance and pass it to writeJSON(), instead
    // of passing the plain movie struct.
    err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

我们还需要更新 healthcheckHandler 中的代码，使它也将 envelope 类型传递给 writeJSON() 辅助函数：

```
File: cmd/api/healthcheck.go

package main

...

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    // Declare an envelope map containing the data for the response. Notice that the way
    // we've constructed this means the environment and version data will now be nested
    // under a system_info key in the JSON response.
    env := envelope{
        "status": "available",
        "system_info": map[string]string{
            "environment": app.config.env,
            "version":     version,
        },
    }

    err := app.writeJSON(w, http.StatusOK, env, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

好了，让我们试试这些改动。重启服务器，然后使用 curl 再次向 API 端点发起一些请求。

现在你应该会得到如下格式的响应。

```
$ curl localhost:4000/v1/movies/123
{
    "movie": {
        "id": 123,
        "title": "Casablanca",
        "runtime": 102,
        "genres": [
            "drama",
            "romance",
            "war"
        ],
        "version":1
    }
}

$ curl localhost:4000/v1/healthcheck
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
```

## 附加信息

## 响应结构

## 高级 JSON 自定义

通过使用结构体标签、添加空白字符和封装数据，我们已经能够为 JSON 响应添加相当多的自定义。但当这些还不够，你需要更大的自由来进一步自定义 JSON 时，会发生什么？

要回答这个问题，我们首先需要讨论一些关于 Go 在幕后如何处理 JSON 编码的理论。需要理解的关键点是：

> *当 Go 将特定类型编码为 JSON 时，它会检查该类型是否实现了 `MarshalJSON()` 方法。如果有，Go 将调用此方法来确定如何对其进行编码。*

这种表述有点模糊，所以让我们说得更精确些。

严格来说，当 Go 将特定类型编码为 JSON 时，它会检查该类型是否满足 `json.Marshaler` 接口，该接口如下所示：

```
type Marshaler interface {
    MarshalJSON() ([]byte, error)
}
```

如果该类型确实满足该接口，Go 将调用其 `MarshalJSON()` 方法，并使用它返回的 `[]byte` 切片作为编码后的 JSON 值。

如果该类型没有 `MarshalJSON()` 方法，则 Go 将回退到基于自身内部规则尝试将其编码为 JSON。

因此，如果我们想要自定义某些内容的编码方式，我们所需要做的就是在其上实现一个 `MarshalJSON()` 方法，该方法返回一个 `[]byte` 切片，其中包含*其自身的自定义 JSON 表示*。

> **提示：** 如果你查看 Go 的 `time.Time` 类型的源代码，就能看到这一点。在幕后，`time.Time` 实际上是一个 `struct`，但它有一个 `MarshalJSON()` 方法，该方法输出其自身的 RFC 3339 格式表示。每当 `time.Time` 值被编码为 JSON 时，调用的就是这个方法。

## 自定义 Runtime 字段

为了帮助说明这一点，让我们看看应用程序中的一个具体例子。

当我们的 `Movie` 结构体被编码为 JSON 时，`Runtime` 字段（属于 `int32` 类型）当前被格式化为 JSON 数字。让我们将其改为以字符串格式 `"<runtime> mins"` 进行编码。就像这样：

