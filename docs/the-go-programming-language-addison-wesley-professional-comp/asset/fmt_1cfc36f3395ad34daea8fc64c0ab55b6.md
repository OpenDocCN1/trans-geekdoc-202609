
## 3.5 Strings and UTF-8

Go source files are always encoded in UTF-8, and UTF-8 is the preferred encoding for text strings manipulated by Go programs. The `unicode` package provides functions for working with individual runes (such as distinguishing letters from numbers, or converting an upper-case letter to a lower-case one), and the `unicode/utf8` package provides functions for encoding and decoding runes as bytes using UTF-8.

### 3.5.1 Unicode Escapes

Many Unicode characters are hard to type on a keyboard or to distinguish visually from similar-looking ones; some are even invisible. Unicode escapes in Go string literals allow us to specify them by their numeric code point value. There are two forms: `\u`*hhhh* for a 16-bit value and `\U`*hhhhhhhh* for a 32-bit value, where each *h* is a hexadecimal digit; the need for the 32-bit form arises very infrequently. Each denotes the UTF-8 encoding of the specified code point. Thus, for example, the following string literals all represent the same six-byte string:

```
""
"\xe4\xb8\x96\xe7\x95\x8c"
"\u4e16\u754c"
"\U00004e16\U0000754c"
```

The three escape sequences above provide alternative notations for the first string, but the values they denote are identical.

Unicode escapes may also be used in rune literals. These three literals are equivalent:

```
''  '\u4e16'  '\U00004e16'
```

A rune whose value is less than 256 may be written with a single hexadecimal escape, such as `'\x41'` for `'A'`, but for higher values, a `\u` or `\U` escape must be used. Consequently, `'\xe4\xb8\x96'` is not a legal rune literal, even though those three bytes are a valid UTF-8 encoding of a single code point.

### 3.5.2 String Operations

Thanks to the nice properties of UTF-8, many string operations don't require decoding. We can test whether one string contains another as a prefix:

