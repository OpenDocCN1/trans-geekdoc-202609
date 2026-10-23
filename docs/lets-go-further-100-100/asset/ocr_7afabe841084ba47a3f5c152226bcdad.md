```
postgres://greenlight:pa55word@localhost/greenlight
```

# Establishing a connection pool

The code that we’ll use for connecting to the `greenlight` database from our Go application is almost exactly the same as in the first *Let’s Go* book. So we won’t dwell on the details, and hopefully this will all feel very familiar.

At a high-level:

+   - We want the DSN to be configurable at runtime, so we will pass it to the application using a command-line flag rather than hard-coding it. For simplicity during development, we’ll use the DSN above as the default value for the flag.
+   - In our `cmd/api/main.go` file we’ll create a new `openDB()` helper function. In this helper we’ll use the `sql.Open()` function to establish a new `sql.DB` connection pool, then — because connections to the database are established lazily as and when needed for the first time — we will also need to use the `db.PingContext()` method to actually create a connection and verify that everything is set up correctly.

Let’s head back to our `cmd/api/main.go` file and update it like so:

```
File: cmd/api/main.go
```