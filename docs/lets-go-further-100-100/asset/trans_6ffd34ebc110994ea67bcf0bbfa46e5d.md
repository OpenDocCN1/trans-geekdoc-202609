
```
}

fmt.Printf("type: %T; value: %v\n", n, n)
```

## 将打印：

```
type: float64; value: 10
```

如果你想将值作为整数获取（而不是 `float64`），你应该在解码之前对你的 `json.Decoder` 实例调用 `UseNumber()` 方法。这将导致所有 JSON 数字被解码为底层类型 `json.Number` 而不是 `float64`。

`json.Number` 类型随后提供了一个 `Int64()` 方法，你可以调用它来将数字作为 `int64` 获取，或者 `String()` 方法来将数字作为 `string` 获取。例如：

```
js := `10`

var n interface{}

dec := json.NewDecoder(strings.NewReader(js))
dec.UseNumber() // Call the UseNumber() method on the decoder before using it.
err := dec.Decode(&n)
if err != nil {
    log.Fatal(err)
}
```

```go
// Type assert the interface{} value to a json.Number, and then call the
Int64() method
// to get the number as a Go int64.
nInt64, err := n.(json.Number).Int64()
if err != nil {
    log.Fatal(err)
}

// Likewise, you can use the String() method to get the number as a Go
string.
nString := n.(json.Number).String()

fmt.Printf("type: %T; value: %v\n", n, n)
fmt.Printf("type: %T; value: %v\n", nInt64, nInt64)
fmt.Printf("type: %T; value: %v\n", nString, nString)
```

这将打印出：

```text
type: json.Number; value: 10
type: int64; value: 10
type: string; value: 10
```

## 结构体标签指令

使用结构体标签 `json:"-"` 在结构体字段上会导致在解码 JSON 时将其 *忽略*，即使 JSON 输入中包含对应的键/值对。例如：

```go
js := `{"name": "alice", "age": 21}`
```

## 请求上下文超时

作为本书中用于管理数据库超时的模式的替代方案，我们本可以在处理器中使用请求上下文作为父上下文创建带超时的上下文——然后将上下文传递给数据库模型。

大致来说，模式如下：

```go
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    ...
    // Create a context.Context with a one-second timeout deadline and which has the
    // request context as the 'parent'.
    ctx, cancel := context.WithTimeout(r.Context(), time.Second)
    defer cancel()

    // Pass the context on to the Get() method.
    example, err := app.models.Example.Get(ctx, id)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrNotFound):
            app.notFoundResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }
}
```

```
...
}
```

在很多方面，这样做被认为是一种良好的实践。允许上下文在你的应用程序中“流动”通常是一个好主意，而且这种方法也更灵活——无论谁在调用数据库模型，都可以轻松控制超时持续时间，而不必总是使用数据库模型设定的固定持续时间。

但使用请求上下文作为父上下文会引入大量额外的复杂性。

需要注意的关键是，如果客户端关闭其 HTTP 连接，则 *请求上下文将被取消*。根据 `net/http` 文档：

> 对于传入的服务器请求，[请求] 上下文会在客户端连接关闭时、请求被取消（使用 HTTP/2）或 ServeHTTP 方法返回时被取消。

如果我们使用请求上下文作为父上下文，那么此取消信号将传递到我们的数据库驱动程序 `pq`，正在运行的 SQL 查询将被终止，其方式与上下文超时时完全相同。重要的是，这意味着我们会收到与数据库查询超时时相同的 `pq: canceling statement due to user request` 错误消息。

一方面这是积极的一面——如果没有剩余客户端可以返回响应，我们不妨取消 SQL 查询并释放资源。

另一方面，我们会在两种截然不同的场景中收到相同的错误消息：

- 当数据库查询花费的时间过长时，在这种情况下我们希望将其记录为错误。
- 当客户端关闭连接时——这可能由于许多无害的原因发生，例如用户关闭浏览器标签页或终止进程。从我们应用程序的角度来看，这 *真的* 不是错误，我们可能希望忽略它或将其记录为警告。

幸运的是，通过在上下文上调用 `ctx.Err()` 方法，*是可以* 区分这两种场景的。如果上下文被取消（由于客户端关闭连接），则 `ctx.Err()` 将返回错误 `context.Canceled`。如果达到超时，则它将返回 `context.DeadlineExceeded`。如果同时达到截止时间和上下文被取消，则 `ctx.Err()` 将返回先发生的那个。

还需要注意的是，如果客户端在查询被 `sql.DB` 排队时关闭连接，你可能会收到 `context.Canceled` 错误，同样 `Scan()` 也可能返回 `context.Canceled` 错误。

综合起来，一个合理的管理方式是在我们的
数据库模型中检查错误 `pq: canceling statement due to user request`，并在返回之前用 `ctx.Err()` 的错误将其包装。例如：

```
func (m ExampleModel) Get(ctx context.Context, id int64) (*Example, error) {
    query := `SELECT ... FROM examples WHERE id = $1`

    var example Example

    err := m.DB.QueryRowContext(ctx, query, id).Scan(...)

    if err != nil {
        switch {
        case err.Error() == "pq: canceling statement due to user request":
            // Wrap the error with ctx.Err().
            return nil, fmt.Errorf("%v: %w", err, ctx.Err())
        case errors.Is(err, sql.ErrNoRows):
            return nil, ErrNotFound
        default:
            return nil, err
        }
    }

    return &example, nil
}
```

然后在你的处理器中，你可以使用 `errors.Is()` 检查数据库模型返回的错误是否等于（或包装）`context.Canceled`，并相应地处理它。

```
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    ...
}
```

```go
ctx, cancel := context.WithTimeout(r.Context(), 3*time.Second)
defer cancel()

example, err := app.models.Example.Get(ctx, id)
if err != nil {
    switch {
    // If the error is equal to or wraps context.Canceled, then return
    // without taking
    // any further action.
    case errors.Is(err, context.Canceled):
        return
    case errors.Is(err, data.ErrNotFound):
        app.notFoundResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

...
}
```

除了这种额外的错误处理之外，你还需要注意使用后台 goroutine 时的影响。请记住我之前引用的关于请求上下文取消的内容：

> *对于传入的服务器请求，[请求] 上下文会在 ... ServeHTTP 方法返回时被取消。*

这意味着，如果你从请求上下文派生上下文，则在后台 goroutine 中使用该上下文的任何 SQL 查询都将在初始请求的 HTTP 响应发送时被取消！如果你不希望出现这种情况（你可能确实不希望），那么你
无论如何都需要使用 `context.Background()` 为后台 goroutine 创建一个全新的上下文。

因此，总结一下，使用请求上下文作为数据库超时的父上下文会增加相当多的行为复杂性，并引入你和任何在代码库上工作的人都需要了解的细微差别。你必须问：*值得吗？*

对于大多数应用程序的大多数端点来说，这可能不值得。例外可能是在资源经常接近饱和点运行的应用程序，或执行运行缓慢或计算成本非常高的 SQL 查询的特定端点。在这些情况下，当客户端消失时积极取消查询可能会产生有意义的积极影响，从而使权衡值得。

