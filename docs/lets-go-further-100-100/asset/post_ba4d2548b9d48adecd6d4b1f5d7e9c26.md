
```go
package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.updateMovieHandler)
    // Add the route for the DELETE /v1/movies/:id endpoint.
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.deleteMovieHandler)

    return router
}
```

OK, let’s restart the API and try this out by deleting *Deadpool* from our movie database (this should have an ID of 3 if you’ve been following along). The delete operation should work without any problems, and you should receive the confirmation message like so:

```bash
$ curl -X DELETE localhost:4000/v1/movies/3
{
    "message": "movie successfully deleted"
}
```

If you repeat the same request to delete the already-deleted movie, you should now get a 404 Not Found response and error message. Similar to this:

```
$ curl -X DELETE localhost:4000/v1/movies/3
{
  "error": "the requested resource could not be found"
}
```

## Advanced CRUD Operations

In this section of the book we’re going to look at a few more ‘advanced’ patterns that you might want to use for the CRUD endpoints that your API provides.

You’ll learn:
- How to support *partial* updates to a resource (so that the client only needs to send the data that they want to change).
- How to use *optimistic concurrency control* to avoid race conditions when two clients try to update the same resource at the same time.
- How to use *context timeouts* to terminate long-running database queries and prevent unnecessary resource use.

## Handling Partial Updates

In this chapter we’re going to change the behavior of the `updateMovieHandler` so that it supports *partial updates* of the movie records. Conceptually this is a little more complicated than making a *complete replacement*, which is why we laid the groundwork with that approach first.

As an example, let’s say that we notice that the release year for *The Breakfast Club* is wrong in our database (it should actually be 1985, not 1986). It would be nice if we could send a JSON request containing only the change that needs to be applied, instead of all the movie data, like so:

```
{"year": 1985}
```

Let’s quickly look at what happens if we try to send this request right now:

```
$ curl -X PUT -d '{"year": 1985}' localhost:4000/v1/movies/4
{
  "error": {
    "genres": "must be provided",
    "runtime": "must be provided",
    "title": "must be provided"
  }
}
```

As we mentioned earlier in the book, when decoding the request body any fields in our `input` struct which *don’t* have a corresponding JSON key/value pair will retain their `zero-value`. We happen to check for these zero-values during validation and return the error messages that you see above.

In the context of partial update this causes a problem. How do we tell the difference between:
- A client *providing a key/value pair which has a zero-value value* — like `{"title": ""}` — in which case we want to return a validation error.
- A client *not providing a key/value pair* in their JSON at all — in which case we want to ‘skip’ updating the field but not send a validation error.

To help answer this, let’s quickly remind ourselves of what the zero-values are for different Go types.

| Go type | Zero-value |
|---|---|
| `int*`, `uint*`, `float*`, `complex` | `0` |
| `string` | `""` |
| `bool` | `false` |
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

### Performing the partial update

Let’s put this into practice, and edit our updateMovieHandler method so it supports partial updates as follows:

```
File: cmd/api/movies.go
```

```go
package main

...

func (app *application) updateMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        app.notFoundResponse(w, r)
        return
    }

    // Retrieve the movie record as normal.
    movie, err := app.models.Movies.Get(id)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrRecordNotFound):
            app.notFoundResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // Use pointers for the Title, Year and Runtime fields.
    var input struct {
        Title    *string        `json:"title"`
        Year     *int32         `json:"year"`
        Runtime  *data.Runtime  `json:"runtime"`
        Genres   []string       `json:"genres"`
    }

    // Decode the JSON as normal.
    err = app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }
}
```

```go
}

err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

To summarize this: we’ve changed our `input` struct so that all the fields now have the zero-value `nil`. After parsing the JSON request, we then go through the `input` struct fields and only update the movie record if the new value is *not* `nil`.

In addition to this, for API endpoints which perform *partial updates* on a resource, it’s appropriate to the use the HTTP method `PATCH` rather than `PUT` (which is intended for replacing a resource in full).

So, before we try out our new code, let’s quickly update our `cmd/api/routes.go` file so that our `updateMovieHandler` is only used for `PATCH` requests.

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)
}
}
```

Again, that’s looking good. We can see that the `year` value has been correctly updated, and the `version` number has been incremented, but none of the other data fields have been changed.

Let’s also quickly try the same request but including an empty `title` value. In this case the update will be blocked and you should receive a validation error, like so:

```
$ curl -X PATCH -d '{"year": 1985, "title": ""}' localhost:4000/v1/movies/4
{
  "error": {
    "title": "must be provided"
  }
}
```

## Additional Information

## Null values in JSON

One special-case to be aware of is when the client explicitly *supplies a field in the JSON request with the value* `null`. In this case, our handler will ignore the field and treat it like it hasn’t been supplied.

For example, the following request would result in no changes to the movie record (apart from the version number being incremented):

```
$ curl -X PATCH -d '{"title": null, "year": null}' localhost:4000/v1/movies/4
{
    "movie": {
        "id": 4,
        "title": "The Breakfast Club",
        "year": 1985,
        "runtime": "96 mins",
        "genres": [
            "drama"
        ],
        "version": 3
    }
}
```

In an ideal world this type of request would return some kind of validation error. But — unless you write your own custom JSON parser — there is no way to determine the difference between the client not supplying a key/value pair in the JSON, or supplying it with the value null.

In most cases, it will probably suffice to explain this special-case behavior in client documentation for the endpoint and say something like “JSON items with null values will be ignored and will remain unchanged”.
