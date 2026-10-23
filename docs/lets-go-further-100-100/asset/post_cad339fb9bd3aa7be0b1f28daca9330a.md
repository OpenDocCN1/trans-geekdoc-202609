
Chapter 10.1.

## Structured JSON Log Entries

At the moment, all of our log entries are simple free-form messages prefixed by the current date and time, written to the *standard out* stream. A good example of these are the log entries that we see when we start the API:

```
$ go run ./cmd/api
2021/04/09 19:43:31 database connection pool established
2021/04/09 19:43:31 starting development server on :4000
```

For many applications this simple style of logging will be *good enough*, and there’s no need to introduce additional complexity to your project.

But for applications which do a lot of logging, it can often be useful to enforce a consistent structure and format for your log entries. This can help make it easier to distinguish between different types of log entry (like *informational* and *error* entries), easier to search and filter log entries, and simpler to integrate your logs with third-party analysis and monitoring systems.

So in this chapter we’re going demonstrate how to adapt our application so that log entries are written in a structured JSON format, similar to this:

```
{"level":"INFO","time":"2020-12-16T10:53:35Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

Essentially, each log entry will be a single JSON object containing the following key/value pairs:

| Key | Description |
|---|---|
| level | A code indicating the severity of the log entry. In this project we will use the following three severity levels, ordered from least to most severe:
- INFO (least severe)
- ERROR
- FATAL (most severe) |
| time | The UTC time that the log entry was made with second precision. |
| message | A string containing the free-text information or error message. |
| properties | Any additional information relevant to the log entry in string key/value pairs (optional). |
| trace | A stack trace for debugging purposes (optional). |

## Creating a custom logger

To implement this in our API, we're going to create our own custom Logger type which writes structured log entries in JSON format.

We'll implement some convenience methods on Logger, such as PrintInfo() and PrintError(), in order to make it easy to write log entries with a specific level from our application in a single command. And we’ll also design the logger so that only entries at or above a certain *minimum severity level* are actually logged — so if you only want to record `ERROR` and `FATAL` messages (and not `INFO` messages), then that is easy to do.

If you’re following along, go ahead and create a new `internal/jsonlog` package like so:

```
$ mkdir internal/jsonlog
$ touch internal/jsonlog/jsonlog.go
```

And then add the following code:

```
File: internal/jsonlog/jsonlog.go

package jsonlog

import (
    "encoding/json"
    "io"
    "os"
    "runtime/debug"
    "sync"
    "time"
)

// Define a Level type to represent the severity level for a log entry.
type Level int8

// Initialize constants which represent a specific severity level. We use the
// iota keyword as a shortcut to assign successive integer values to the constants.
const (
    LevelInfo  Level = iota // Has the value 0.
    LevelError              // Has the value 1.
    LevelFatal              // Has the value 2.
    LevelOff                // Has the value 3.
)

// Return a human-friendly string for the severity level.
func (l Level) String() string {
    switch l {
    case LevelInfo:
        return "INFO"
    case LevelError:
        return "ERROR"
    case LevelFatal:
        return "FATAL"
    default:
        return ""
    }
}

// Define a custom Logger type. This holds the output destination that the log entries
// will be written to, the minimum severity level that log entries will be written for,
// plus a mutex for coordinating the writes.
type Logger struct {
    out      io.Writer
    minLevel Level
    mu       sync.Mutex
}

// Return a new Logger instance which writes log entries at or above a minimum severity
// level to a specific output destination.
func New(out io.Writer, minLevel Level) *Logger {
    return &Logger{
        out:      out,
        minLevel: minLevel,
    }
}

// Declare some helper methods for writing log entries at the different
// levels. Notice
// that these all accept a map as the second parameter which can contain any
// arbitrary
// 'properties' that you want to appear in the log entry.
func (l *Logger) PrintInfo(message string, properties map[string]string) {
    l.print(LevelInfo, message, properties)
}

func (l *Logger) PrintError(err error, properties map[string]string) {
    l.print(LevelError, err.Error(), properties)
}

func (l *Logger) PrintFatal(err error, properties map[string]string) {
    l.print(LevelFatal, err.Error(), properties)
    os.Exit(1) // For entries at the FATAL level, we also terminate the
application.
}

// Print is an internal method for writing the log entry.
func (l *Logger) print(level Level, message string, properties map[string]string) (int, error) {
    // If the severity level of the log entry is below the minimum severity
    // for the
    // logger, then return with no further action.
    if level < l.minLevel {
        return 0, nil
    }

    // Declare an anonymous struct holding the data for the log entry.
    aux := struct {
        Level   string        `json:"level"`
        Time    string        `json:"time"`
```

```
// We also implement a Write() method on our Logger type so that it satisfies
// the
// io.Writer interface. This writes a log entry at the ERROR level with no
// additional
// properties.
func (l *Logger) Write(message []byte) (n int, err error) {
    return l.print(LevelError, string(message), nil)
}
```

**Note:** If you want, you could extend this code to support additional severity levels such as `DEBUG` and `WARNING`.

Essentially, our `Logger` type is a fairly thin wrapper around an `io.Writer`. We have some helper methods like `PrintInfo()` and `PrintError()` which accept some data for the log entry, encode this data to JSON, and then write it to the `io.Writer`.

The two most interesting things to point out in this code are our use of the `iota` enumerator to create the log levels and a `sync.Mutex` to coordinate the writes.

You can use `iota` to easily assign successive integer values to a set of integer *constants*. It starts at zero, and increments by 1 for every constant declaration, resetting to 0 when the word `const` appears in the code again. The way that we’ve used this means that each of our severity levels has an integer value, with the *more severe levels having a higher value*.

// Initialize a new jsonlog.Logger which writes any messages *at or
above* the INFO
    // severity level to the standard out stream.
    logger := jsonlog.New(os.Stdout, jsonlog.LevelInfo)

    db, err := openDB(cfg)
    if err != nil {
        // Use the PrintFatal() method to write a log entry containing the
        error at the
            // FATAL level and exit. We have no additional properties to include
        in the log
            // entry, so we pass nil as the second parameter.
        logger.PrintFatal(err, nil)
    }

    defer db.Close()
    // Likewise use the PrintInfo() method to write a message at the INFO
    level.
    logger.PrintInfo("database connection pool established", nil)

    app := &application{
        config: cfg,
        logger: logger,
        models: data.NewModels(db),
    }

    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", cfg.port),
        Handler:      app.routes(),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }

    // Again, we use the PrintInfo() method to write a "starting server"
    message at the
        // INFO level. But this time we pass a map containing additional
    properties (the
