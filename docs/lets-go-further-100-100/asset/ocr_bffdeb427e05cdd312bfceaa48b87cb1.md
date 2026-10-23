```
}

func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
    flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.Parse()

    logger := log.New(os.Stdout, "", log.Ldate|log.Ltime)

    db, err := openDB(cfg)
    if err != nil {
        logger.Fatal(err)
    }

    defer db.Close()
    logger.Printf("database connection pool established")

    // Use the data.NewModels() function to initialize a Models struct,
    passing in the
    // connection pool as a parameter.
    app := &application{
        config: cfg,
        logger: logger,
        models: data.NewModels(db),
    }
}
```