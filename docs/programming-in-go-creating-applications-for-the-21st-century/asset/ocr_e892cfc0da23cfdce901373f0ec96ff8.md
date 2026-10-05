# 3.4. Indexing and Slicing Strings

| s[:2] | | s[2:] == s[len(s)-4:] | Slices |
|---|---|---|---|---||
| 'n' | 'a' | 'i' | 'v' | 'e' | Characters |
| U+006E | U+0061 | U+00EE | U+0076 | U+0065 | Code points |
| 0x6E | 0x61 | 0xC3 | 0xAF | 0x65 | Bytes |
| 0 | 1 | 2 | 3 | 4 | Indexes |
| | | | len(s)-2 | len(s)-1 | Anatomy of a string

> Figure 3.1 Anatomy of a string

Each index position shown in Figure 3.1 can be used with the [] operator to return the corresponding ASCII character (as a byte)—example, s[0] == 'n' and s[len(s)-1] == 'e'. The index position of the start of the i character is 2, but if we use s[2:] we would simply get the first of the UTF-8 bytes used to encode î (0xC3); such bytes are rarely what we want.

For strings that contain only 7-bit ASCII characters we can extract the first character (as a byte) using the syntax s[0], and the last character using s[len(s)-1]. However, in general we should use utf8.DecodeRuneString() to get the character as a rune, along with the number of UTF-8 bytes used to represent it, and utf8.DecodeLastRuneString() to get the last character. See Table 3.10.

If we need to identify individual characters, a couple of options are open to us. For strings that contain only 7-bit ASCII we can use the [] operator which gives us very fast O(1) lookups. For non-ASCII strings, we can convert the string to a []rune and use the [] operator. This delivers fast O(1) lookup performance, but at the expense of the one-off conversion which costs CPU and memory O(n).

In the case of our example, if we wrote chars := []rune(s), the chars variable would be created as a rune (i.e., int32) with the five code points—compared with six bytes—shown in Figure 3.1. Recall that we can easily convert any rune (code point) back to a string—using the string(char) syntax.

For arbitrary strings (i.e., those that contain non-ASCII characters), extracting characters by index is rarely the right approach. Better is to use string slicing—which also has the convenience of returning a string rather than a byte. To safely slice arbitrary strings, it is best to find the index position where we want to slice up or from using one of the strings’ functions—see Tables 3.6 and 3.7 (► 108–109).

The following equality holds for string slices—and, in fact, for slices of every kind:

```
s := s[:i] + s[i:] // s is a string; i is an int; 0 <= i <= len(s)
```