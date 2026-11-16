# Helpers for test assertions

As I mentioned briefly earlier in the book, over the next few chapters we’ll be writing a lot of test assertions that are a variation of this pattern:

```
if actualValue != expectedValue {
	t.Errorf("got %v; want %v", actualValue, expectedValue)
}
```

Let's quickly abstract this code into a helper function.

If you’re following along, go ahead and create a new `internal/assert` package:

```
$ mkdir internal/assert
$ touch internal/assert/assert.go
```

And then add the following code:

```
File: internal/assert/assert.go

package assert

import (
	"testing"
)

func Equal[T comparable](t *testing.T, actual, expected T) {
	t.Helper()

	if actual != expected {
		t.Errorf("got: %v; want: %v", actual, expected)
	}
}
```

Notice how `Equal()` is a *generic function*? This means that we’ll be able to use it irrespective of what the type of the `actual` and `expected` values is. So long as both `actual` and `expected` have the *same type* and can be compared using the `!=` operator (for example, they are both `string` values, or both `int` values) our test code should compile and work fine when we call `Equal()`.

> **Note:** The `t.Helper()` function that we’re using in the code above indicates to the Go test runner that our `Equal()` function is a test helper. This means that when `t.Errorf()` is called from our `Equal()` function, the Go test runner will report the filename and line number of the code `which called` our `Equal()` function in the output.