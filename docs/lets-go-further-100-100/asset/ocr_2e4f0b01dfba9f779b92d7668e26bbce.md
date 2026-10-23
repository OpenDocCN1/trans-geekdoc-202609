```
&movie.CreatedAt,
&movie.Title,
&movie.Year,
&movie.Runtime,
pq.Array(&movie.Genres),
&movie.Version,
)

if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

return &movie, nil
}

...
```

There are a couple of things in the code above that I’d like to emphasize and explain:

+   - The `defer cancel()` line is necessary because it ensures that the resources associated with our context will always be released before the `Get()` method returns, thereby preventing a memory leak. Without it, the resources won’t be released until either the 3-second timeout is hit or the parent context (which in this specific example is `context.Background()`) is canceled.
+   - The timeout countdown begins from the moment that the context is created using `context.WithTimeout()`. Any time spent