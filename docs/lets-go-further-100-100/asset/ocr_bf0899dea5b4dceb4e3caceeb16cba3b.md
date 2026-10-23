```
```go
// At this point we know that the graceful shutdown completed
successfully and we
    // log a "stopped server" message.
    app.logger.PrintInfo("stopped server", map[string]string{
        "addr": srv.Addr,
    })

    return nil
}
```
```

At first glance this code might seem a bit complex, but at a high-level what it’s doing can be summarized very simply: *when we receive a `SIGINT` or `SIGTERM` signal, we instruct our server to stop accepting any new HTTP requests, and give any in-flight requests a ‘grace period’ of 5 seconds to complete before the application is terminated.*

But there are a couple of important details to be aware of:

+   - The `Shutdown()` method does not wait for any background tasks to complete, nor does it close hijacked long-lived connections like WebSockets. Instead, you will need to implement your own logic to coordinate a graceful shutdown of these things. We’ll look at some techniques for doing this later in the book.
+   - There is an open bug which effectively limits the grace period to 5 seconds for HTTP/2 connections. HTTP/2 is automatically supported for HTTPS connections in Go, so if you’re planning to handle HTTPS connections from your Go application then (for now) it is sensible to use a sub 5-second grace period for your