```
flag.IntVar(&cfg.port, "port", 4000, "API server port")
flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

// Use the value of the GREENLIGHT_DB_DSN environment variable as the default value
// for our db-dsn command-line flag.
flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

flag.Parse()

...
}
```

If you restart the application again now, you should find that it compiles correctly and works just like before.

You can also try specifying the -help flag when running the application. This should output the descriptive text and default values for our three command-line flags, including the DSN value pulled through from the environment variable. Similar to this:

```
$ go run ./cmd/api -help
Usage of /tmp/go-build417842398/b001/exe/api:
  -db-dsn string
      PostgreSQL DSN (default
"postgres://greenlight:pa55word@localhost/greenlight")
  -env string
      Environment (development|staging|production) (default "development")
  -port int
      API server port (default 4000)
```