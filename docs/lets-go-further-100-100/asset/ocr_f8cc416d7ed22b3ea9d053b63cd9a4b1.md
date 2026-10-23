```
$ pkill -SIGTERM api
```

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:42:46Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:42:46Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:42:512","message":"caught signal","properties":{"signal":"terminated"}}
```

In contrast, sending a `SIGKILL` or `SIGQUIT` signal will continue to cause the application to exit immediately *without the signal being caught*, so you shouldn't see a `caught signal` message in the logs. For example, if you restart the application and issue a `SIGKILL`...

```
$ pkill -SIGKILL api
```

The application should be terminated immediately, and the logs will look like this:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"starting
```