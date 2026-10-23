In our case, we’ll a new make a rateLimit() middleware method which creates a new rate limiter as part of the ‘initialization’ code, and then uses this rate limiter for every request that it subsequently handlers.

If you’re following along, open up the cmd/api/middleware.go file and create the middleware like so:

```
File: cmd/api/middleware.go

package main

import (
    "fmt"
    "net/http"

    "golang.org/x/time/rate" // New import
)

...

func (app *application) rateLimit(next http.Handler) http.Handler {
    // Initialize a new rate limiter which allows an average of 2 requests
per second,
    // with a maximum of 4 requests in a single ‘burst’.
    limiter := rate.NewLimiter(2, 4)

    // The function we are returning is a closure, which 'closes over' the
limiter
    // variable.
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Call limiter.Allow() to see if the request is permitted, and if
it's not,
        // then we call the rateLimitExceededResponse() helper to return a
429 Too Many
```