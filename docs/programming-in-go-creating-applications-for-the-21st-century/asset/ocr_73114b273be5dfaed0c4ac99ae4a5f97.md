# 3.6. Other String-Related Packages

does not.) So, in this case, every sequence of one or more whitespace characters (ASCII whitespaces and Unicode line and paragraph separators) is replaced with a single space.

For our final regexp example we will see how to replace using a function.

```
unaccentedLatin1Rx := regexp.MustCompile(
'[AAAAAAAÈÈÊIIIIÑÓÓÙÝàáççéêíïñðõøùùý]+)
unaccented := unaccentedLatin1Rx.ReplaceAllStringFunc(latin1,
unaccentedLatin1)
```

The regexp simply matches one or more accented Latin-1 letters. The regexp.ReplaceAllStringFunc() function calls the passed as its second argument (with signature func(string) string) every time there is a match. The function gives the match's text as its argument and this text is replaced with the function returns (which can be an empty string).

```
func UnaccentedLatin1(s string) string {
  chars := make([]rune, 0, len(s))
  for _, char := range s {
    switch char {
    case 'A', 'Á', 'Â', 'Ä', 'Ã', 'Ā':
      char = 'A'
    case 'É':
      chars = append(chars, 'A')
      char = 'E'
    case 'Ý', 'ÿ':
      char = 'y'
    }
    chars = append(chars, char)
  }
  return string(chars)
}
```

This simple function replaces the accented Latin-1 character with its unaccented cousin. It also replaces the æ ligature (which is a full character in some languages) with a and e. Of course, this example is artificial in this case we could just as easily write unaccented := UnaccentedLatin1(latin1) to perform the conversion.

This completes the illustrative regexp examples. Notice that in Tables 3.18 and 3.19, for every "String" that operates on []byte there is a corresponding function operating on strings. Also, a few of the book's other examples use the regexp package (e.g., 35 ◄ 344).