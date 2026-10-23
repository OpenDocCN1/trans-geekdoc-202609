One thing to point out — by default `make` echoes commands in the terminal output. We can see that in the code above where the first line in the output is the echoed command `go run ./cmd/api`. If you want, it’s possible to suppress commands from being echoed by prefixing them with the `@` character.

# Environment variables

When we execute a `make` rule, every environment variable that is available to `make` when it starts is transformed into a *make variable* with the same name and value. We can then access these variables using the syntax `${VARIABLE_NAME}` in our makefile.

To illustrate this, let’s create two additional rules — a `psql` rule for connecting to our database and an `up` rule to execute our database migrations. If you’ve been following along, both of these rules will need access to the database DSN value from your `GREENLIGHT_DB_DSN` environment variable.

Go ahead and update your `Makefile` to include these two new rules like so:

```
File: Makefile

run:
    go run ./cmd/api

psql:
    psql ${GREENLIGHT_DB_DSN}
```