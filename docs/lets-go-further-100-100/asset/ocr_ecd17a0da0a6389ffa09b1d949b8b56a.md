entries with a specific level from our application in a single command. And we’ll also design the logger so that only entries at or above a certain *minimum severity level* are actually logged — so if you only want to record `ERROR` and `FATAL` messages (and not `INFO` messages), then that is easy to do.

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
```