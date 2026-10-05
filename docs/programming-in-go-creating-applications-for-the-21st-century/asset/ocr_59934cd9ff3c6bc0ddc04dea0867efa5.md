# 3.6. Other String-Related Packages

Table 3.11 The Unicode Package's Functions

Variable c is of type rune and represents a Unicode code point.

| Syntax | Description/result |
| --- | --- |
| unicode.Is(table,c) | true if c is in the table (see text) |
| unicode.IsControl(c) | true if c is a control character |
| unicode.IsDigit(c) | true if c is a decimal digit |
| unicode.IsGraphic(c) | true if c is a “graphic” character such as a letter, number, punctuation mark, symbol, or space |
| unicode.IsLetter(c) | true if c is a letter |
| unicode.IsLower(c) | true if c is a lowercase letter |
| unicode.IsMark(c) | true if c is a mark character |
| unicode.OneOf(tables,c) | true if c is in one of the tables |
| unicode.IsPrint(c) | true if c is a printable character |
| unicode.IsPunct(c) | true if c is a punctuation character |
| unicode.IsSpace(c) | true if c is a whitespace |
| unicode.IsSymbol(c) | true if c is a symbol |
| unicode.IsTitle(c) | true if c is a title-case letter |
| unicode.IsUpper(c) | true if c is an uppercase letter |
| unicode.SimpleFold(c) | A case-folded copy of c where case is unicode.LowerCase, unicode.TitleCase, or unicode.UpperCase |
| unicode.To(case,c) | The case version of c where case is unicode.LowerCase, unicode.TitleCase, or unicode.UpperCase |
| unicode.ToLower(c) | The lowercase version of c |
| unicode.ToTitle(c) | The title-case version of c |
| unicode.ToUpper(c) | The uppercase version of c |

```
fmt.Println(IsHexDigit('8'), IsHexDigit('x'), IsHexDigit('X'),
IsHexDigit('b'), IsHexDigit('B'))

true false false true
```

The Unicode package provides the unicode.IsDigit() function to check whether a character is a decimal digit, but there is no similar function to check for hexadecimal digits, so here we have used our custom IsHexDigit() function.