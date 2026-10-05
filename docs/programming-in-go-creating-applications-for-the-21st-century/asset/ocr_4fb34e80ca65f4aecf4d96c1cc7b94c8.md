# Chapter 3. Strings

# Table 3.18 The *regexp.Regexp Type's Methods #1

Variable rx is of type *regexp.Regexp; s is the string to match; b is the []byte to match; r is the io. RuneReader to match; and n is the maximum number of matches (-1 means as many as possible). A nil return means match(es).

| Syntax | Description/result |
| --- | --- |
| rx.Expand(...) | Performs the $s replacements done by the Replace()—rarely used directly (advanced) |
| rx.FindString(...) | Performs the $s replacements done by the ReplaceAll()—rarely used directly (advanced) |
| rx.Find(b) | []byte with the leftmost match or nil |
| rx.FindAll(b, n) | [][]byte of all nonoverlapping matches or nil |
| rx.FindAllIndex(b, n) | []int a slice of 2-item slices identifying a match or e.g., b[pos:pos] |
| rx.FindAllString(s, n) | []int of all nonoverlapping matches or nil |
| rx.FindAllStringIndex(s, n) | []int a slice of 2-item slices identifying a match or e.g., s[pos:pos] |
| rx.FindAllSubmatch(s, n) | [][]string a slice of string slices where each string corresponds to a capture or nil |
| rx.FindAllSubmatchIndex(s, n) | [][]int a slice of 2-item slices that corresponds to a capture or nil |
| rx.FindAllSubmatch(b, n) | [][]byte a slice of byte slices where each byte corresponds to a capture or nil |
| rx.FindAllSubmatchIndex(b, n) | [][]int a slice of 2-item slices that corresponds to nil |
| rx.FindIndex(b) | []int identifying the leftmost match; e.g., b[pos:pos] where pos is the 2-item slice, or nil |
| rx.FindReaderIndex(r) | []int identifying the leftmost match or nil |
| rx.FindReaderSubmatchIndex(r) | []int identifying the match and captures or nil |
| rx.FindString(s) | The leftmost match or an empty string |
| rx.FindStringIndex(s) | []int identifying the leftmost match or nil |
| rx.FindStringSubmatch(s) | []string with the leftmost match and captures or nil |
| rx.FindStringSubmatchIndex(s) | []int identifying the leftmost match and captures or nil |