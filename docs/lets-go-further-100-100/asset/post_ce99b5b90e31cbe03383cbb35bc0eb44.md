
## The SetConnMaxLifetime method

The `SetConnMaxLifetime()` method sets the `ConnMaxLifetime` limit — the maximum length of time that a connection can be reused for. By default, there’s no maximum lifetime and connections will be reused forever.

If we set `ConnMaxLifetime` to one hour, for example, it means that all connections will be marked as ‘expired’ one hour after they were first created, and cannot be reused after they’ve expired. But note:

- This doesn’t guarantee that a connection will exist in the pool for a whole hour; it’s possible that a connection will become unusable for some reason and be automatically closed before then.
- A connection can still be in use more than one hour after being created — it just cannot *start* to be reused after that time.
- This isn’t an idle timeout. The connection will expire one hour after it was first created — not one hour after it last became idle.
- Once every second Go runs a background cleanup operation to remove expired connections from the pool.

In theory, leaving `ConnMaxLifetime` unlimited (or setting a long lifetime) will help performance because it makes it less likely that new connections will need to be created from scratch. But in certain situations, it can be useful to enforce a shorter lifetime. For example:

- If your SQL database enforces a maximum lifetime on connections, it makes sense to set `ConnMaxLifetime` to a slightly shorter value.
- To help facilitate swapping databases gracefully behind a load balancer.

If you do decide to set a `ConnMaxLifetime` on your pool, it’s important to bear in mind the frequency at which connections will expire (and subsequently be recreated). For example, if you have 100 open connections in the pool and a `ConnMaxLifetime` of 1 minute, then your application can potentially kill and recreate up to 1.67 connections (on average) every second. You don’t want the frequency to be so great that it ultimately hinders performance.

## The SetConnMaxIdleTime method

The `SetConnMaxIdleTime()` method (which was introduced in Go 1.15) sets the `ConnMaxIdleTime` limit. This works in a very similar way to `ConnMaxLifetime`, except it sets the maximum length of time that a connection can be *idle* for before it is marked as expired. By default there’s no limit.

If we set `ConnMaxIdleTime` to 1 hour, for example, any connections that have sat idle in the pool for 1 hour since last being used will be marked as expired and removed by the background cleanup operation.

This setting is really useful because it means that we can set a relatively high limit on the number of idle connections in the pool, but periodically free-up resources by removing any idle connections that we know aren’t really being used anymore.

## Putting it into practice

So that’s a lot of information to take in… and what does it mean in practice? Let’s summarize all the above into some actionable points.

- 1. As a rule of thumb, you should explicitly set a `MaxOpenConns` value. This should be comfortably below any hard limits on the number of connections imposed by your database and infrastructure, and you may also want to consider keeping it fairly low to act as a rudimentary throttle.

For this project we’ll set a `MaxOpenConns` limit of 25 connections. I’ve found this to be a reasonable starting point for small-to-medium web applications and APIs, but ideally you should tweak this value for your hardware depending on the results of benchmarking and load-testing.

- 2. In general, higher `MaxOpenConns` and `MaxIdleConns` values will lead to better performance. But the returns are diminishing, and you should be aware that having a too-large idle connection pool (with connections that are not frequently re-used) can actually lead to reduced performance and unnecessary resource consumption.

Because `MaxIdleConns` should always be less than or equal to `MaxOpenConns`, we’ll also limit `MaxIdleConns` to 25 connections for this project.

- 3. To mitigate the risk from point 2 above, you should generally set a `ConnMaxIdleTime` value to remove idle connections that haven’t been used for a long time. In this project we’ll set a `ConnMaxIdleTime` duration of 15 minutes.

- 4. It’s probably OK to leave `ConnMaxLifetime` as unlimited, unless your database imposes a hard limit on connection lifetime, or you need it specifically to facilitate something like gracefully swapping databases. Neither of those things apply in this project, so we’ll leave this as the default unlimited setting.

## Configuring the connection pool

Rather than hard-coding these settings, lets update the `cmd/api/main.go` file to accept them as command line flags.

The command-line flag for the `ConnMaxIdleTime` value is particularly interesting, because we want it to convey a *duration of time* which we ultimately need to convert to a Go `time.Duration` type. There are a couple of options here:

- 1. We could use an integer to represent the number of seconds (or minutes) and convert this to a `time.Duration`.
- 2. We could use a string representing the duration — like "5s" (5 seconds) or "10m" (10 minutes) — and then parse it using the `time.ParseDuration()` function.

Both approaches would work fine, but we’ll go with option 2 in this project. Go ahead and update the `cmd/api/main.go` file as follows:

File: cmd/api/main.go

```go
package main

...

// Add maxOpenConns, maxIdleConns and maxIdleTime fields to hold the
// configuration
// settings for the connection pool.
type config struct {
    port int
    env  string
    db   struct {
        dsn          string
        maxOpenConns int
        maxIdleConns int
        maxIdleTime  string
    }
}

...

func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    // Read the connection pool settings from command-line flags into the config struct.
    // Notice the default values that we're using?
    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.Parse()

    ...
}

func openDB(cfg config) (*sql.DB, error) {
    db, err := sql.Open("postgres", cfg.db.dsn)
    if err != nil {
        return nil, err
    }

    // Set the maximum number of open (in-use + idle) connections in the
pool. Note that
    // passing a value less than or equal to 0 will mean there is no limit.
    db.SetMaxOpenConns(cfg.db.maxOpenConns)

    // Set the maximum number of idle connections in the pool. Again, passing
a value
    // less than or equal to 0 will mean there is no limit.
    db.SetMaxIdleConns(cfg.db.maxIdleConns)

    // Use the time.ParseDuration() function to convert the idle timeout
duration string
    // to a time.Duration type.
    duration, err := time.ParseDuration(cfg.db.maxIdleTime)
    if err != nil {
        return nil, err
    }

    // Set the maximum idle timeout.
    db.SetConnMaxIdleTime(duration)

    ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
    defer cancel()

err = db.PingContext(ctx)
if err != nil {
    return nil, err
}

return db, nil
}
```

If you go ahead and run the application again now, everything should still work correctly. You won’t really notice any changes, and there’s not much we can do to demonstrate the impact of these settings at this point.

But later in the book we’ll do a bit of load testing, and explain how to monitor the state of the connection pool in real-time using the db.Stats() method. At that point, you’ll be able to see some of the behavior that we’ve talked about in this chapter in action.
