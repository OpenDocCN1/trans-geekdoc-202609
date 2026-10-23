
```
}

fmt.Printf("type: %T; value: %v\n", n, n)
```

## Will print:

```
type: float64; value: 10
```

If you want to get the value as an integer (instead of a `float64`) you should call the `UseNumber()` method on your `json.Decoder` instance before decoding. This will cause all JSON numbers to be decoded to the underlying type `json.Number` instead of `float64`.

The `json.Number` type then provides an `Int64()` method that you can call to get the number as an `int64`, or the `String()` method to get the number as a `string`. For example:

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

This will print out:

```text
type: json.Number; value: 10
type: int64; value: 10
type: string; value: 10
```

## Struct tag directives

Using the struct tag `json:"-"` on a struct field will cause it to be *ignored* when decoding JSON, even if the JSON input contains a corresponding key/value pair. For example:

```go
js := `{"name": "alice", "age": 21}`
```

## Request Context Timeouts

As an alternative to the pattern that we’ve used in this book for managing database timeouts, we could have created a context with a timeout in our handlers using the request context as the parent — and then passed the context on to our database model.

Very roughly, a pattern like this:

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

In many ways, doing this would be considered good practice. Allowing context to ‘flow’ through your application is generally a good idea, and this approach is also more flexible — whatever is calling the database model can easily control the timeout duration rather than it always being a fixed duration set by the database model.

But using the request context as the parent introduces a lot of additional complexity.

The key thing to be aware of is that the *request context will be canceled* if the client closes their HTTP connection. From the `net/http` docs:

> For incoming server requests, the [request] context is canceled when the client’s connection closes, the request is canceled (with HTTP/2), or when the ServeHTTP method returns.

If we use the request context as the parent, then this cancellation signal will bubble down to our database driver `pq` and the running SQL query will be terminated in exactly the same way that it is when a context timeout is reached. Importantly, it means we would receive the same `pq: canceling statement due to user request` error message that we do when a database query times out.

On one hand this is a positive thing — if there is no client left to return a response to, we may as well cancel the SQL query and free-up resources.

On the other hand, we will receive the same error message in two very different scenarios:

- When a database query takes too long to complete, in which case we would want to log it as an error.
- When a client closes the connection — which can happen for many innocuous reasons, such as a user closing a browser tab or terminating a process. It’s not *really* an error from our application’s point of view, and we would probably want to either ignore it or perhaps log it as a warning.

Fortunately, it *is* possible to tell these two scenarios apart by calling the `ctx.Err()` method on the context. If the context was canceled (due to a client closing the connection), then `ctx.Err()` will return the error `context.Canceled`. If the timeout was reached, then it will return `context.DeadlineExceeded` instead. If both the deadline is reached and the context is canceled, then `ctx.Err()` will surface whichever happened first.

It’s also important to be aware that you may receive a `context.Canceled` error if the client closes the connection while the query is queued by `sql.DB`, and likewise `Scan()` may return a `context.Canceled` error too.

Putting all that together, a sensible way to manage this is to check for the error `pq: canceling statement due to user request` in our

database model and wrap it with the error from `ctx.Err()` before returning. For example:

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

Then in your handlers you can use `errors.Is()` to check if the error returned by the database model is equal to (or wraps) `context.Canceled`, and manage it accordingly.

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

As well as this additional error handling, you also need to be aware of the implications when using background goroutines. Bear in mind what I quoted earlier about request context cancellation:

> *For incoming server requests, the [request] context is canceled ... when the ServeHTTP method returns.*

This means that if you derive your context from the request context, any SQL queries using the context in a background goroutine will be canceled when the HTTP response is sent for the initial request! If you don’t want that to be the case (and you probably don’t), then you

would need to create a brand-new context for the background goroutine using `context.Background()` anyway.

So, to summarize, using the request context as the parent context for database timeouts adds quite a lot of behavioral complexity and introduces nuances that you and anyone else working on the codebase needs to be aware of. You have to ask: *is it worth it?*

For most applications, on most endpoints, it’s probably not. The exceptions are probably applications which frequently run close to saturation point of their resources, or for specific endpoints which execute slow running or very computationally expensive SQL queries. In those cases, canceling queries aggressively when a client disappears may have a meaningful positive impact and make it worth the trade-off.
