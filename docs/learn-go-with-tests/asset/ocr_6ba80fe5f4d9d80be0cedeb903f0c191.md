```
type WebsiteChecker func(string) bool

func CheckWebsites(wc WebsiteChecker, urls []string) map[string]
results := make(map[string]bool)

    for _, url := range urls {
        go func() {
            results[url] = wc(url)
        }()
    }

    return results
}
```

Because the only way to start a goroutine is to put `go` in front of a function call, we often use *anonymous functions* when we want to start a goroutine. An anonymous function literal looks just the same as a normal function declaration, but without a name (unsurprisingly). You can see one above in the body of the `for` loop.

Anonymous functions have a number of features which make them useful, two of which we're using above. Firstly, they can be executed at the same time that they're declared - this is what the `()` at the end of the anonymous function is doing. Secondly they maintain access to the lexical scope they are defined in - all the variables that are available at the point when you declare the anonymous function are also available in the body of the function.

The body of the anonymous function above is just the same as the loop body was before. The only difference is that each iteration of the loop will start a new goroutine, concurrent with the current process (the `WebsiteChecker` function) each of which will add its result to the results map.

But when we run `go test`:

```
--- FAIL: TestCheckWebsites (0.00s)
```