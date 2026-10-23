```
```go
// will return the empty string "".
s := qs.Get(key)

// If no key exists (or the value is empty) then return the default value.
if s == "" {
    return defaultValue
}

// Otherwise return the string.
return s
}

// The readCSV() helper reads a string value from the query string and then splits it
// into a slice on the comma character. If no matching key could be found, it returns
// the provided default value.
func (app *application) readCSV(qs url.Values, key string, defaultValue []string) []string {
    // Extract the value from the query string.
    csv := qs.Get(key)

    // If no key exists (or the value is empty) then return the default value.
    if csv == "" {
        return defaultValue
    }

    // Otherwise parse the value into a []string slice and return it.
    return strings.Split(csv, ",")
}

// The readInt() helper reads a string value from the query string and
converts it to an
// integer before returning. If no matching key could be found it returns the
provided
// default value. If the value couldn't be converted to an integer, then we
```
```