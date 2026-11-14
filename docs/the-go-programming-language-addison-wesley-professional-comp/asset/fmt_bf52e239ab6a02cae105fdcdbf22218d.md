
## Bare Returns

```go
// CountWordsAndImages does an HTTP GET request for the HTML
// document url and returns the number of words and images in it.
func CountWordsAndImages(url string) (words, images int, err error) {
    resp, err := http.Get(url)
    if err != nil {
        return
    }

    doc, err := html.Parse(resp.Body)
    resp.Body.Close()
    if err != nil {
        err = fmt.Errorf("parsing HTML: %s", err)
        return
    }
    words, images = countWordsAndImages(doc)
    return
}

func countWordsAndImages(n *html.Node) (words, images int) { /* ... */ }
```

A bare `return` is a shorthand way to return each of the named result variables in order, so in the function above, each `return` statement is equivalent to

```go
return words, images, err
```

In functions like this one, with many `return` statements and several results, bare returns can reduce code duplication, but they rarely make code easier to understand. For instance, it’s not obvious at first glance that the two early returns are equivalent to `return 0, 0, err` (because the result variables `words` and `images` are initialized to their zero values) and that the final `return` is equivalent to `return words, images, nil`. For this reason, bare returns are best used sparingly.

**Exercise 5.5:** Implement `countWordsAndImages`. (See [Exercise 4.9](#part0038.html#id-ex-wordfreq) for word-splitting.)

**Exercise 5.6:** Modify the `corner` function in `gopl.io/ch3/surface` ([§3.2](#part0030.html#id-surface)) to use named results and a bare `return` statement.

## 5.4 Errors

Some functions always succeed at their task. For example, `strings.Contains` and `strconv.FormatBool` have well-defined results for all possible argument values and cannot fail—barring catastrophic and unpredictable scenarios like running out of memory, where the symptom is far from the cause and from which there’s little hope of recovery.

Other functions always succeed so long as their preconditions are met. For example, the `time.Date` function always constructs a `time.Time` from its components—year, month, and so on—unless the last argument (the time zone) is `nil`, in which case it panics. This panic is a sure sign of a bug in the calling code and should never happen in a well-written program.

For many other functions, even in a well-written program, success is not assured because it depends on factors beyond the programmer’s control. Any function that does I/O, for example, must confront the possibility of error, and only a naïve programmer believes a simple read or write cannot fail. Indeed, it’s when the most reliable operations fail unexpectedly that we most need to know why.

Errors are thus an important part of a package’s API or an application’s user interface, and failure is just one of several expected behaviors. This is the approach Go takes to error handling.

A function for which failure is an expected behavior returns an additional result, conventionally the last one. If the failure has only one possible cause, the result is a boolean, usually called `ok`, as in this example of a cache lookup that always succeeds unless there was no entry for that key:

[Click here to view code image](#part0135_split_016.html#id128pro01_r)

```go
value, ok := cache.Lookup(key)
if !ok {
    // ...cache[key] does not exist...
}
```

More often, and especially for I/O, the failure may have a variety of causes for which the caller will need an explanation. In such cases, the type of the additional result is `error`.

The built-in type `error` is an interface type. We’ll see more of what this means and its implications for error handling in [Chapter 7](#part0068.html#id-theerrorinterface). For now it’s enough to know that an `error` may be `nil` or non-`nil`, that `nil` implies success and non-`nil` implies failure, and that a non-`nil` `error` has an error message string which we can obtain by calling its `Error()` method or print by calling `fmt.Println(err)` or `fmt.Printf("%v", err)`.

Usually when a function returns a non-`nil` error, its other results are undefined and should be ignored. However, a few functions may return partial results in error cases. For example, if an error occurs while reading from a file, a call to `Read` returns the number of bytes it was able to read *and* an `error` value describing the problem. For correct behavior, some callers may need to process the incomplete data before handling the error, so it is important that such functions clearly document their results.

Go’s approach sets it apart from many other languages in which failures are reported using *exceptions*, not ordinary values. Although Go does have an exception mechanism of sorts, as we will see in [Section 5.9](#part0051.html#id-panic), it is used only for reporting truly unexpected errors that indicate a bug, not the routine errors that a robust program should be built to expect.

The reason for this design is that exceptions tend to entangle the description of an error with the control flow required to handle it, often leading to an undesirable outcome: routine errors are reported to the end user in the form of an incomprehensible stack trace, full of information about the structure of the program but lacking intelligible context about what went wrong.

By contrast, Go programs use ordinary control-flow mechanisms like `if` and `return` to respond to errors. This style undeniably demands that more attention be paid to error-handling logic, but that is precisely the point.

### 5.4.1 Error-Handling Strategies

When a function call returns an error, it’s the caller’s responsibility to check it and take appropriate action. Depending on the situation, there may be a number of possibilities. Let’s take a look at five of them.

First, and most common, is to *propagate* the error, so that a failure in a subroutine becomes a failure of the calling routine. We saw examples of this in the `findLinks` function of [Section 5.3](#part0045.html#id-multiplereturnvalues). If the call to `http.Get` fails, `findLinks` returns the HTTP error to the caller without further ado:

```go
resp, err := http.Get(url)
if err != nil {
    return nil, err
}
```

In contrast, if the call to `html.Parse` fails, `findLinks` does not return the HTML parser’s error directly because it lacks two crucial pieces of information: that the error occurred in the parser, and the URL of the document that was being parsed. In this case, `findLinks` constructs a new error message that includes both pieces of information as well as the underlying parse error:

[Click here to view code image](#part0135_split_017.html#id129pro01_r)

```go
doc, err := html.Parse(resp.Body)
resp.Body.Close()
if err != nil {
    return nil, fmt.Errorf("parsing %s as HTML: %v", url, err)
}
```

The `fmt.Errorf` function formats an error message using `fmt.Sprintf` and returns a new `error` value. We use it to build descriptive errors by successively prefixing additional context information to the original error message. When the error is ultimately handled by the program’s `main` function, it should provide a clear causal chain from the root problem to the overall failure, reminiscent of a NASA accident investigation:

[Click here to view code image](#part0135_split_018.html#id129pro02_r)

```
genesis: crashed: no parachute: G-switch failed: bad relay orientation
```

Because error messages are frequently chained together, message strings should not be capitalized and newlines should be avoided. The resulting errors may be long, but they will be self-contained when found by tools like `grep`.

When designing error messages, be deliberate, so that each one is a meaningful description of the problem with sufficient and relevant detail, and be consistent, so that errors returned by the same function or by a group of functions in the same package are similar in form and can be dealt with in the same way.
