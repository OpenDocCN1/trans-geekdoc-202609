following a hyphen to upper case, and the rest of the letters to lowercase. This has the practical implication that when calling these methods the header name is case-insensitive.

If you need to avoid this canonicalization behavior, you can edit the underlying header map directly. It has the type map[string][]string behind the scenes. For example:

```
w.Header()["X-XSS-Protection"] = []string{"1; mode=block"}
```

> **Note:** If a HTTP/2 connection is being used, Go will *always* automatically convert the header names and values to lowercase for you when writing the response, as per the HTTP/2 specifications.