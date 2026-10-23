```
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
```