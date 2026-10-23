It’s simpler than it sounds. All you have to do is something like this:

```
```go
func main() {
    ...
    // Initialize the custom logger.
    logger := jsonlog.New(os.Stdout, jsonlog.LevelInfo)
    ...
    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", cfg.port),
        Handler:      app.routes(),
        // Create a new Go log.Logger instance with the log.New() function,
        // passing in
        // our custom Logger as the first parameter. The "" and 0 indicate
        // that the
        // log.Logger instance should not use a prefix or any flags.
        ErrorLog:     log.New(logger, "", 0),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }
    ...
}
```
```

With that set up, any log messages that http.Server writes will be passed to our Logger.Write() method, which in turn will output a log entry in JSON format at the ERROR level.

# Third-party logging packages