[Click here to view code image](#part0132_split_034.html#id069pro01_01_r)

```
func HasPrefix(s, prefix string) bool {
    return len(s) >= len(prefix) && s[:len(prefix)] == prefix
}
```

or as a suffix:

[Click here to view code image](#part0132_split_035.html#id069pro01_02_r)

```
func HasSuffix(s, suffix string) bool {
    return len(s) >= len(suffix) && s[len(s)-len(suffix):] == suffix
}
```

or as a substring:

[Click here to view code image](#part0132_split_036.html#id069pro01_03_r)

```
func Contains(s, substr string) bool {
    for i := 0; i < len(s); i++ {
        if HasPrefix(s[i:], substr) {
            return true
        }
    }
    return false
}
```

using the same logic for UTF-8-encoded text as for raw bytes. This is not true for other encodings. (The functions above are drawn from the `strings` package, though its implementation of `Contains` uses a hashing technique to search more efficiently.)

### 3.5.3 Processing Unicode Characters

On the other hand, if we really care about the individual Unicode characters, we have to use other mechanisms. Consider the string from our very first example, which includes two East Asian characters. [Figure 3.5](#part0033.html#id-figures-stringutf8) illustrates its representation in memory. The string contains 13 bytes, but interpreted as UTF-8, it encodes only nine code points or runes:

![A range loop decodes a UTF-8-encoded string.](`images/00013.jpeg`)

**Figure 3.5.** A `range` loop decodes a UTF-8-encoded string.

[Click here to view code image](#part0132_split_037.html#id069pro02_r)

```
import "unicode/utf8"

s := "Hello, "
fmt.Println(len(s))                    // "13"
fmt.Println(utf8.RuneCountInString(s)) // "9"
```

To process those characters, we need a UTF-8 decoder. The `unicode/utf8` package provides one that we can use like this:

[Click here to view code image](#part0132_split_038.html#id069pro03_r)

```
for i := 0; i < len(s); {
    r, size := utf8.DecodeRuneInString(s[i:])
    fmt.Printf("%d\t%c\n", i, r)
    i += size
}
```

Each call to `DecodeRuneInString` returns `r`, the rune itself, and `size`, the number of bytes occupied by the UTF-8 encoding of `r`. The size is used to update the byte index `i` of the next rune in the string. But this is clumsy, and we need loops of this kind all the time. Fortunately, Go's `range` loop, when applied to a string, performs UTF-8 decoding implicitly. The output of the loop below is also shown in [Figure 3.5](#part0033.html#id-figures-stringutf8); notice how the index jumps by more than 1 for each non-ASCII rune.

[Click here to view code image](#part0132_split_039.html#id070pro01_r)

```
for i, r := range "Hello, " {
    fmt.Printf("%d\t%q\t%d\n", i, r, r)
}
```

We could use a simple `range` loop to count the number of runes in a string, like this:

```
n := 0
for _, _ = range s {
    n++
}
```

As with the other forms of `range` loop, we can omit the variables we don't need:

```
n := 0
for range s {
    n++
}
```

Or we can just call `utf8.RuneCountInString(s)`.

We mentioned earlier that it is mostly a matter of convention in Go that text strings are interpreted as UTF-8-encoded sequences of Unicode code points, but for correct use of `range` loops on strings, it's more than a convention, it's a necessity. What happens if we range over a string containing arbitrary binary data or, for that matter, UTF-8 data containing errors?

Each time a UTF-8 decoder, whether explicit in a call to `utf8.DecodeRuneInString` or implicit in a `range` loop, consumes an unexpected input byte, it generates a special Unicode *replacement character*, `'\uFFFD'`, which is usually printed as a white question mark inside a black hexagonal or diamond-like shape ![Image](`images/00014.jpeg`). When a program encounters this rune value, it's often a sign that some upstream part of the system that generated the string data has been careless in its treatment of text encodings.

UTF-8 is exceptionally convenient as an interchange format but within a program runes may be more convenient because they are of uniform size and are thus easily indexed in arrays and slices.

A `[]rune` conversion applied to a UTF-8-encoded string returns the sequence of Unicode code points that the string encodes:

[Click here to view code image](#part0132_split_040.html#id071pro01_r)

```
// "program" in Japanese katakana
s := ""
fmt.Printf("% x\n", s) // "e3 83 97 e3 83 ad e3 82 b0 e3 83 a9 e3 83 a0"
r := []rune(s)
fmt.Printf("%x\n", r)  // "[30d7 30ed 30b0 30e9 30e0]"
```

(The verb `% x` in the first `Printf` inserts a space between each pair of hex digits.)

If a slice of runes is converted to a string, it produces the concatenation of the UTF-8 encodings of each rune:

[Click here to view code image](#part0132_split_041.html#id071pro02_r)

```
fmt.Println(string(r)) // ""
```

Converting an integer value to a string interprets the integer as a rune value, and yields the UTF-8 representation of that rune:

[Click here to view code image](#part0132_split_042.html#id071pro03_r)

```
fmt.Println(string(65))     // "A", not "65"
fmt.Println(string(0x4eac)) // ""
```

If the rune is invalid, the replacement character is substituted:

[Click here to view code image](#part0132_split_043.html#id071pro04_r)

```
fmt.Println(string(1234567)) // ""
```

### 3.5.4 Strings and Byte Slices

Four standard packages are particularly important for manipulating strings: `bytes`, `strings`, `strconv`, and `unicode`. The `strings` package provides many functions for searching, replacing, comparing, trimming, splitting, and joining strings.

The `bytes` package has similar functions for manipulating slices of bytes, of type `[]byte`, which share some properties with strings. Because strings are immutable, building up strings incrementally can involve a lot of allocation and copying. In such cases, it's more efficient to use the `bytes.Buffer` type, which we'll show in a moment.

The `strconv` package provides functions for converting boolean, integer, and floating-point values to and from their string representations, and functions for quoting and unquoting strings.
