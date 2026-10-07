Here is our Go struct for rows in the City table:

```
type City struct {
    Name string
    CountryCode string
    District string
    Population uint32
}
```

Next, let's have a variable in which we store a handle to our database when we're connected:

```
var database *sql.DB
```

Finally, we're ready to connect to the database. We build up the connection string by serializing the server host, port number, initial database, and password strings.

Next, we attempt to connect by calling the database/sql.Open method, passing in the type of driver and the connection string:

```
dbConn := fmt.Sprintf("%s:%s@tcp(%s)/%s", dbUser, dbPass, dbHost, dbDatabase)
db, err := sql.Open("mysql", dbConn)
```

This returns an instance of sql.DB (about which we will have more to say later).

The full code is here in Code Listing 7.

# Code Listing 7: Connecting to the Database

```
package main

import (
    "database/sql"
    "log"
    _ "github.com/go-sql-driver/mysql"
)

var database *sql.DB

func main() {
    db, err := sql.Open("mysql", "root:password@tcp(127.0.0.1:3306)/world")
    if err != nil {
        log.Println("Could not connect!")
    }
    database = db
    log.Println("Connected.")
}
```