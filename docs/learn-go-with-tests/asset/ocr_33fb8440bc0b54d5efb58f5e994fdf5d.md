```
log.Fatal(http.ListenAndServe(":5000", server))
}
```

Build it, run it and then use `curl` to test it out.

+   - Run this a few times, change the player names if you like `curl -X POST http://localhost:5000/players/Pepper`
+   - Check scores with `curl http://localhost:5000/players/Pepper`

Great! You've made a REST-ish service. To take this forward you'd want to pick a data store to persist the scores longer than the length of time the program runs.

+   - Pick a store (Bolt? Mongo? Postgres? File system?)
+   - Make `PostgresPlayerStore` implement `PlayerStore`
+   - TDD the functionality so you're sure it works
+   - Plug it into the integration test, check it's still ok
+   - Finally plug it into `main`

# Refactor

We are almost there! Lets take some effort to prevent concurrency errors like these

```
fatal error: concurrent map read and map write
```

By adding mutexes, we enforce concurrency safety especially for the counter in our `RecordWin` function. Read more about mutexes in the sync chapter.

# Wrapping up

# http.Handler

+   - Implement this interface to create web servers