# Table 3.8 The Strconv Package's Functions #1

Parameter bs is a []byte, base is a number base (2–36), bits is the bit size the result must fit into (8, 16, 32, 64—or for int's for ints; 32 or 64 for float64s), and s is a string.

| Syntax | Description/result |
| strconv.AppendBool(bs, b) | bs with "true" or "false" appended depending on bool b |
| strconv.AppendFloat(bs, f, fmt, prec, bits) | bs with float64 f appended; see strconv.Format() for the other parameters |
| strconv.AppendInt(i, base) | bs with int64 i appended using the given base |
| strconv.AppendQuote(bs, s) | bs with s appended using strconv.Quote() |
| strconv.AppendQuote-Rune(bs, char) | bs with rune char appended using strconv.QuoteR() |
| strconv.AppendQuote-RuneToASCII(bs, char) | bs with rune char appended using strconv.QuoteRToASCII() |
| strconv.AppendQuote-ToASCII(bs, s) | bs with s appended using strconv.QuoteToASCII() |
| strconv.AppendUint(u, base) | bs with uint64 u appended using the given base |
| strconv.Atoi(s) | string converted to an int, and an error or nil; see also strconv.ParseInt() |
| strconv.Canbackquote(s) | true if bs can be represented in Go syntax using backticks |
| strconv.FormatBool(tf) | "true" or "false" depending on bool tf |
| strconv.FormatFloat(f, fmt, prec, bits) | float64 f as a string. The fmt is a byte corresponding to an fmt.Print() verb, 'b' for %b, 'e' for %e, etc. (see Table 3.4, 95 ◄). The prec is the number of digits after the decimal point for fmt of 'e', 'E', and 'f'; or the number of digits for fmt of 'g' and 'G'—use -1 to request the smallest number of digits that can be used while preserving accuracy The bits bits are usually 64 |
| strconv.FormatInt(i, base) | int64 i as a string in base base |
| strconv.FormatUint(u, base) | uint64 u as a string in base base |
| strconv.IsPrint(c) | true if rune c is a printable character |
| strconv.Ito(i) | int i as a string using base 10; see also strconv.Format() |