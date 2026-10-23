```
app.failedValidationResponse(w, r, v.Errors)
    return
}

    // Call the GetAll() method to retrieve the movies, passing in the
various filter
    // parameters.
    movies, err := app.models.Movies.GetAll(input.Title, input.Genres,
input.Filters)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    // Send a JSON response containing the movie data.
err = app.writeJSON(w, http.StatusOK, envelope{"movies": movies}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

And now we should be ready to try this out.

Go ahead and restart the API, then when you make a GET /v1/movies request you should see the slice of movies returned by GetAll() rendered as a JSON array. Similar to this:

```
$ curl localhost:4000/v1/movies
{
    "movies": [
        {
            "id": 1,
            "title": "Moana",
            "year": 2016,
```