```
package main

import (
    "Context"
    "database/sql"
    "fmt"
    "time"
    "github.com/mattn/go-sqlite3"
)

func main() {
    db, err := sql.Open("sqlite3", "/tmp/example.db")

    if err != nil {
        fmt.Println(err)
        panic(err)
    }
    defer db.Close()
    db.SetMaxIdleLifetime(time.Minute * 3)
    db.SetMaxOpenConns(10)
    db.SetMaxIdleConns(10)

    ctx := context.Background()
    if err := db.PingContext(ctx); err == nil {
        fmt.Println("Database responds")
    } else {
        fmt.Println("Database does not respond")
        panic(err)
    }
}
```

![](bbox=[0.775, 0.125, 0.866, 0.199])

The instance can be configured with some parameters such as the maximum connection lifetime, the maximum number of open connections or the maximum number of idle connections. ... (truncated)

# 18.1.2 Modifying data statements

The Go standard library provides queries that return rows of data and queries that modify the database. When modifying the database we do not expect any row to be returned. Methods Exec and ExecContext execute queries to create, update, or insert new rows into a table. They return a Result which contains the ID of the latest inserted row if it applies, and the number of rows affected by update, insert, or delete operations. Not every database may provide these values. Check out the documentation before proceeding to operate with these values.

Example 18.2 assumes an DB connection and uses it to create a table and insert a new entry. The Exec and ExecContext methods receive a query in a string and one or several arguments.