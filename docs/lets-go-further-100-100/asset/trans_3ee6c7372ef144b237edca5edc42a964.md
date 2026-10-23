
```
{
  "id": 123,
  "title": "Casablanca",
  "runtime": "102 mins",    ← This is now a string
  "genres": [
    "drama",
    "romance",
    "war"
  ],
  "version":1
}
```

有几种方法可以实现这一点，但一种简洁明了的方法是为 Runtime 字段专门创建一个自定义类型，并在该自定义类型上实现 MarshalJSON() 方法。

防止 internal/data/movie.go 文件变得杂乱，让我们创建一个新文件来存放 Runtime 类型的逻辑：

```
$ touch internal/data/runtime.go
```

然后继续添加以下代码：

```
File: internal/data/runtime.go

package data

import (
  "fmt"
  "strconv"
)
// Declare a custom Runtime type, which has the underlying type int32 (the
same as our
// Movie struct field).
type Runtime int32

// Implement a MarshalJSON() method on the Runtime type so that it satisfies
the
// json.Marshaler interface. This should return the JSON-encoded value for
the movie
// runtime (in our case, it will return a string in the format "<runtime>
mins").
func (r Runtime) MarshalJSON() ([]byte, error) {
    // Generate a string containing the movie runtime in the required format.
    jsonValue := fmt.Sprintf("%d mins", r)

    // Use the strconv.Quote() function on the string to wrap it in double
quotes. It
    // needs to be surrounded by double quotes in order to be a valid *JSON
string*.
    quotedJSONValue := strconv.Quote(jsonValue)

    // Convert the quoted string value to a byte slice and return it.
    return []byte(quotedJSONValue), nil
}
```

这里有两点我想强调：

- 如果你的 MarshalJSON() 方法返回一个 JSON 字符串值，像我们这样，那么你必须在返回前用双引号将字符串包裹起来。否则它不会被解释为 JSON 字符串，你会收到类似以下的运行时错误：

```
json: error calling MarshalJSON for type data.Runtime: invalid character 'm' after top-level value
```

- 我们故意为 `MarshalJSON()` 方法使用 *值接收者* 而不是像 `func (r *Runtime) MarshalJSON()` 这样的 *指针接收者*。这样做可以提供更大的灵活性，因为这意味着我们的自定义 JSON 编码既适用于 `Runtime` 值，也适用于指向 `Runtime` 值的指针。Effective Go 中提到：

> 关于接收者指针与值的规则是：值方法可以对指针和值调用，但指针方法只能对指针调用。

**提示：** 如果你对指针接收者和值接收者之间的区别没有把握，那么这篇博客文章提供了很好的总结。

好的，现在自定义 `Runtime` 类型已定义，打开你的 `internal/data/movies.go` 文件并按如下方式更新 `Movie` 结构体以使用它：

```
File: internal/data/movies.go

package data

import (
"time"
)

type Movie struct {
    ID          int64       `json:"id"`
    CreatedAt   time.Time   `json:"-"`
    Title       string      `json:"title"`
    Year        int32       `json:"year,omitempty"`
    // Use the Runtime type instead of int32. Note that the omitempty
    directive will
    // still work on this: if the Runtime field has the underlying value 0,
    then it will
    // be considered empty and omitted -- and the MarshalJSON() method we
    just made
    // won't be called at all.
    Runtime Runtime    `json:"runtime,omitempty"`
    Genres  []string   `json:"genres,omitempty"`
    Version int32      `json:"version"`
}
```

让我们通过重启 API 并向 GET /v1/movies/:id 端点发出请求来试试。你现在应该会看到一个包含自定义 runtime 值的响应，格式为 "<runtime> mins"，类似于这样：

```
$ curl localhost:4000/v1/movies/123
{
    "movie": {
        "id": 123,
        "title": "Casablanca",
        "runtime": "102 mins",
        "genres": [
            "drama",
            "romance",
            "war"
        ],
        "version": 1
    }
}
```

