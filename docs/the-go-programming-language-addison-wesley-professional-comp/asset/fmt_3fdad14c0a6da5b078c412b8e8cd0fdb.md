
# 7.1 ByteCounter 示例

Let’s test this out using a new type. The `Write` method of the `*ByteCounter` type below merely counts the bytes written to it before discarding them. (The conversion is required to make the types of `len(p)` and `*c` match in the `+=` assignment statement.)

[Click here to view code image](#part0137_split_002.html#id173pro01_r)

gopl.io/ch7/bytecounter

```
type ByteCounter int

func (c *ByteCounter) Write(p []byte) (int, error) {
    *c += ByteCounter(len(p)) // convert int to ByteCounter
    return len(p), nil
}
```

Since `*ByteCounter` satisfies the `io.Writer` contract, we can pass it to `Fprintf`, which does its string formatting oblivious to this change; the `ByteCounter` correctly accumulates the length of the result.

[Click here to view code image](#part0137_split_003.html#id173pro02_r)

```
var c ByteCounter
c.Write([]byte("hello"))
fmt.Println(c) // "5", = len("hello")

c = 0 // reset the counter
var name = "Dolly"
fmt.Fprintf(&c, "hello, %s", name)
fmt.Println(c) // "12", = len("hello, Dolly")
```

Besides `io.Writer`, there is another interface of great importance to the `fmt` package. `Fprintf` and `Fprintln` provide a way for types to control how their values are printed. In [Section 2.5](#part0025.html#id-typedeclarations), we defined a `String` method for the `Celsius` type so that temperatures would print as `"100°C"`, and in [Section 6.5](#part0058.html#id-intset) we equipped `*IntSet` with a `String` method so that sets would be rendered using traditional set notation like `"{1 2 3}"`. Declaring a `String` method makes a type satisfy one of the most widely used interfaces of all, `fmt.Stringer`:

[Click here to view code image](#part0137_split_004.html#id173pro03_r)

```
package fmt

// The String method is used to print values passed
// as an operand to any format that accepts a string
// or to an unformatted printer such as Print.
type Stringer interface {
    String() string
}
```

We’ll explain how the `fmt` package discovers which values satisfy this interface in [Section 7.10](#part0070.html#id-typeassertions).

**Exercise 7.1:** Using the ideas from `ByteCounter`, implement counters for words and for lines. You will find `bufio.ScanWords` useful.

**Exercise 7.2:** Write a function `CountingWriter` with the signature below that, given an `io.Writer`, returns a new `Writer` that wraps the original, and a pointer to an `int64` variable that at any moment contains the number of bytes written to the new `Writer`.

[Click here to view code image](#part0137_split_005.html#id174pro01_r)

```
func CountingWriter(w io.Writer) (io.Writer, *int64)
```

**Exercise 7.3:** Write a `String` method for the `*tree` type in `gopl.io/ch4/treesort` ([§4.4](#part0039.html#id-structs)) that reveals the sequence of values in the tree.

## 7.2 Interface Types

An interface type specifies a set of methods that a concrete type must possess to be considered an instance of that interface.

The `io.Writer` type is one of the most widely used interfaces because it provides an abstraction of all the types to which bytes can be written, which includes files, memory buffers, network connections, HTTP clients, archivers, hashers, and so on. The `io` package defines many other useful interfaces. A `Reader` represents any type from which you can read bytes, and a `Closer` is any value that you can close, such as a file or a network connection. (By now you’ve probably noticed the naming convention for many of Go’s single-method interfaces.)

[Click here to view code image](#part0137_split_006.html#id174pro02_r)

```
package io

type Reader interface {
    Read(p []byte) (n int, err error)
}

type Closer interface {
    Close() error
}
```

Looking farther, we find declarations of new interface types as combinations of existing ones. Here are two examples:

[Click here to view code image](#part0137_split_007.html#id174pro03_r)

```
type ReadWriter interface {
    Reader
    Writer
}

type ReadWriteCloser interface {
    Reader
    Writer
    Closer
}
```

The syntax used above, which resembles struct embedding, lets us name another interface as a shorthand for writing out all of its methods. This is called *embedding* an interface. We could have written `io.ReadWriter` without embedding, albeit less succinctly, like this:

[Click here to view code image](#part0137_split_008.html#id175pro01_r)

```
type ReadWriter interface {
    Read(p []byte) (n int, err error)
    Write(p []byte) (n int, err error)
}
```

or even using a mixture of the two styles:

[Click here to view code image](#part0137_split_009.html#id175pro02_r)

```
type ReadWriter interface {
    Read(p []byte) (n int, err error)
    Writer
}
```

All three declarations have the same effect. The order in which the methods appear is immaterial. All that matters is the set of methods.

**Exercise 7.4:** The `strings.NewReader` function returns a value that satisfies the `io.Reader` interface (and others) by reading from its argument, a string. Implement a simple version of `NewReader` yourself, and use it to make the HTML parser ([§5.2](#part0044.html#id-recursion)) take input from a string.

**Exercise 7.5:** The `LimitReader` function in the `io` package accepts an `io.Reader` `r` and a number of bytes `n`, and returns another `Reader` that reads from `r` but reports an end-of-file condition after `n` bytes. Implement it.

[Click here to view code image](#part0137_split_010.html#id175pro03_r)

```
func LimitReader(r io.Reader, n int64) io.Reader
```

## 7.3 Interface Satisfaction

A type *satisfies* an interface if it possesses all the methods the interface requires. For example, an `*os.File` satisfies `io.Reader`, `Writer`, `Closer`, and `ReadWriter`. A `*bytes.Buffer` satisfies `Reader`, `Writer`, and `ReadWriter`, but does not satisfy `Closer` because it does not have a `Close` method. As a shorthand, Go programmers often say that a concrete type “is a” particular interface type, meaning that it satisfies the interface. For example, a `*bytes.Buffer` is an `io.Writer`; an `*os.File` is an `io.ReadWriter`.

The assignability rule ([§2.4.2](#part0024.html#id-assignability)) for interfaces is very simple: an expression may be assigned to an interface only if its type satisfies the interface. So:

[Click here to view code image](#part0137_split_011.html#id175pro04_r)

```
var w io.Writer
w = os.Stdout           // OK: *os.File has Write method
w = new(bytes.Buffer)   // OK: *bytes.Buffer has Write method
w = time.Second         // compile error: time.Duration lacks Write method

var rwc io.ReadWriteCloser
rwc = os.Stdout         // OK: *os.File has Read, Write, Close methods
rwc = new(bytes.Buffer) // compile error: *bytes.Buffer lacks Close method
```

This rule applies even when the right-hand side is itself an interface:

[Click here to view code image](#part0137_split_012.html#id175pro05_r)

```
w = rwc                 // OK: io.ReadWriteCloser has Write method
rwc = w                 // compile error: io.Writer lacks Close method
```

Because `ReadWriter` and `ReadWriteCloser` include all the methods of `Writer`, any type that satisfies `ReadWriter` or `ReadWriteCloser` necessarily satisfies `Writer`.

Before we go further, we should explain one subtlety in what it means for a type to have a method. Recall from [Section 6.2](#part0055.html#id-methodswithapointerreceiver) that for each named concrete type `T`, some of its methods have a receiver of type `T` itself whereas others require a `*T` pointer. Recall also that it is legal to call a `*T` method on an argument of type `T` so long as the argument is a *variable*; the compiler implicitly takes its address. But this is mere syntactic sugar: a value of type `T` does not possess all the methods that a `*T` pointer does, and as a result it might satisfy fewer interfaces.
