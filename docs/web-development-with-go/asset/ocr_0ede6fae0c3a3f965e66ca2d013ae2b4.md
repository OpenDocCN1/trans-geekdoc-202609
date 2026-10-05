# 8.3. USING POSTGRES WITH GO AND RAW SQL

### Listing 8.10: Connecting to Postgres with database/sql
```go
package main

import (
    "database/sql"
    "fmt"

    "github.com/lib/pq"
)

const (
    host = "localhost"
    port = "5432"
    user = "postgres"
    password = "your-password"
    dbname = "lenslocked_dev"
)

func main() {
    psqlInfo := fmt.Sprintf("host=%s port=%s user=%s dbname=%s sslmode=disable",
        host, port, user, dbname)
    db, err := sql.Open("postgres", psqlInfo)
    if err != nil {
        panic(err)
    }

    err = db.Ping()
    if err != nil {
        panic(err)
    }

    fmt.Println("Successfully connected!")
    db.Close()
}
```

Once your code is ready, give it a try. Change to the exp directory and then build and run your code.

### Listing 8.11: Running our code
```bash
cd exp
go run main.go
```

You should see the output Successfully connected! in your terminal