```
// Call Shutdown() on our server, passing in the context we just
made.
    // Shutdown() will return nil if the graceful shutdown was
successful, or an
    // error (which may happen because of a problem closing the
listeners, or
    // because the shutdown didn't complete before the 5-second context
deadline is
    // hit). We relay this return value to the shutdownError channel.
    shutdownError <- srv.Shutdown(ctx)
}()

app.logger.PrintInfo("starting server", map[string]string{
    "addr": srv.Addr,
    "env":  app.config.env,
})

    // Calling Shutdown() on our server will cause ListenAndServe() to
immediately
    // return a http.ErrServerClosed error. So if we see this error, it is
actually a
    // good thing and an indication that the graceful shutdown has started.
So we check
    // specifically for this, only returning the error if it is NOT
http.ErrServerClosed.
    err := srv.ListenAndServe()
    if !errors.Is(err, http.ErrServerClosed) {
        return err
    }

    // Otherwise, we wait to receive the return value from Shutdown() on the
    // shutdownError channel. If return value is an error, we know that there
was a
    // problem with the graceful shutdown and we return the error.
    err = <-shutdownError
    if err != nil {
        return err
    }
```