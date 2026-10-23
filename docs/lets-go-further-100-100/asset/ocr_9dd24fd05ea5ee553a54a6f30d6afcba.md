```
json: error calling MarshalJSON for type data.Runtime: invalid character 'm' after top-level value
```

+   - We’re deliberately using a *value receiver* for our `MarshalJSON()` method rather than a *pointer receiver* like `func (r *Runtime) MarshalJSON()`. This gives us more flexibility because it means that our custom JSON encoding will work on both `Runtime` values and pointers to `Runtime` values. As Effective Go mentions:

> The rule about pointers vs. values for receivers is that value methods can be invoked on pointers and values, but pointer methods can only be invoked on pointers.

**Hint:** If you’re not confident about the difference between pointer and value receivers, then this blog post provides a good summary.

OK, now that the custom `Runtime` type is defined, open your `internal/data/movies.go` file and update the `Movie` struct to use it like so:

```
File: internal/data/movies.go

package data

import (
```