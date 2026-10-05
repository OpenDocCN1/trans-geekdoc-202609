
## 3.4. Indexing and Slicing Strings

| s[:2] | s[2:] | s[2:] == s[len(s)-4:] | Slices |
|---|---|---|---|---|---|
| 'n' | 'a' | 'i' | 'v' | 'e' | Characters |
| U+006E | U+0061 | U+00EE | U+0076 | U+0065 | Code points |
| 0x6E | 0x61 | 0xC3 | 0xAF | 0x65 | Bytes |
| 0 | 1 | 2 | 3 | 4 | Indexes |
| | | | len(s)-2 | len(s)-1 | Anatomy of a string |

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

## Chapter 3. Strings

Now let's look at a real slice example, one that takes a rather naïve approach. Suppose we have a line of text and want to extract the line’s first and last words. One simple way to write the code is like this:

```
line := "rød og gule sløjer"
i := strings.Index(line, " ") // Get the index of the first space
firstWord := line[:i] // Slice up to the first space
j := strings.LastIndex(line, " ") // Get the index of the last space
lastWord := line[j+1:] // Slice after the last space
fmt.Println(firstWord, lastWord) // Prints: rød sløjer
```

The firstword (of type string) is assigned the bytes from the line from index position 0 (the first byte) to index position 1-1 (i.e., up to the last byte before the space) since string slices up to but exclude the end position. Similarly, the lastword is assigned the bytes from the line index position j+1 (the byte after the space), to the end of the line’s bytes (i.e., to index position len(line)).

Although this example approach is fine for spaces and would also work for other 7-bit ASCII characters, it’s not suitable for working with arbitrary Unicode characters such as U+2028 (Line Separator, ⏎) or U+2029 (Paragraph Separator, ℽ).

Here is how to find the first and last words of a string no matter what whitespace characters used to separate the words.

```
line := "rå tørt\u2028vær"
i := strings.Index(line, " ")
firstWord := line[:i]
j := strings.LastIndexFunc(line, unicode.IsSpace) // j == 9
size := utf8.DecodeRuneInString(line[j:]) // size == 3
lastWord := line[j+size:] // j + size == 12
// (Note logic corrected based on context)
```

The line is shown as characters, code points, and hints in Figure 3.2; the figure also shows the byte index positions and the slices in the code snippet.

The strings.IndexFunc() function returns the first index position in the string given as its first argument the function given as its second argument (with signature func(rune) bool) returns true. The strings.LastIndexFunc() does the same except that it works from the end of the string and returns the last index position by which the function returns. Here we use the unicode package’s IsSpace() function as the argument and returns true if the code point (of type rune) is a whitespace character. (See Table 3.1.) A function’s name is a reference to the function, and so be passed whenever a parameter is required—so long as the named (i.e., referred to) function's signature matches the parameter. (See §4.1.)

Using the strings.IndexFunc() to find the first whitespace character and slicing the string to get the first word is easy. When searching for the last whitespace character we must be careful because some characters are encoded as more than a single UTF-8 byte. We solve this problem by using the utf8.DecodeRuneString() function to give us the number of bytes occupied by the first character in the slice that starts where the last character begins. We then add this number to the last whitespace character's index position to jump over the last character.

## 3.5. String Formatting with the Fmt Package

Go's standard library's fmt package provides print functions for writing data to the console, and other values satisfying the writer interface. These functions are listed in Table 3.3. Some of the print functions return an error. It is not uncommon to return this value when printing to the console, but the error should be checked when printing to files, network connections, and so.

The fmt package also provides various scan functions (such as fmt.Scan(), fmt.Scan(), and fmt.Scanln()) for reading data from the console, from files, and from strings. Some of these functions are used in Chapter 8 (§8.1.3.2.—see also Table 8.2 (► 383). An alternative to using the scan functions is to split each string into fields using the strings.Fields() function and convert those that aren't strings to values (e.g., numbers) using functions from the strconv package—see Tables 3.8 and 3.9 (► 114–115). Recall from Chapter 1 that we can read input typed at the keyboard by creating a bufio.Reader to read from os.Stdin and use the bufio.Reader.ReadString() function to read each line entered ($1.7, 40).

The easiest way to output values is to use the fmt.Print() and fmt.Println() functions to print to os.Stdout, i.e., to the console), or the fmt.Fprint() and fmt.Fprintf() functions to output to a given io.Writer (e.g., to a file), or the fmt.Sprint() and fmt.Println() functions to output to a string.

# Table 3.3 The Fmt Package's Print Functions

| Syntax | Description/result |
|---|---|
| fmt.Errorf(format, args...) | Returns an error value containing a string created with the format and the args |
| fmt.Fprintf(writer, args...) | Writes the args to the writer using format %v and space-separating nonstrings; returns the number of bytes written, and an error or nil |
| fmt.Printf(writer, args...) | Writes the args to the writer using the format string; returns the number of bytes written, and an error or nil |
| fmt.Println(writer, args...) | Writes the args to the writer using format %v, space-separated and ending with a newline; returns the number of bytes written, and an error or nil |
| fmt.Print(args...) | Writes the args to os.Stdout using format %v and space-separating nonstrings; returns the number of bytes written, and an error or nil |
| fmt.Printf(format, args...) | Writes the args to os.Stdout using the format string; returns the number of bytes written, and an error or nil |
| fmt.Println(args...) | Writes the args to os.Stdout using format %v, space-separated and ending with a newline; returns the number of bytes written, and an error or nil |
| fmt.Sprint(args...) | Returns a string of the args, each formatted using %v and space-separating nonstrings |
| fmt.Sprintf(format, args...) | Returns a string of the args formatted using the string |
| fmt.Println(args...) | Returns a string of the args, each formatted using %v, space-separated and ending with a newline |

> Go has two built-in print functions, print() and println(). These should not be used; they exist purely for the convenience of Go implementers and may be removed from the language.
