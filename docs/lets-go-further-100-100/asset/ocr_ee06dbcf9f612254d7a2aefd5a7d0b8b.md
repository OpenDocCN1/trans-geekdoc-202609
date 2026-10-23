```
package main

...

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title   string  `json:"title"`
        Year    int32   `json:"year"`
        Runtime int32   `json:"runtime"`
        Genres  []string `json:"genres"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        // Use the new badRequestResponse() helper.
        app.badRequestResponse(w, r, err)
        return
    }

    fmt.Fprintf(w, "%+v\n", input)
}

...
```

This is a small change, but a useful one. As our application gradually gets more complex, using specialist helpers like this to manage different kinds of errors will help ensure that our error responses remain consistent across all our endpoints.