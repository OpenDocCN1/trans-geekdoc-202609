
Since in an end-of-file condition there is no information to report besides the fact of it, `io.EOF` has a fixed error message, `"EOF"`. For other errors, we may need to report both the quality and quantity of the error, so to speak, so a fixed error value will not do. In [Section 7.11](#ebook_split_070.html#id-discriminatingerrors), we’ll present a more systematic way to distinguish certain error values from others.

## 5.5 Function Values

Functions are *first-class values* in Go: like other values, function values have types, and they may be assigned to variables or passed to or returned from functions. A function value may be called like any other function. For example:

[Click here to view code image](#ch05_images.html#id132pro03_r)

```
func square(n int) int     { return n * n }
func negative(n int) int   { return -n }
func product(m, n int) int { return m * n }

f := square
fmt.Println(f(3)) // "9"

f = negative
fmt.Println(f(3))     // "-3"
fmt.Printf("%T\n", f) // "func(int) int"

f = product // compile error: can't assign f(int, int) int to f(int) int
```

The zero value of a function type is `nil`. Calling a nil function value causes a panic:

[Click here to view code image](#ch05_images.html#id132pro04_r)

```
var f func(int) int
f(3) // panic: call of nil function
```

Function values may be compared with `nil`:

```
var f func(int) int
if f != nil {
    f(3)
}
```

but they are not comparable, so they may not be compared against each other or used as keys in a map.

Function values let us parameterize our functions over not just data, but behavior too. The standard libraries contain many examples. For instance, `strings.Map` applies a function to each character of a string, joining the results to make another string.

[Click here to view code image](#ch05_images.html#id133pro01_r)

```
func add1(r rune) rune { return r + 1 }

fmt.Println(strings.Map(add1, "HAL-9000")) // "IBM.:111"
fmt.Println(strings.Map(add1, "VMS"))      // "WNT"

fmt.Println(strings.Map(add1, "Admix"))    // "Benjy"
```

The `findLinks` function from [Section 5.2](#ebook_split_043.html#id-recursion) uses a helper function, `visit`, to visit all the nodes in an HTML document and apply an action to each one. Using a function value, we can separate the logic for tree traversal from the logic for the action to be applied to each node, letting us reuse the traversal with different actions.

[Click here to view code image](#ch05_images.html#id133pro02_r)

gopl.io/ch5/outline2

```
// forEachNode calls the functions pre(x) and post(x) for each node
// x in the tree rooted at n. Both functions are optional.
// pre is called before the children are visited (preorder) and
// post is called after (postorder).
func forEachNode(n *html.Node, pre, post func(n *html.Node)) {
    if pre != nil {
        pre(n)
    }

    for c := n.FirstChild; c != nil; c = c.NextSibling {
        forEachNode(c, pre, post)
    }

    if post != nil {
        post(n)
    }
}
```

The `forEachNode` function accepts two function arguments, one to call before a node’s children are visited and one to call after. This arrangement gives the caller a great deal of flexibility. For example, the functions `startElement` and `endElement` print the start and end tags of an HTML element like `<b>...</b>`:

[Click here to view code image](#ch05_images.html#id133pro03_r)

```
var depth int

func startElement(n *html.Node) {
    if n.Type == html.ElementNode {
        fmt.Printf("%*s<%s>\n", depth*2, "", n.Data)
        depth++
    }
}

func endElement(n *html.Node) {
    if n.Type == html.ElementNode {
        depth--
        fmt.Printf("%*s</%s>\n", depth*2, "", n.Data)
    }
}
```

The functions also indent the output using another `fmt.Printf` trick. The `*` adverb in `%*s` prints a string padded with a variable number of spaces. The width and the string are provided by the arguments `depth*2` and `""`.

If we call `forEachNode` on an HTML document, like this:

[Click here to view code image](#ch05_images.html#id134pro01_r)

```
forEachNode(doc, startElement, endElement)
```

we get a more elaborate variation on the output of our earlier `outline` program:

[Click here to view code image](#ch05_images.html#id134pro02_r)

```
$ go build gopl.io/ch5/outline2
$ ./outline2 http://gopl.io
<html>
  <head>
    <meta>
    </meta>
    <title>
    </title>
    <style>
    </style>
  </head>
  <body>
    <table>
      <tbody>
        <tr>
          <td>
            <a>
              <img>
              </img>
...
```

**Exercise 5.7:** Develop `startElement` and `endElement` into a general HTML pretty-printer. Print comment nodes, text nodes, and the attributes of each element (`<a href='...'>`). Use short forms like `<img/>` instead of `<img></img>` when an element has no children. Write a test to ensure that the output can be parsed successfully. (See [Chapter 11](#ebook_split_103.html#id-testing).)

**Exercise 5.8:** Modify `forEachNode` so that the `pre` and `post` functions return a boolean result indicating whether to continue the traversal. Use it to write a function `ElementByID` with the following signature that finds the first HTML element with the specified `id` attribute. The function should stop the traversal as soon as a match is found.

[Click here to view code image](#ch05_images.html#id135pro01_r)

```
func ElementByID(doc *html.Node, id string) *html.Node
```

**Exercise 5.9:** Write a function `expand(s string, f func(string) string) string` that replaces each substring “`$foo`” within `s` by the text returned by `f("foo")`.

## 5.6 Anonymous Functions

Named functions can be declared only at the package level, but we can use a *function literal* to denote a function value within any expression. A function literal is written like a function declaration, but without a name following the `func` keyword. It is an expression, and its value is called an *anonymous function*.

Function literals let us define a function at its point of use. As an example, the earlier call to `strings.Map` can be rewritten as

[Click here to view code image](#ch05_images.html#id135pro02_r)

```
strings.Map(func(r rune) rune { return r + 1 }, "HAL-9000")
```

More importantly, functions defined in this way have access to the entire lexical environment, so the inner function can refer to variables from the enclosing function, as this example shows:

[Click here to view code image](#ch05_images.html#id135pro03_r)

gopl.io/ch5/squares

```
// squares returns a function that returns
// the next square number each time it is called.
func squares() func() int {
    var x int
    return func() int {
        x++
        return x * x
    }
}

func main() {
    f := squares()
    fmt.Println(f()) // "1"
    fmt.Println(f()) // "4"
    fmt.Println(f()) // "9"
    fmt.Println(f()) // "16"
}
```

The function `squares` returns another function, of type `func() int`. A call to `squares` creates a local variable `x` and returns an anonymous function that, each time it is called, increments `x` and returns its square. A second call to `squares` would create a second variable `x` and return a new anonymous function which increments that variable.

The `squares` example demonstrates that function values are not just code but can have state. The anonymous inner function can access and update the local variables of the enclosing function `squares`. These hidden variable references are why we classify functions as reference types and why function values are not comparable. Function values like these are implemented using a technique called *closures*, and Go programmers often use this term for function values.

Here again we see an example where the lifetime of a variable is not determined by its scope: the variable `x` exists after `squares` has returned within `main`, even though `x` is hidden inside `f`.
