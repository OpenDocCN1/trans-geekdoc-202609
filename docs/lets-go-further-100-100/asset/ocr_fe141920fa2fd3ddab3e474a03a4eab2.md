Instead, we can update our makefile so that the DSN value from the `GREENLIGHT_DB_DSN` environment variable is passed in as part of the rule. If you’re following along, please go ahead and update the `run/api` rule as follows:

```
File: Makefile

...

## run/api: run the cmd/api application
.PHONY: run/api
run/api:
    go run ./cmd/api -db-dsn=${GREENLIGHT_DB_DSN}

...
```

This is a small change but a really nice one, because it means that the *default configuration values for our application no longer change depending on the operating environment*. The command-line flag values passed at runtime are the *sole* mechanism for configuring our application settings, and there are still no secrets hard-coded in our project files.

During development running our application remains nice and easy — all we need to do is type `make run/api`, like so:

```
$ make run/api
go run ./cmd/api -db-dsn=postgres://greenlight:pa55word@localhost/greenlight
```