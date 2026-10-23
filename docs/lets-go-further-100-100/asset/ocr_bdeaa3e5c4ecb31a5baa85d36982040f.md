One thing I’d like to quickly emphasize about this: our `quit` channel is a `buffered channel` with size 1.

We need to use a buffered channel here because `signal.Notify()` `does not wait` for a receiver to be available when sending a signal to the `quit` channel. If we had used a regular (non-buffered) channel here instead, a signal could be ‘missed’ if our `quit` channel is not ready to receive at the exact moment that the signal is sent. By using a buffered channel, we avoid this problem and ensure that we never miss a signal.

OK, let’s try this out.

First, run the application and then press `Ctrl+C` on your keyboard to send a `SIGINT` signal. You should see a `"caught signal"` log entry with `"signal":"interrupt"` in the properties, similar to this:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:42:28Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:42:28Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
^C{"level":"INFO","time":"2021-04-11T10:42:29Z","message":"caught signal","properties":{"signal":"interrupt"}}
```

You can also restart the application and try sending a `SIGTERM` signal. This time the log entry properties should contain `"signal":"terminated"`, like so: