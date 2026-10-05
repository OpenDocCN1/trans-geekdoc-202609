slogan := "End Örættli♥%s\n%q\n%%q#\q\n"
fmt.Printf("%s\n%q\n%%q#\q\n", slogan, slogan, slogan, slogan)

End Örættli♥
"End Örættli♥"
"End \u00d3r\u00e97tl\u00e6ti\u2665"
`End Örættli♥`

The %q (quoted string) verb is used to print a string as a Go double-quoted string with printable characters printed literally, and with all other characters output using escapes (see Table 3.1, 84). If the + modifier is used, all ASCII characters (U+0020 to U+007F) are printed literally, with the rest output using escapes. If the # modifier is used the output is a Go string where possible, and a double-quoted string otherwise.

Although normally the variable corresponding to a verb is a single value of a compatible type (e.g., an int for the %d or for the %x verb), the variable can be a slice or a map, the map’s key and value are both compatible with the verb (e.g., both strings or numbers).

```
chars := [rune(slogan)
fmt.Printf("%s\n%x\n%%x\n\n", chars, chars, chars)
[45 64 20 23 72 70 74 6c 6e 74 69 2665]
[0x45 0x66 0x64 0x20 0x03 0x72 0x69 0x74 0x74 0x6c 0x74 0x66 0x45 0xx4  0x43 0x7  0x74 0x74 0x74 0x64 0x69 0x2665]
```

Here we print a slice of runes—in this example, a slice of code points—as a hexadecimal number, one per code, using the %x and %X verbs. If the # modifier is used it forces a leading 0x or X to be output for each number.

For most types, slices of the type are output as a bracket enclosed sequence of space-separated items. An exception is []byte where no brackets are spaces output unless we use the %v verb.

```
bytes := []byte(slogan)
fmt.Printf("%s\n%x\n%%x\n\n", bytes, bytes, bytes, bytes)
End Örættli♥
456e6420c3a93372c3a97446cc3a67469e299a5
456e6420c3a93372c3a97446cc3a67469e299a5
45 6E 64 20 C93 72 C3 A9 74 74 6c C3 A6 74 69 E2 99 A5
[69 110 100 32 195 147 194 195 169 116 116 108 195 166 116 105 226 153 165] *
```