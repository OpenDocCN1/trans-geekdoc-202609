
// Use rows.Next to iterate through the rows in the resultset.
for rows.Next() {
    // Initialize an empty Movie struct to hold the data for an
individual movie.
    var movie Movie

    // Scan the values from the row into the Movie struct. Again, note
that we're
    // using the pq.Array() adapter on the genres field here.
    err := rows.Scan(
        &movie.ID,
        &movie.CreatedAt,
        &movie.Title,
        &movie.Year,
        &movie.Runtime,
        pq.Array(&movie.Genres),
        &movie.Version,
    )
    if err != nil {
        return nil, err
    }

    // Add the Movie struct to the slice.
    movies = append(movies, &movie)
}

// When the rows.Next() loop has finished, call rows.Err() to retrieve
any error
    // that was encountered during the iteration.
if err = rows.Err(); err != nil {
    return nil, err
}

// If everything went OK, then return the slice of movies.
return movies, nil
}

Next up, we need to adapt the `listMoviesHandler` so that it calls the new `GetAll()` method to retrieve the movie data, and then writes this data as a JSON response.

If you’re following along, go ahead and update the handler like so:

```
File: cmd/api/movies.go

package main

...

func (app *application) listMoviesHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title string
        Genres []string
        data.Filters
    }

    v := validator.New()

    qs := r.URL.Query()

    input.Title = app.readString(qs, "title", "")
    input.Genres = app.readCSV(qs, "genres", []string{})

    input.Filters.Page = app.readInt(qs, "page", 1, v)
    input.Filters.PageSize = app.readInt(qs, "page_size", 20, v)

    input.Filters.Sort = app.readString(qs, "sort", "id")
    input.Filters.SortSafelist = []string{"id", "title", "year", "runtime", "-id", "-title", "-year", "-runtime"}

    if data.ValidateFilters(v, input.Filters); !v.Valid() {
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
"runtime": "107 mins",
"genres": [
    "animation",
    "adventure"
],
"version": 1
},
{
    "id": 2,
    "title": "Black Panther",
    "year": 2018,
    "runtime": "134 mins",
    "genres": [
        "sci-fi",
        "action",
        "adventure"
    ],
    "version": 2
},
{
    "id": 4,
    "title": "The Breakfast Club",
    "year": 1985,
    "runtime": "97 mins",
    "genres": [
        "comedy"
    ],
    "version": 5
}
]
}
```

## Filtering Lists

In this chapter we’re going to start putting our query string parameters to use, so that clients can search for movies with a specific title or genres.

Specifically, we’ll build a restrictive filter which allows clients to search based on a case-insensitive exact match for movie title and/or one or more movie genres. For example:

```
```
// List all movies.
/v1/movies

// List movies where the title is a case-insensitive exact match for 'black panther'.
/v1/movies?title=black+panther

// List movies where the genres includes 'adventure'.
/v1/movies?genres=adventure

// List movies where the title is a case-insensitive exact match for 'moana' AND the
// genres include both 'animation' AND 'adventure'.
/v1/movies?title=moana&genres=animation,adventure
```
```

**Note:** The + symbol in the query strings above is a URL-encoded space character. Alternatively you could use %20

> instead... either will work in the context of a query string.

## Dynamic filtering in the SQL query

The hardest part of building a dynamic filtering feature like this is the SQL query to retrieve the data — we need it to work with no filters, filters on both `title` and `genres`, or a filter on only one of them.

To deal with this, one option is to build up the SQL query dynamically at runtime... with the necessary SQL for each filter concatenated or interpolated into the `WHERE` clause. But this approach can make your code messy and difficult to understand, especially for large queries which need to support lots of filter options.

In this book we’ll opt for a different technique and use a fixed SQL query which looks like this:

```
```sql
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (LOWER(title) = LOWER($1) OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```
```

This SQL query is designed so that each of the filters behaves like it is ‘optional’. For example, the condition `(LOWER(title) = LOWER($1) OR $1 = '')` will evaluate as `true` if the placeholder parameter `$1` is a case-insensitive match for the movie
title or the placeholder parameter equals '' . So this filter condition will essentially be ‘skipped’ when movie title being searched for is the empty string "".

The (genres @> $2 OR $2 = '{}') condition works in the same way. The @> symbol is the ‘contains’ operator for PostgreSQL arrays, and this condition will return true if all values in the placeholder parameter $2 are contained in the database genres field or the placeholder parameter contains an empty array.

You’ll remember that earlier in the book we set up our listMoviesHandler so that the empty string "" and an empty slice are used as the default values for the title and genres filter parameters:

```
input.Title = app.readString(qs, "title", "")
input.Genres = app.readCSV(qs, "genres", []string{})
```

So, putting this all together, it means that if a client doesn’t provide a title parameter in their query string, then value for the $1 placeholder will be the empty string "", and the filter condition in the SQL query will evaluate to true and act like it has been ‘skipped’. Likewise with the genres parameter.

Note: PostgreSQL also provides a range of other useful array operators and functions, including the && ‘overlap’ operator, the
<@ ‘contained by’ operator, and the `array_length()` function. A complete list [can be found here](.).

Alright, let’s head back to our `internal/data/movies.go` file, and update the `GetAll()` method to use this new query. Like so:

```
File: internal/data/movies.go

package data

...

func (m MovieModel) GetAll(title string, genres []string, filters Filters) ([]*Movie, error) {
    // Update the SQL query to include the filter conditions.
    query := `
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (LOWER(title) = LOWER($1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
        ORDER BY id`

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // Pass the title and genres as the placeholder parameter values.
    rows, err := m.DB.QueryContext(ctx, query, title, pq.Array(genres))
    if err != nil {
        return nil, err
    }

    defer rows.Close()

    movies := []*Movie{}

```
```go
for rows.Next() {
    var movie Movie

    err := rows.Scan(
        &movie.ID,
        &movie.CreatedAt,
        &movie.Title,
        &movie.Year,
        &movie.Runtime,
        pq.Array(&movie.Genres),
        &movie.Version,
    )
    if err != nil {
        return nil, err
    }

    movies = append(movies, &movie)
}

if err = rows.Err(); err != nil {
    return nil, err
}

return movies, nil
}
```

Now let's restart the application and try this out, using the examples that we gave at the start of the chapter. If you've been following along, the responses should look similar to this:

```
```
$ curl "localhost:4000/v1/movies?title=black+panther"
{
    "movies": [
        {
