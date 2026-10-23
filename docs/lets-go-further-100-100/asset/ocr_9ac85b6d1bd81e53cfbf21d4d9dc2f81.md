```
```go
import (
    "context"
    "database/sql"
    "flag"
    "os"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/jsonlog"
    "greenlight.alexedwards.net/internal/mailer" // New import

    _ "github.com/lib/pq"
)

const version = "1.0.0"

// Update the config struct to hold the SMTP server settings.
type config struct {
    port int
    env  string
    db   struct {
        dsn          string
        maxOpenConns int
        maxIdleConns int
        maxIdleTime  string
    }
    limiter struct {
        enabled bool
        rps     float64
        burst   int
    }
    smtp struct {
        host     string
        port     int
        username string
        password string
        sender   string
    }
}
```
```