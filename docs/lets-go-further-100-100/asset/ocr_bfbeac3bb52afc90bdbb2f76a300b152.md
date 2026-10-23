```
...
```

Next let's update our database model's Update() method to execute the new SQL query and manage the situation where a matching record couldn't be found.

# File: internal/data/movies.go

```
```go
package data

...

func (m MovieModel) Update(movie *Movie) error {
    // Add the 'AND version = $6' clause to the SQL query.
    query := `
        UPDATE movies
        SET title = $1, year = $2, runtime = $3, genres = $4, version =
        version + 1
        WHERE id = $5 AND version = $6
        RETURNING version`

    args := []interface{}{
        movie.Title,
        movie.Year,
        movie.Runtime,
        pq.Array(movie.Genres),
        movie.ID,
        movie.Version, // Add the expected movie version.
    }

    // Execute the SQL query. If no matching row could be found, we know the movie
    // version has changed (or the record has been deleted) and we return our
```
```