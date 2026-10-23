
Chapter 12.1.

## Sending Shutdown Signals

When our application is running, we can terminate it at any time by sending it a specific signal. A common way to do this, which you've probably been using, is by pressing `Ctrl+C` on your keyboard to send an *interrupt* signal — also known as a `SIGINT`.

But this isn't the only type of signal which can stop our application. Some of the other common ones are:

| Signal | Description | Keyboard shortcut | Catchable |
|---|---|---|---|
| `SIGINT` | Interrupt from keyboard | `Ctrl+C` | Yes |
| `SIGQUIT` | Quit from keyboard | `Ctrl+\` | Yes |
| `SIGKILL` | Kill process (terminate immediately) | - | No |
| `SIGTERM` | Terminate process in orderly manner | - | Yes |

It's important to explain upfront that some signals are *catchable* and others are not. Catchable signals can be intercepted by our application and either ignored, or used to trigger a certain action (such as a graceful shutdown). Other signals, like `SIGKILL`, are not catchable and cannot be intercepted.

Let’s take a quick look at these signals in action. If you’re following along, go ahead and start the API application with the same `go run ./cmd/api` command as normal:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

Doing this should start a process with the name `api` on your machine. You can use the `pgrep` command to verify that this process exists, like so:

```
$ pgrep -l api
4414 api
```

In my case, I can see that the `api` process is running and has the *process ID* `4414` (your process ID will most likely be different).

Once that’s confirmed, go ahead and try sending a `SIGKILL` signal to the `api` process using the `pkill` command like so:

```
$ pkill -SIGKILL api
```

If you go back to the terminal window that is running the API application, you should see that it has been terminated and the final line in the output stream is signal: killed. Similar to this:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
signal: killed
```

Feel free to repeat the same process, but sending a SIGTERM signal instead:

```
$ pkill -SIGTERM api
```

This time you should see the line signal: terminated at the end of the output, like so:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T07:35:54Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T07:35:54Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
signal: terminated
```

We can see that these signals are effective in terminating our application — but the problem we have is that they all cause our application to exit *immediately*.

Fortunately, Go provides tools in the `os/signals` package that we can use to intercept catchable signals and trigger a graceful shutdown of our application. We’ll look at how to do that in the next chapter.

```
defer db.Close()

logger.PrintInfo("database connection pool established", nil)

app := &application{
    config: cfg,
    logger: logger,
    models: data.NewModels(db),
}

// Call app.serve() to start the server.
err = app.serve()
if err != nil {
    logger.PrintFatal(err, nil)
}
}
...
```

## Catching SIGINT and SIGTERM signals

The next thing that we want to do is update our application so that it ‘catches’ any SIGINT and SIGTERM signals. As we mentioned above, SIGKILL signals are not catchable (and will always cause the application to terminate immediately), and we’ll leave SIGQUIT with its default behavior (as it’s handy if you want to execute a non-graceful shutdown via a keyboard shortcut).

To catch the signals, we’ll need to spin up a background goroutine which runs for the lifetime of our application. In this background goroutine, we can use the signal.Notify() function to listen for specific signals and relay them to a channel for further processing.

I'll demonstrate.

Open up the cmd/api/server.go file and update it like so:

```
File: cmd/api/server.go

package main

import (
    "fmt"
    "net/http"
    "os"      // New import
    "os/signal" // New import
    "syscall"  // New import
    "time"
)

func (app *application) serve() error {
    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", app.config.port),
        Handler:      app.routes(),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }

    // Start a background goroutine.
    go func() {
        // Create a quit channel which carries os.Signal values.
        quit := make(chan os.Signal, 1)

        // Use signal.Notify() to listen for incoming SIGINT and SIGTERM signals and
```

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

```
$ pkill -SIGTERM api
```

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:42:46Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:42:46Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:42:51Z","message":"caught signal","properties":{"signal":"terminated"}}
```

In contrast, sending a `SIGKILL` or `SIGQUIT` signal will continue to cause the application to exit immediately *without the signal being caught*, so you shouldn't see a `caught signal` message in the logs. For example, if you restart the application and issue a `SIGKILL`...

```
$ pkill -SIGKILL api
```

The application should be terminated immediately, and the logs will look like this:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"starting
```

## Executing the Shutdown

Intercepting the signals is all well and good, but it’s not very useful until we do something with them! In this chapter, we’re going to update our application so that the `SIGINT` and `SIGTERM` signals we intercept trigger a graceful shutdown of our API.

Specifically, after receiving one of these signals we will call the `Shutdown()` method on our HTTP server. The official documentation describes this as follows:

> > *Shutdown gracefully shuts down the server without interrupting any active connections. Shutdown works by first closing all open listeners, then closing all idle connections, and then waiting indefinitely for connections to return to idle and then shut down.*

The pattern to implement this in practice is difficult to describe with words, so let’s jump into the code and talk through the details as we go along.

```
File: cmd/api/server.go

```go
package main

import (
    "context" // New import
)
```
