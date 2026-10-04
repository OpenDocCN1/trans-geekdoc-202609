```
}
fmt.Println("Found:", id, name, email)
)
}
```

As a final note, observe that we have inserted the records in the reverse order that they are retrieved. This occurs because Cassandra sorts the records using the primary key.

# 19.1.6 User Defined Types

User-defined types (UDTs) can be expressed using structs and tag fields. Example 19.14 defines a laptop UDT to be incorporated into the users table. The Laptop struct defines the field of the UDT we created. GoCQL uses field tags like cql:"sn" to indicate that struct field corresponds to variable sn in the UDT. The Scan method can populate this struct without additional guidance as shown in the code.

Example 19.14: GoCQL UDT struct definition and query.

```
package main

import (
	"context"
	"fmt"
	"github.com/gocql/gocql"
	"time"
)

const LAPTOP_TYPE = 'CREATE TYPE example.Laptop {
	sn int,
	model text,
	memory int
}

const USERS_TABLE = 'CREATE TABLE example.users (
	user_id int PRIMARY KEY,
	name text,
	email text,
	laptop frozen<Laptop>'

const INSERT = 'INSERT INTO users.users (
	user_id, name, email, Laptop) VALUES (?,?,?,?)'

type type struct struct {
	sn string `cql:"sn""
	model string `cql:"model""
	memory string `cql:"memory""
}

func main() {
	cluster := gocql.NewCluster("127.0.0.1:9042")
	cluster.Keyspace = "example"
```

![](bbox=[0.725, 0.435, 0.882, 0.473])