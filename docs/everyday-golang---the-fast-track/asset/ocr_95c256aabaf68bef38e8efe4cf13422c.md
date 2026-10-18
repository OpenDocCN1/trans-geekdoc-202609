```
$ go run .
Error: Get "": unsupported protocol scheme ""
exit status 1

$ go run . -uri https://gitzub.com
Error: Get "https://gitzub.com": dial tcp: lookup gitzub.com: no such host
exit status 1
```

# Using a context to handle timeouts

Now, there’s also another potential problem here. Some websites may hang or keep a connection open indefinitely. Go provides a concept called “context” that can be passed into calls that make use of external resources like with our HTTP request from above.

A Context carries a deadline, a cancellation signal, and other values across API boundaries.

You can view the docs for the context package here: context.

Some library functions allow a Context to be passed via a parameter, but if one is not present, you can get the background context with:

```
ctx := context.Background()
```

You may also see context.TODO() used which can be used when no context is available, or it’s unclear which context to use.

Its API also has several utility methods for defining a cancellation policy:

```
func WithCancel(parent Context) (ctx Context, cancel CancelFunc)
```

A parent context needs to be passed in, when the cancel function is called, any in-progress operations must be stopped and resources should be released.

```
func WithDeadline(parent Context, d time.Time) (Context, CancelFunc)
```

This function is similar to WithCancel, except there is a deadline time/date for some future date at which time the operation should be cancelled. This is useful with HTTP requests or when accessing an external system.

```
func WithTimeout(parent Context, timeout time.Duration) (Context, CancelFunc)
```

The WithTimeout function is also similar, but provides a helper so that a timeout value can be passed in rather than an actual date in the future.

In the example below, you’ll see how WithTimeout works.

```
package main

import (
  "context"
  "flag"
  "fmt"
  "io"
  "net/http"
  "os"
  "strings"
  "time"
)
```