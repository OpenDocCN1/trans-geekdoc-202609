```
// Requests response (we will create this helper in a minute).
if !limiter.Allow() {
    app.rateLimitExceededResponse(w, r)
    return
}

next.ServeHTTP(w, r)
})
}
```

In this code, whenever we call the Allow() method on the rate limiter exactly one token will be consumed from the bucket. If there are no tokens left in the bucket, then Allow() will return false and that acts as the trigger for us send the client a 429 Too Many Requests response.

It’s also important to note that the code behind the Allow() method is protected by a mutex and is safe for concurrent use.

Let’s now go to our cmd/api/errors.go file and create the rateLimitExceededResponse() helper. Like so:

```
File: cmd/api/errors.go

package main

...

func (app *application) rateLimitExceededResponse(w http.ResponseWriter, r *http.Request) {
    message := "rate limit exceeded"
```