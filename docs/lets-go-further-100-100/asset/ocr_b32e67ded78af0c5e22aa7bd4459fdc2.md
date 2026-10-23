```
```go
}

err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```
```

To summarize this: we’ve changed our `input` struct so that all the fields now have the zero-value `nil`. After parsing the JSON request, we then go through the `input` struct fields and only update the movie record if the new value is *not* `nil`.

In addition to this, for API endpoints which perform *partial updates* on a resource, it’s appropriate to the use the HTTP method `PATCH` rather than `PUT` (which is intended for replacing a resource in full).

So, before we try out our new code, let’s quickly update our `cmd/api/routes.go` file so that our `updateMovieHandler` is only used for `PATCH` requests.

```
```
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)
```
```