calling source code in the log entries, like so:

```
logger := slog.New(slog.NewTextHandler(os.Stdout, &slog.HandlerOptions{
AddSource: true,
}))
```

The log entries will look similar to this, with the caller location recorded under the source key:

```
time=2024-03-18T11:29:23.000+00:00 level=INFO source=/home/alex/code/snippetbox/cmd/web/main.go:32 msg="starting server" addr
```

# Decoupled logging

In this chapter we've set up our structured logger to write entries to os.Stdout — the standard out stream.

The big benefit of writing log entries to os.Stdout is that your application and logging are decoupled. Your application itself isn't concerned with the routing or storage of the logs, and that can make it easier to manage the logs differently depending on the environment.

During development, it's easy to view the log output because the standard out stream is displayed in the terminal.

In staging or production environments, you can redirect the stream to a final destination for viewing and archival. This destination could be on-disk files, or a logging service such as Splunk. Either way, the final destination of the logs can be managed by your execution environment independently of the application.

For example, we could redirect the standard out stream to a on-disk file when starting the application like so:

```
$ go run ./cmd/web >> /tmp/web.log
```

> Note: Using the double arrow >> will append to an existing file, instead of truncating it when starting the application.

# Concurrent logging

Custom loggers created by slog.New() are concurrency-safe. You can share a single logger