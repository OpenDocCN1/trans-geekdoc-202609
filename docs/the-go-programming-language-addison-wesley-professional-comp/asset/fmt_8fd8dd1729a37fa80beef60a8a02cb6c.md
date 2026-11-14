
## The `unicode` Package

The `unicode` package provides functions like `IsDigit`, `IsLetter`, `IsUpper`, and `IsLower` for classifying runes. Each function takes a single rune argument and returns a boolean. Conversion functions like `ToUpper` and `ToLower` convert a rune into the given case if it is a letter. All these functions use the Unicode standard categories for letters, digits, and so on.

## The `strings` Package

The `strings` package has similar functions, also called `ToUpper` and `ToLower`, that return a new string with the specified transformation applied to each character of the original string.

## The `basename` Function

The `basename` function below was inspired by the Unix shell utility of the same name. In our version, `basename(s)` removes any prefix of `s` that looks like a file system path with components separated by slashes, and it removes any suffix that looks like a file type:

```
fmt.Println(basename("a/b/c.go")) // "c"
fmt.Println(basename("c.d.go"))   // "c.d"
fmt.Println(basename("abc"))      // "abc"
```

### First Version (Without Libraries)

The first version of `basename` does all the work without the help of libraries:

```
gopl.io/ch3/basename1
```

```
// basename removes directory components and a .suffix.
// e.g., a => a, a.go => a, a/b/c.go => c, a/b.c.go => b.c
func basename(s string) string {
    // Discard last '/' and everything before.
    for i := len(s) - 1; i >= 0; i-- {
        if s[i] == '/' {
            s = s[i+1:]
            break
        }
    }
    // Preserve everything before last '.'.
    for i := len(s) - 1; i >= 0; i-- {
        if s[i] == '.' {
            s = s[:i]
            break
        }
    }
    return s
}
```

### Second Version (Using `strings.LastIndex`)

A simpler version uses the `strings.LastIndex` library function:

```
gopl.io/ch3/basename2
```

```
func basename(s string) string {
    slash := strings.LastIndex(s, "/") // -1 if "/" not found
    s = s[slash+1:]
    if dot := strings.LastIndex(s, "."); dot >= 0 {
        s = s[:dot]
    }
    return s
}
```

## The `path` and `path/filepath` Packages

The `path` and `path/filepath` packages provide a more general set of functions for manipulating hierarchical names. The `path` package works with slash-delimited paths on any platform. It shouldn't be used for file names, but it is appropriate for other domains, like the path component of a URL. By contrast, `path/filepath` manipulates file names using the rules for the host platform, such as `/foo/bar` for POSIX or `c:\foo\bar` on Microsoft Windows.

## The `comma` Function

Let's continue with another substring example. The task is to take a string representation of an integer, such as `"12345"`, and insert commas every three places, as in `"12,345"`. This version only works for integers; handling floating-point numbers is left as an exercise.

```
gopl.io/ch3/comma
```

```
// comma inserts commas in a non-negative decimal integer string.
func comma(s string) string {
    n := len(s)
    if n <= 3 {
        return s
    }
    return comma(s[:n-3]) + "," + s[n-3:]
}
```

The argument to `comma` is a string. If its length is less than or equal to 3, no comma is necessary. Otherwise, `comma` calls itself recursively with a substring consisting of all but the last three characters, and appends a comma and the last three characters to the result of the recursive call.

## Conversions Between Strings and Byte Slices

A string contains an array of bytes that, once created, is immutable. By contrast, the elements of a byte slice can be freely modified.

Strings can be converted to byte slices and back again:

```
s := "abc"
b := []byte(s)
s2 := string(b)
```

Conceptually, the `[]byte(s)` conversion allocates a new byte array holding a copy of the bytes of `s`, and yields a slice that references the entirety of that array. An optimizing compiler may be able to avoid the allocation and copying in some cases, but in general copying is required to ensure that the bytes of `s` remain unchanged even if those of `b` are subsequently modified. The conversion from byte slice back to string with `string(b)` also makes a copy, to ensure immutability of the resulting string `s2`.

## The `bytes` Package and `Buffer` Type

To avoid conversions and unnecessary memory allocation, many of the utility functions in the `bytes` package directly parallel their counterparts in the `strings` package. For example, here are half a dozen functions from `strings`:

```
func Contains(s, substr string) bool
func Count(s, sep string) int
func Fields(s string) []string
func HasPrefix(s, prefix string) bool
func Index(s, sep string) int
func Join(a []string, sep string) string
```

and the corresponding ones from `bytes`:

```
func Contains(b, subslice []byte) bool
func Count(s, sep []byte) int
func Fields(s []byte) [][]byte
func HasPrefix(s, prefix []byte) bool
func Index(s, sep []byte) int
func Join(s [][]byte, sep []byte) []byte
```

The only difference is that strings have been replaced by byte slices.

The `bytes` package provides the `Buffer` type for efficient manipulation of byte slices. A `Buffer` starts out empty but grows as data of types like `string`, `byte`, and `[]byte` are written to it. As the example below shows, a `bytes.Buffer` variable requires no initialization because its zero value is usable:

```
gopl.io/ch3/printints
```

```
// intsToString is like fmt.Sprint(values) but adds commas.
func intsToString(values []int) string {
    var buf bytes.Buffer
    buf.WriteByte('[')
    for i, v := range values {
        if i > 0 {
            buf.WriteString(", ")
        }
        fmt.Fprintf(&buf, "%d", v)
    }
    buf.WriteByte(']')
    return buf.String()
}

func main() {
    fmt.Println(intsToString([]int{1, 2, 3})) // "[1, 2, 3]"
}
```

When appending the UTF-8 encoding of an arbitrary rune to a `bytes.Buffer`, it's best to use `bytes.Buffer`'s `WriteRune` method, but `WriteByte` is fine for ASCII characters such as `'['` and `']'`.

The `bytes.Buffer` type is extremely versatile, and when we discuss interfaces in Chapter 7, we'll see how it may be used as a replacement for a file whenever an I/O function requires a sink for bytes (`io.Writer`) as `Fprintf` does above, or a source of bytes (`io.Reader`).

## Exercises

**Exercise 3.10:** Write a non-recursive version of `comma`, using `bytes.Buffer` instead of string concatenation.

**Exercise 3.11:** Enhance `comma` so that it deals correctly with floating-point numbers and an optional sign.

**Exercise 3.12:** Write a function that reports whether two strings are anagrams of each other, that is, they contain the same letters in a different order.

## 3.5.5 Conversions Between Strings and Numbers

In addition to conversions between strings, runes, and bytes, it's often necessary to convert between numeric values and their string representations. This is done with functions from the `strconv` package.

To convert an integer to a string, one option is to use `fmt.Sprintf`; another is to use the function `strconv.Itoa` ("integer to ASCII"):

```
x := 123
y := fmt.Sprintf("%d", x)
fmt.Println(y, strconv.Itoa(x)) // "123 123"
```

`FormatInt` and `FormatUint` can be used to format numbers in a different base:

```
fmt.Println(strconv.FormatInt(int64(x), 2)) // "1111011"
```

The `fmt.Printf` verbs `%b`, `%d`, `%u`, and `%x` are often more convenient than `Format` functions, especially if we want to include additional information besides the number:

```
s := fmt.Sprintf("x=%b", x) // "x=1111011"
```