总的来说，这是一种生成自定义 JSON 的相当不错的方法。我们的代码简洁清晰，而且我们拥有一个自定义的 Runtime 类型，可以在任何需要时使用。

但也有一个缺点。需要注意的是，使用自定义类型在将代码与其他包集成时有时会显得 awkward，你可能需要执行类型转换，将自定义类型转换为其他包理解和接受的值，反之亦然。

## 附加信息

这里有几种可行的替代方法可以达到同样的最终结果，我想快速描述一下并讨论它们的优缺点。如果你正在跟随构建进行编码，请不要做这些更改（除非你好奇，当然！）。

### 替代方案 #1 - 自定义 Movie 结构体

如果不创建自定义 Runtime 类型，我们本可以在 Movie 结构体上实现 MarshalJSON() 方法并自定义整个结构体。像这样：

```
// Note that there are no struct tags on the Movie struct itself.
type Movie struct {
    ID          int64
    CreatedAt   time.Time
    Title       string
    Year        int32
    Runtime     int32
    Genres      []string
    Version     int32
}

// Implement a MarshalJSON() method on the Movie struct, so that it satisfies the
// json.Marshaler interface.
func (m Movie) MarshalJSON() ([]byte, error) {
    // Declare a variable to hold the custom runtime string (this will be the empty
    // string "" by default).
    var runtime string

    // If the value of the Runtime field is not zero, set the runtime variable to be a
    // string in the format "<runtime> mins".
    if m.Runtime != 0 {
        runtime = fmt.Sprintf("%d mins", m.Runtime)
    }

    // Create an anonymous struct to hold the data for JSON encoding. This has exactly
    // the same fields, types and tags as our Movie struct, except that the Runtime
    // field here is a string, instead of an int32. Also notice that we don't
```

"<runtime> mins" 首先。然后最后，我们将匿名结构体编码为 JSON —— 而不是原始的 Movie 结构体 —— 并返回它。

也值得指出的是，这样的设计使得 omitempty 指令仍然适用于我们的自定义编码。如果 Runtime 字段的值为零，则本地 runtime 变量将保持等于 ""，这（正如我们之前提到的）在编码目的上被视为“空”。

### 替代方案 #2 - 嵌入别名

上述方法的缺点是代码感觉相当冗长且重复。你可能会想：有没有更好的方法？

为了减少重复，而不是逐行写出所有结构体字段，可以在匿名结构体中嵌入 Movie 结构体的别名。像这样：

```
// Notice that we use the - directive on the Runtime field, so that it never appears
// in the JSON output.
type Movie struct {
    ID        int64     `json:"id"`
    CreatedAt time.Time `json:"-"`
    Title     string    `json:"title"`
    Year      int32     `json:"year,omitempty"`
    Runtime   int32     `json:"-"`
    Genres    []string  `json:"genres,omitempty"`
    Version   int32     `json:"version"`
}
```

```
func (m Movie) MarshalJSON() ([]byte, error) {
    // Create a variable holding the custom runtime string, just like before.
    var runtime string

    if m.Runtime != 0 {
        runtime = fmt.Sprintf("%d mins", m.Runtime)
    }

    // Define a MovieAlias type which has the underlying type Movie. Due to
    the way that
        // Go handles type definitions
    (https://golang.org/ref/spec#Type_definitions) the
        // MovieAlias type will contain all the fields that our Movie struct has
    but,
        // importantly, none of the methods.
    type MovieAlias Movie

    // Embed the MovieAlias type inside the anonymous struct, along with a
    Runtime field
        // that has the type string and the necessary struct tags. It's important
    that we
        // embed the MovieAlias type here, rather than the Movie type directly,
    to avoid
        // inheriting the MarshalJSON() method of the Movie type (which would
    result in an
        // infinite loop during encoding).
    aux := struct {
        MovieAlias
        Runtime string `json:"runtime,omitempty"`
    }{
        MovieAlias: MovieAlias(m),
        Runtime:    runtime,
    }

    return json.Marshal(aux)
}
```
