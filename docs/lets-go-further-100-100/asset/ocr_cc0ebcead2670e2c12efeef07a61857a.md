```
config config
logger *jsonlog.Logger
models data.Models
mailer mailer.Mailer
wg     sync.WaitGroup
}
...

```

Next let's head to the cmd/api/helpers.go file and update the app.background() helper so that the sync.WaitGroup counter is incremented each time before we launch a background goroutine, and then decremented when it completes.

Like this:

```
File: cmd/api/helpers.go

package main

...

func (app *application) background(fn func()) {
    // Increment the WaitGroup counter.
    app.wg.Add(1)

    // Launch the background goroutine.
    go func() {
        // Use defer to decrement the WaitGroup counter before the goroutine returns.
        defer app.wg.Done()

        defer func() {
```