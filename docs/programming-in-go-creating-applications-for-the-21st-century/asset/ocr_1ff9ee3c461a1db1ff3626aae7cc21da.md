# 3.6. Other String-Related Packages

```
}
}
```

The regexp greedily matches one or more "word" characters. The regexp.FindAllString() returns a []string of all nonoverlapping matches. If there was at least one match (i.e., matches is not nil), we iterate the string slice and print any duplicates by comparing the current matched word with the previous word.

Another common regexp use is to match key: value lines in configuration files. Here is an example that populates a map based on lines.

```
keyValueKey := make(map[string]string)
keyValueRx := regexp.Compile(`\s*([[:alpha:]]\w*):\s*(.+)`)
nif matches := keyValueRx.FindAllStringSubmatch(lines, -1); matches != nil {
	for _, match := range matches {
		Key[match[1]] = strings.TrimRight(match[2], "\t ")
	}
}
```

The regexp says to skip any leading whitespace and match a key which must begin with an English letter followed by zero or more letters, digits, or underscores, followed by optional whitespace, a colon, and then the value—any characters up to excluding the newline or underscores. Incidentally, we used the slightly different [A-Za-z] instead of [[:alpha:]], or if we wanted to support Unicode keys, [\p{L}\p{N}_*], Unicode letter followed by zero or more Unicode characters, decimal digits, or underscores. Since the .+ expression matches this, the regexp will work on a string that contains multiple key: value lines.

Thanks to the use of greedy matching (which is the default), the regexp will consume any whitespace that precedes the value. To get rid of whitespace at the end of a value we must use a trim function since the .+ expression's greediness means that following it with .* would have no effect. Could not have used nongreedy matching (e.g., .+*), since that would only match the first word of values that contain two or more space-separated words.

By using the regexp.FindAllStringSubmatch() function we get a slice of slices (or nil); the -1 says to match as many times as possible (without overlaps). In this example, each match will produce a slice of exactly three strings, the first containing the whole match, the second containing the key, and the third containing the value. Both the key and the value will have at least one character because their quantification is one.

Although it is best to parse XML using Go's xml.Decoder, sometimes we may imply XML-style attributes which have the form name="value" or name='value'. For these, a simple regexp is sufficient.