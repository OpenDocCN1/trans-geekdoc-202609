

```go
"fmt"
"io"
"net/http"
"strconv"
"strings" // New import

"github.com/julienschmidt/httprouter"
)

...

func (app *application) readJSON(w http.ResponseWriter, r *http.Request, dst interface{}) error {
    // Use http.MaxBytesReader() to limit the size of the request body to 1MB.
    maxBytes := 1_048_576
    r.Body = http.MaxBytesReader(w, r.Body, int64(maxBytes))

    // Initialize the json.Decoder, and call the DisallowUnknownFields() method on it
    // before decoding. This means that if the JSON from the client now includes any
    // field which cannot be mapped to the target destination, the decoder will return
    // an error instead of just ignoring the field.
    dec := json.NewDecoder(r.Body)
    dec.DisallowUnknownFields()

    // Decode the request body to the destination.
    err := dec.Decode(dst)
    if err != nil {
        var syntaxError *json.SyntaxError
        var unmarshalTypeError *json.UnmarshalTypeError
        var invalidUnmarshalError *json.InvalidUnmarshalError

        switch {
        case errors.As(err, &syntaxError):
            return fmt.Errorf("body contains badly-formed JSON (at character %d)", syntaxError.Offset)
```
```
case errors.Is(err, io.ErrUnexpectedEOF):
    return errors.New("body contains badly-formed JSON")

case errors.As(err, &unmarshalTypeError):
    if unmarshalTypeError.Field != "" {
        return fmt.Errorf("body contains incorrect JSON type for field %q", unmarshalTypeError.Field)
    }
    return fmt.Errorf("body contains incorrect JSON type (at character %d)", unmarshalTypeError.Offset)

case errors.Is(err, io.EOF):
    return errors.New("body must not be empty")

    // If the JSON contains a field which cannot be mapped to the target destination
    // then Decode() will now return an error message in the format
    "json: unknown
    // field \"<name>\". We check for this, extract the field name from
    the error,
    // and interpolate it into our custom error message. Note that
    there's an open
    // issue at https://github.com/golang/go/issues/29035 regarding
    turning this
    // into a distinct error type in the future.
    case strings.HasPrefix(err.Error(), "json: unknown field "):
        fieldName := strings.TrimPrefix(err.Error(), "json: unknown field ")
        return fmt.Errorf("body contains unknown key %s", fieldName)

    // If the request body exceeds 1MB in size the decode will now fail
    with the
    // error "http: request body too large". There is an open issue about
    turning
    // this into a distinct error type at
    https://github.com/golang/go/issues/30715.
    case err.Error() == "http: request body too large":
        return fmt.Errorf("body must not be larger than %d bytes",
maxBytes)

    case errors.As(err, &invalidUnmarshalError):
        panic(err)

    default:
        return err
    }
}

    // Call Decode() again, using a pointer to an empty anonymous struct as the
    // destination. If the request body only contained a single JSON value this will
    // return an io.EOF error. So if we get anything else, we know that there is
    // additional data in the request body and we return our own custom error message.
    err = dec.Decode(&struct{}{})
    if err != io.EOF {
        return errors.New("body must only contain a single JSON value")
    }

    return nil
}
```

做完这些修改后，让我们再试一下本章前面提到的请求：

```
$ curl -d '{"title": "Moana", "rating":"PG"}' localhost:4000/v1/movies
{
    "error": "body contains unknown key \"rating\""
}

$ curl -d '{"title": "Moana"}{"title": "Top Gun"}' localhost:4000/v1/movies
```
```
{
  "error": "body must only contain a single JSON value"
}

$ curl -d '{"title": "Moana"} :~()' localhost:4000/v1/movies
{
  "error": "body must only contain a single JSON value"
}
```

现在这些处理得好多了——请求处理会被终止，客户端会收到一条清晰的错误消息，准确解释了问题所在。

最后，我们来尝试发送一个非常大的 JSON 请求体。

