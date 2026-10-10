
## Exercise 5.17

Write a variadic function `ElementsByTagName` that, given an HTML node tree and zero or more names, returns all the elements that match one of those names. Here are two example calls:

[Click here to view code image](#ch05_images.html#id143pro03_r)

```
func ElementsByTagName(doc *html.Node, name ...string) []*html.Node

images := ElementsByTagName(doc, "img")
headings := ElementsByTagName(doc, "h1", "h2", "h3", "h4")
```

## 5.8 Deferred Function Calls

Our `findLinks` examples used the output of `http.Get` as the input to `html.Parse`. This works well if the content of the requested URL is indeed HTML, but many pages contain images, plain text, and other file formats. Feeding such files into an HTML parser could have undesirable effects.

The program below fetches an HTML document and prints its title. The `title` function inspects the `Content-Type` header of the server’s response and returns an error if the document is not HTML.

[Click here to view code image](#ch05_images.html#id144pro01_r)

gopl.io/ch5/title1

```
func title(url string) error {
    resp, err := http.Get(url)
    if err != nil {
        return err
    }

    // Check Content-Type is HTML (e.g., "text/html; charset=utf-8").
    ct := resp.Header.Get("Content-Type")
    if ct != "text/html" && !strings.HasPrefix(ct, "text/html;") {
        resp.Body.Close()
        return fmt.Errorf("%s has type %s, not text/html", url, ct)
    }

    doc, err := html.Parse(resp.Body)
    resp.Body.Close()
    if err != nil {
        return fmt.Errorf("parsing %s as HTML: %v", url, err)
    }

    visitNode := func(n *html.Node) {
        if n.Type == html.ElementNode && n.Data == "title" &&
            n.FirstChild != nil {
            fmt.Println(n.FirstChild.Data)
        }
    }
    forEachNode(doc, visitNode, nil)
    return nil
}
```

Here’s a typical session, slightly edited to fit:

[Click here to view code image](#ch05_images.html#id144pro02_r)

```
$ go build gopl.io/ch5/title1
$ ./title1 http://gopl.io
The Go Programming Language
$ ./title1 https://golang.org/doc/effective_go.html
Effective Go - The Go Programming Language
$ ./title1 https://golang.org/doc/gopher/frontpage.png
title: https://golang.org/doc/gopher/frontpage.png
    has type image/png, not text/html
```

Observe the duplicated `resp.Body.Close()` call, which ensures that `title` closes the network connection on all execution paths, including failures. As functions grow more complex and have to handle more errors, such duplication of clean-up logic may become a maintenance problem. Let’s see how Go’s novel `defer` mechanism makes things simpler.

Syntactically, a `defer` statement is an ordinary function or method call prefixed by the keyword `defer`. The function and argument expressions are evaluated when the statement is executed, but the actual call is *deferred* until the function that contains the `defer` statement has finished, whether normally, by executing a return statement or falling off the end, or abnormally, by panicking. Any number of calls may be deferred; they are executed in the reverse of the order in which they were deferred.

A `defer` statement is often used with paired operations like open and close, connect and disconnect, or lock and unlock to ensure that resources are released in all cases, no matter how complex the control flow. The right place for a `defer` statement that releases a resource is immediately after the resource has been successfully acquired. In the `title` function below, a single deferred call replaces both previous calls to `resp.Body.Close()`:

[Click here to view code image](#ch05_images.html#id145pro01_r)

gopl.io/ch5/title2

```
func title(url string) error {
    resp, err := http.Get(url)
    if err != nil {
        return err
    }
    defer resp.Body.Close()

    ct := resp.Header.Get("Content-Type")
    if ct != "text/html" && !strings.HasPrefix(ct, "text/html;") {
        return fmt.Errorf("%s has type %s, not text/html", url, ct)
    }

    doc, err := html.Parse(resp.Body)
    if err != nil {
        return fmt.Errorf("parsing %s as HTML: %v", url, err)
    }

    // ...print doc's title element...

    return nil
}
```

The same pattern can be used for other resources beside network connections, for instance to close an open file:

[Click here to view code image](#ch05_images.html#id145pro02_r)

io/ioutil

```
package ioutil

func ReadFile(filename string) ([]byte, error) {
    f, err := os.Open(filename)
    if err != nil {
        return nil, err
    }
    defer f.Close()
    return ReadAll(f)
}
```

or to unlock a mutex ([§9.2](#ebook_split_088.html#id-mutex)):

```
var mu sync.Mutex
var m = make(map[string]int)

func lookup(key string) int {
    mu.Lock()
    defer mu.Unlock()
    return m[key]
}
```

The `defer` statement can also be used to pair “on entry” and “on exit” actions when debugging a complex function. The `bigSlowOperation` function below calls `trace` immediately, which does the “on entry” action then returns a function value that, when called, does the corresponding “on exit” action. By deferring a call to the returned function in this way, we can instrument the entry point and all exit points of a function in a single statement and even pass values, like the `start` time, between the two actions. But don’t forget the final parentheses in the `defer` statement, or the “on entry” action will happen on exit and the on-exit action won’t happen at all!

[Click here to view code image](#ch05_images.html#id146pro01_r)

gopl.io/ch5/trace

```
func bigSlowOperation() {
    defer trace("bigSlowOperation")() // don't forget the extra parentheses
    // ...lots of work...
    time.Sleep(10 * time.Second) // simulate slow operation by sleeping
}

func trace(msg string) func() {
    start := time.Now()
    log.Printf("enter %s", msg)
    return func() { log.Printf("exit %s (%s)", msg, time.Since(start)) }
}
```

Each time `bigSlowOperation` is called, it logs its entry and exit and the elapsed time between them. (We used `time.Sleep` to simulate a slow operation.)

[Click here to view code image](#ch05_images.html#id146pro02_r)

```
$ go build gopl.io/ch5/trace
$ ./trace
2015/11/18 09:53:26 enter bigSlowOperation
2015/11/18 09:53:36 exit bigSlowOperation (10.000589217s)
```

Deferred functions run *after* return statements have updated the function’s result variables. Because an anonymous function can access its enclosing function’s variables, including named results, a deferred anonymous function can observe the function’s results.

Consider the function `double`:

[Click here to view code image](#ch05_images.html#id147pro01_r)

```
func double(x int) int {
    return x + x
}
```

By naming its result variable and adding a `defer` statement, we can make the function print its arguments and results each time it is called.

[Click here to view code image](#ch05_images.html#id147pro02_r)

```
func double(x int) (result int) {
    defer func() { fmt.Printf("double(%d) = %d\n", x, result) }()
    return x + x
}

_ = double(4)
// Output:
// "double(4) = 8"
```

This trick is overkill for a function as simple as `double` but may be useful in functions with many return statements.

A deferred anonymous function can even change the values that the enclosing function returns to its caller:

```
func triple(x int) (result int) {
    defer func() { result += x }()
    return double(x)
}

fmt.Println(triple(4)) // "12"
```

Because deferred functions aren’t executed until the very end of a function’s execution, a `defer` statement in a loop deserves extra scrutiny. The code below could run out of file descriptors since no file will be closed until all files have been processed:

[Click here to view code image](#ch05_images.html#id147pro03_r)
