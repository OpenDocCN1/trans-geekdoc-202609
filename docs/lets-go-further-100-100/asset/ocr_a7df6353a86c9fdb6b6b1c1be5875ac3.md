| Go type | Zero-value |
|---|---|
| `func`, `array`, `slice`, `map`, `chan` and `pointers` | `nil` |

The key thing to notice here is that pointers have the zero-value nil.

So — in theory — we could change the fields in our input struct to be pointers. Then to see if a client has provided a particular key/value pair in the JSON, we can simply check whether the corresponding field in the input struct equals nil or not.

```
// Use pointers for the Title, Year and Runtime fields.
var input struct {
    Title   *string        `json:"title"`   // This will be nil if there is no corresponding key in the JSON.
    Year    *int32         `json:"year"`    // Likewise...
    Runtime *data.Runtime  `json:"runtime"` // Likewise...
    Genres  []string       `json:"genres"`  // We don't need to change this because slices already have the zero-value nil.
}
```

# Performing the partial update

Let’s put this into practice, and edit our updateMovieHandler method so it supports partial updates as follows:

```
File: cmd/api/movies.go
```