为了演示这一点，我创建了一个 1.5MB 的 JSON 文件，你可以运行以下命令将其下载到 `/tmp` 目录：

```
$ wget -O /tmp/largefile.json
https://www.alexedwards.net/static/largefile.json
```

如果你尝试将这个文件作为请求体发送到 `POST /v1/movies` 端点，`http.MaxBytesReader()` 检查就会生效，你应该会得到类似如下的响应：

```
$ curl -d @/tmp/largefile.json localhost:4000/v1/movies
{
```

## 自定义 JSON 解码

在本书前面，我们为 API 添加了一些自定义 JSON 编码行为，以便在 JSON 响应中以 "<runtime> mins" 的格式显示电影时长信息。

在本章中，我们将从另一个角度来看待这个问题，并更新我们的应用程序，使 `createMovieHandler` 接受这种格式的时长信息。

如果你现在就尝试发送一个带有这种电影时长格式的请求，你会得到 `400 Bad Request` 响应（因为无法将 JSON 字符串解码为 `int32` 类型）。如下所示：

```
$ curl -d '{"title": "Moana", "runtime": "107 mins"}'
localhost:4000/v1/movies
{
  "error": "body contains incorrect JSON type for \"runtime\""
}
```

要使其工作，我们需要做的是*拦截解码过程*，并手动将 "<runtime> mins" 这个 JSON 字符串转换为 `int32`。

那么我们该怎么做呢？

```go
package main

...

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title   string       `json:"title"`
        Year    int32        `json:"year"`
        Runtime data.Runtime `json:"runtime"` // Make this field a data.Runtime type.
        Genres  []string     `json:"genres"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    fmt.Fprintf(w, "%+v\n", input)
}

...
```

然后，让我们打开 `internal/data/runtime.go` 文件，为我们 `Runtime` 类型添加一个 `UnmarshalJSON()` 方法。在这个方法中，我们需要解析格式为 "`<runtime> mins`" 的 JSON 字符串，将时长数字转换为 `int32`，然后将其赋值给 `Runtime` 值本身。

这实际上有点复杂，而且有一些重要细节，所以最好直接进入代码，并随着代码逐步用注释来解释。

## 验证 JSON 输入

在许多情况下，你会希望对来自客户端的数据执行额外的验证检查，以确保在处理之前符合你的特定业务规则。在本章中，我们将通过更新 `createMovieHandler` 来演示如何在 JSON API 中做到这一点，检查以下内容：

- 客户端提供的电影标题不能为空，并且不能超过 500 个字节。
- 电影年份不能为空，并且必须在 1888 年到当前年份之间。
- 电影时长不能为空，并且必须是一个正整数。
- 电影必须包含一至五个（不重复的）类型。

如果这些检查中有任何一项失败，我们就会向客户端发送一个 `422 Unprocessable Entity` 响应，并附带清晰描述验证失败的错误消息。

## 创建 validator 包

为帮助我们在整个项目中进行验证，我们将创建一个小的 `internal/validator` 包，其中包含一些简单的可复用辅助类型和函数。如果你正在跟着编码，请在机器上创建以下目录和文件：

```go
// New is a helper which creates a new Validator instance with an empty
errors map.
func New() *Validator {
    return &Validator{Errors: make(map[string]string)}
}

// Valid returns true if the errors map doesn't contain any entries.
func (v *Validator) Valid() bool {
    return len(v.Errors) == 0
}

// AddError adds an error message to the map (so long as no entry already
exists for
// the given key).
func (v *Validator) AddError(key, message string) {
    if _, exists := v.Errors[key]; !exists {
        v.Errors[key] = message
    }
}

// Check adds an error message to the map only if a validation check is not
'ok'.
func (v *Validator) Check(ok bool, key, message string) {
    if !ok {
        v.AddError(key, message)
    }
}

// In returns true if a specific value is in a list of strings.
func In(value string, list ...string) bool {
    for i := range list {
        if value == list[i] {
            return true
        }
    }
    return false
}

// Matches returns true if a string value matches a specific regexp pattern.
```

