haven’t been used for a long time. In this project we’ll set a `ConnMaxIdleTime` duration of 15 minutes.

+   4. It’s probably OK to leave `ConnMaxLifetime` as unlimited, unless your database imposes a hard limit on connection lifetime, or you need it specifically to facilitate something like gracefully swapping databases. Neither of those things apply in this project, so we’ll leave this as the default unlimited setting.

# Configuring the connection pool

Rather than hard-coding these settings, lets update the `cmd/api/main.go` file to accept them as command line flags.

The command-line flag for the `ConnMaxIdleTime` value is particularly interesting, because we want it to convey a *duration of time* which we ultimately need to convert to a Go `time.Duration` type. There are a couple of options here:

+   1. We could use an integer to represent the number of seconds (or minutes) and convert this to a `time.Duration`.
+   2. We could use a string representing the duration — like "5s" (5 seconds) or "10m" (10 minutes) — and then parse it using the `time.ParseDuration()` function.

Both approaches would work fine, but we’ll go with option 2 in this project. Go ahead and update the `cmd/api/main.go` file as follows: