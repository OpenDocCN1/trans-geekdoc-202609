# 8.3. USING POSTGRES WITH GO AND RAW SQL

that you don't call it before you are ready to move on!

# 8.3.6 Writing a relational record

In this section we are going to create an order for one of our existing users. The code here really isn’t any different than creating records like we did before, so we aren’t going to spend time talking about the code.

Instead you need to run the code in Listing 8.18 so that you have a few orders in your database for the next section where we will be doing some relational queries.

```
Listing 8.18: Creating orders to query
package main

import (
	"database/sql"
	"fmt"
	"github.com/lib/pq"
)

const {
	host = "localhost"
	port = 5432
	user = "postgres"
	password = "your-password"
	dbname = "lensocked_dev"
}

func main() {
	pqlInfo := fmt.Sprintf("host=%s port=%d user=%s dbname=%s sslmode=disable",
	host, port, user, password, dbname)
	db, err := sql.Open("postgres", psqlInfo)
	if err != nil {
		panic(err)
	}

var id int
for i := 1; i < 6; i++ {
		// Create some fake data
```