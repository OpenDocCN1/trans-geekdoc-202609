
```
$ go run ./cmd/web
time=2024-03-18T11:29:23.000+00:00 level=INFO msg="starting server" addr=:4000
time=2024-03-18T11:29:23.000+00:00 level=ERROR msg="listen tcp :4000: bind: address already in use"
exit status 1
```

This is looking pretty good. We can see that the two log entries contain different information, but are formatted in the same overall way.

The first log entry has the severity level=INFO and message msg="starting server", along with the additional addr=:4000 attribute. In contrast, we see that the second log entry has the severity level=ERROR, the msg value contains the content of the error message, and there are no additional attributes.

## Additional information

### Safer attributes

Let's say that you accidentally write some code where you forget to include either the key or value for an attribute. For example:

```
logger.Info("starting server", "addr") // Oops, the value for "addr" is missing
```

When this happens, the log entry will still be written but the attribute will have the key !BADKEY, like so:

```
time=2024-03-18T11:29:23.000+00:00 level=INFO msg="starting server" !BADKEY=addr
```

To avoid this happening and catch any problems at compile-time, you can use the slog.Any() function to create an attribute pair instead:

```
logger.Info("starting server", slog.Any("addr", ":4000"))
```

Or you can go even further and introduce some additional type safety by using the slog.String(), slog.Int(), slog.Bool(), slog.Time() and slog.Duration() functions to create attributes with a specific type of value.

```
logger.Info("starting server", slog.String("addr", ":4000"))
```

Whether you want to use these functions or not is up to you. The log/slog package is relatively new to Go (introduced in Go 1.21), and there isn't much in the way of established best-practices or conventions around using it yet. But the trade-off is straightforward... using functions like slog.String() to create attributes is more verbose, but safer in sense that it reduces the risk of bugs in your application.

## JSON formatted logs

The slog.NewTextHandler() function that we've used in this chapter creates a handler that writes plaintext log entries. But it's possible to create a handler that writes log entries as JSON objects instead using the slog.NewJSONHandler() function. Like so:

```
logger := slog.New(slog.NewJSONHandler(os.Stdout, nil))
```

When using the JSON handler, the log output will look similar to this:

```
{"time":"2024-03-18T11:29:23.000000000+00:00","level":"INFO","msg":"starting server","addr":":4000"}
{"time":"2024-03-18T11:29:23.000000000+00:00","level":"ERROR","msg":"listen tcp :4000: bind: address already in use"}
```

## Minimum log level

As we've mentioned a couple of times, the log/slog package supports four severity levels: Debug, Info, Warn and Error in that order. Debug is the least severe level, and Error is the most severe.

By default, the minimum log level for a structured logger is Info. That means that any log entries with a severity less than Info — i.e. Debug level entries — will be silently discarded.

You can use the slog.HandlerOptions struct to override this and set the minimum level to Debug (or any other level) if you want:

```
logger := slog.New(slog.NewTextHandler(os.Stdout, &slog.HandlerOptions{
Level: slog.LevelDebug,
}))
```

## Caller location

You can also customize the handler so that it includes the filename and line number of the calling source code in the log entries, like so:

```
logger := slog.New(slog.NewTextHandler(os.Stdout, &slog.HandlerOptions{
AddSource: true,
}))
```

The log entries will look similar to this, with the caller location recorded under the source key:

```
time=2024-03-18T11:29:23.000+00:00 level=INFO source=/home/alex/code/snippetbox/cmd/web/main.go:32 msg="starting server" addr
```

## Decoupled logging

In this chapter we've set up our structured logger to write entries to os.Stdout — the standard out stream.

The big benefit of writing log entries to os.Stdout is that your application and logging are decoupled. Your application itself isn't concerned with the routing or storage of the logs, and that can make it easier to manage the logs differently depending on the environment.

During development, it's easy to view the log output because the standard out stream is displayed in the terminal.

In staging or production environments, you can redirect the stream to a final destination for viewing and archival. This destination could be on-disk files, or a logging service such as Splunk. Either way, the final destination of the logs can be managed by your execution environment independently of the application.

For example, we could redirect the standard out stream to a on-disk file when starting the application like so:

```
$ go run ./cmd/web >> /tmp/web.log
```

> Note: Using the double arrow >> will append to an existing file, instead of truncating it when starting the application.

## Concurrent logging

Custom loggers created by slog.New() are concurrency-safe. You can share a single logger and use it across multiple goroutines and in your HTTP handlers without needing to worry about race conditions.

That said, if you have *multiple* structured loggers writing to the same destination then you need to be careful and ensure that the destination's underlying `Write()` method is also safe for concurrent use.

## Dependency injection

If you open up your handlers.go file you'll notice that the home handler function is still writing error messages using Go's standard logger, not the structured logger that we now want to be using.

```go
func home(w http.ResponseWriter, r *http.Request) {
	...

ts, err := template.ParseFiles(files...)
if err != nil {
	log.Print(err.Error()) // This isn't using our new structured logger.
	http.Error(w, "Internal Server Error", http.StatusInternalServerError)
	return
}

err = ts.ExecuteTemplate(w, "base", nil)
if err != nil {
	log.Print(err.Error()) // This isn't using our new structured logger.
	http.Error(w, "Internal Server Error", http.StatusInternalServerError)
}
}
```

This raises a good question: how can we make our new structured logger available to our home function from main()?

And this question generalizes further. Most web applications will have multiple dependencies that their handlers need to access, such as a database connection pool, centralized error handlers, and template caches. What we really want to answer is: how can we make any dependency available to our handlers?

There are a few different ways to do this, the simplest being to just put the dependencies in global variables. But in general, it is good practice to inject dependencies into your handlers. It makes your code more explicit, less error-prone, and easier to unit test than if you use global variables.

For applications where all your handlers are in the same package, like ours, a neat way to inject dependencies is to put them into a custom application struct, and then define your handler functions as methods against application.

I'll demonstrate.

First open your main.go file and create a new application struct like so:

```go
File: cmd/web/main.go

package main

import (
	"flag"
	"log/slog"
	"net/http"
	"os"
)

// Define an application struct to hold the application-wide dependencies for the
// web application. For now we'll only include the structured logger, but we'll
// add more to this as the build progresses.
type application struct {
	logger *slog.Logger
}

func main() {
	...
}
```

And then in the handlers.go file, we want to update the handler functions so that they become *methods against the application struct* and use the structured logger that it contains.

```go
File: cmd/web/handlers.go

package main

import (
	"fmt"
	"html/template"
	"net/http"
	"strconv"
)

// Change the signature of the home handler so it is defined as a method against
// *application.
func (app *application) home(w http.ResponseWriter, r *http.Request) {
	w.Header().Add("Server", "Go")

	files := []string{
		"./ui/html/base.tmpl",
		"./ui/html/partials/nav.tmpl",
		"./ui/html/pages/home.tmpl",
	}

ts, err := template.ParseFiles(files...)
	if err != nil {
		// Because the home handler is now a method against the application
		// struct it can access its fields, including the structured logger. We'll
		// use this to create a log entry at Error level containing the error
		// message, also including the request method and URI as attributes to
		// assist with debugging.
		app.logger.Error(err.Error(), "method", r.Method, "uri", r.URL.RequestURI())
		http.Error(w, "Internal Server Error", http.StatusInternalServerError)
		return
	}
}
```
