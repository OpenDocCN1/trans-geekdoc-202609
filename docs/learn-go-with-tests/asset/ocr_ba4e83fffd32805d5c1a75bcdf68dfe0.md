+   - Why are we testing the speeds of the websites one after another when Go is great at concurrency? We should be able to check both at the same time.
+   - We don't really care about *the exact response times* of the requests, we just want to know which one comes back first.

To do this, we're going to introduce a new construct called `select` which helps us synchronise processes really easily and clearly.

```
```go
func Racer(a, b string) (winner string) {
    select {
    case <-ping(a):
        return a
    case <-ping(b):
        return b
    }
}
```
```

```
```go
func ping(url string) chan struct{} {
    ch := make(chan struct{})
    go func() {
        http.Get(url)
        close(ch)
    }()
    return ch
}
```
```

# ping

We have defined a function `ping` which creates a `chan struct{}` and returns it.

In our case, we don't *care* what type is sent to the channel, *we just want to signal we are done* and closing the channel works perfectly!

Why `struct{}` and not another type like a `bool`? Well, a `chan struct{}` is the smallest data type available from a memory perspective so we get no allocation versus a `bool`. Since we are