```
Description: desc,
))
if db.Error != nil {
    panic(db.Error)
}
```

With these two pieces we are ready to put it all together and look up a user, then create several orders for that user. The final code can be found in Listing 8.35. You should update your exp/main.go file with this code and then run it to create a few orders to use in the next section.

# Listing 8.35: Creating the orders table

```
package main

import (
    "fmt"

    "github.com/jinzhu/gorm"
    "github.com/lib/pq"
)

const {
    host = "localhost"
    port = 5432
    user = "postgres"
    password = "your-password"
    dbname = "lenslocked_dev"
}

type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null;unique_index"`"
}

type Order struct {
    gorm.Model
    UserID uint
    Amount int
    Description string
}

func main() {
    psqlInfo := fmt.Sprintf("host=%s port=%d user=%s" +
```