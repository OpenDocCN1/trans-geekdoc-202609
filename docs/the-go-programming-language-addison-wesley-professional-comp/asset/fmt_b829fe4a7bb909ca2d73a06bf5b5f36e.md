
```
fmt.Println(s[:5]) // "hello"
fmt.Println(s[7:]) // "world"
fmt.Println(s[:])  // "hello, world"
```

The `+` operator makes a new string by concatenating two strings:

[Click here to view code image](#part0132_split_030.html#id065pro02_r)

```
fmt.Println("goodbye" + s[5:]) // "goodbye, world"
```

Strings may be compared with comparison operators like `==` and `<`; the comparison is done byte by byte, so the result is the natural lexicographic ordering.

String values are immutable: the byte sequence contained in a string value can never be changed, though of course we can assign a new value to a string `variable`. To append one string to another, for instance, we can write

```
s := "left foot"
t := s
s += ", right foot"
```

This does not modify the string that `s` originally held but causes `s` to hold the new string formed by the `+=` statement; meanwhile, `t` still contains the old string.

[Click here to view code image](#part0132_split_031.html#id065pro03_r)

```
fmt.Println(s) // "left foot, right foot"
fmt.Println(t) // "left foot"
```

Since strings are immutable, constructions that try to modify a string's data in place are not allowed:

[Click here to view code image](#part0132_split_032.html#id065pro04_r)

```
s[0] = 'L' // compile error: cannot assign to s[0]
```

Immutability means that it is safe for two copies of a string to share the same underlying memory, making it cheap to copy strings of any length. Similarly, a string `s` and a substring like `s[7:]` may safely share the same data, so the substring operation is also cheap. No new memory is allocated in either case. [Figure 3.4](#part0033.html#id-figures-stringshare) illustrates the arrangement of a string and two of its substrings sharing the same underlying byte array.

![The string "hello, world" and two substrings.](images/00011.jpeg)

**Figure 3.4.** The string `"hello, world"` and two substrings.

### 3.5.1 String Literals

A string value can be written as a `string literal`, a sequence of bytes enclosed in double quotes:

```
"Hello, "
```

Because Go source files are always encoded in `UTF-8` and Go text strings are conventionally interpreted as `UTF-8`, we can include Unicode code points in string literals.

Within a double-quoted string literal, `escape sequences` that begin with a backslash `\` can be used to insert arbitrary byte values into the string. One set of escapes handles ASCII control codes like newline, carriage return, and tab:

| Escape sequence | Meaning |
| --- | --- |
| `\a` | “alert” or bell |
| `\b` | backspace |
| `\f` | form feed |
| `\n` | newline |
| `\r` | carriage return |
| `\t` | tab |
| `\v` | vertical tab |
| `\'` | single quote (only in the rune literal `'\''`) |
| `\"` | double quote (only within `"..."` literals) |
| `\\` | backslash |

Arbitrary bytes can also be included in literal strings using hexadecimal or octal escapes. A `hexadecimal escape` is written `\xhh`, with exactly two hexadecimal digits `h` (in upper or lower case). An `octal escape` is written `\ooo` with exactly three octal digits `o` (0 through 7) not exceeding `\377`. Both denote a single byte with the specified value. Later, we'll see how to encode Unicode code points numerically in string literals.

A `raw string literal` is written `` `...` ``, using backquotes instead of double quotes. Within a raw string literal, no escape sequences are processed; the contents are taken literally, including backslashes and newlines, so a raw string literal may spread over several lines in the program source. The only processing is that carriage returns are deleted so that the value of the string is the same on all platforms, including those that conventionally put carriage returns in text files.

Raw string literals are a convenient way to write regular expressions, which tend to have lots of backslashes. They are also useful for HTML templates, JSON literals, command usage messages, and the like, which often extend over multiple lines.

[Click here to view code image](#part0132_split_033.html#id067pro01_r)

```
const GoUsage = `Go is a tool for managing Go source code.

Usage:
    go command [arguments]
...`
```

### 3.5.2 Unicode

Long ago, life was simple and there was, at least in a parochial view, only one character set to deal with: ASCII, the American Standard Code for Information Interchange. ASCII, or more precisely US-ASCII, uses 7 bits to represent 128 "characters": the upper- and lower-case letters of English, digits, and a variety of punctuation and device-control characters. For much of the early days of computing, this was adequate, but it left a very large fraction of the world's population unable to use their own writing systems in computers. With the growth of the Internet, data in myriad languages has become much more common. How can this rich variety be dealt with at all and, if possible, efficiently?

The answer is Unicode (`unicode.org`), which collects all of the characters in all of the world's writing systems, plus accents and other diacritical marks, control codes like tab and carriage return, and plenty of esoterica, and assigns each one a standard number called a `Unicode code point` or, in Go terminology, a `rune`.

Unicode version 8 defines code points for over 120,000 characters in well over 100 languages and scripts. How are these represented in computer programs and data? The natural data type to hold a single rune is `int32`, and that's what Go uses; it has the synonym `rune` for precisely this purpose.

We could represent a sequence of runes as a sequence of `int32` values. In this representation, which is called `UTF-32` or `UCS-4`, the encoding of each Unicode code point has the same size, 32 bits. This is simple and uniform, but it uses much more space than necessary since most computer-readable text is in ASCII, which requires only 8 bits or 1 byte per character. All the characters in widespread use still number fewer than 65,536, which would fit in 16 bits. Can we do better?

### 3.5.3 UTF-8

UTF-8 is a variable-length encoding of Unicode code points as bytes. UTF-8 was invented by Ken Thompson and Rob Pike, two of the creators of Go, and is now a Unicode standard. It uses between 1 and 4 bytes to represent each rune, but only 1 byte for ASCII characters, and only 2 or 3 bytes for most runes in common use. The high-order bits of the first byte of the encoding for a rune indicate how many bytes follow. A high-order `0` indicates 7-bit ASCII, where each rune takes only 1 byte, so it is identical to conventional ASCII. A high-order `110` indicates that the rune takes 2 bytes; the second byte begins with `10`. Larger runes have analogous encodings.

[View table image](#part0133.html#table01_r)

| Bits pattern | Code point range | Notes |
| --- | --- | --- |
| `0xxxxxx` | runes 0–127 | (ASCII) |
| `110xxxxx 10xxxxxx` | 128–2047 | (values <128 unused) |
| `1110xxxx 10xxxxxx 10xxxxxx` | 2048–65535 | (values <2048 unused) |
| `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx` | 65536–0x10ffff | (other values unused) |

A variable-length encoding precludes direct indexing to access the *n*-th character of a string, but UTF-8 has many desirable properties to compensate. The encoding is compact, compatible with ASCII, and self-synchronizing: it's possible to find the beginning of a character by backing up no more than three bytes. It's also a prefix code, so it can be decoded from left to right without any ambiguity or lookahead. No rune's encoding is a substring of any other, or even of a sequence of others, so you can search for a rune by just searching for its bytes, without worrying about the preceding context. The lexicographic byte order equals the Unicode code point order, so sorting UTF-8 works naturally. There are no embedded `NUL` (zero) bytes, which is convenient for programming languages that use `NUL` to terminate strings.
