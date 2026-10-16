```
results := make(map[string]bool)

for _, url := range urls {
    go func(u string) {
        results[u] = wc(u)
    }(url)
}

time.Sleep(2 * time.Second)

    return results
}
```

By giving each anonymous function a parameter for the url - u - and then calling the anonymous function with the url as the argument, we make sure that the value of u is fixed as the value of url for the iteration of the loop that we're launching the goroutine in. u is a copy of the value of url, and so can't be changed.

Now if you're lucky you'll get:

```
PASS
ok      github.com/gypsydave5/learn-go-with-tests/concurrency/v1
```

But if you're unlucky (this is more likely if you run them with the benchmark as you'll get more tries)

```
fatal error: concurrent map writes

goroutine 8 [running]:
runtime.throw(0x12c5895, 0x15)
        /usr/local/Cellar/go/1.9.3/libexec/src/runtime/panic.go:
runtime.mapassign_faststr(0x1271d80, 0xc42007acf0, 0x12c6634, 0x
        /usr/local/Cellar/go/1.9.3/libexec/src/runtime/hashmap_f
github.com/gypsydave5/learn-go-with-tests/concurrency/v3.Website
        /Users/gypsydave5/go/src/github.com/gypsydave5/learn-go-
runtime.goexit()
```