Create db.go. The code is largely same as the previous chapter. I’ve just changed the input to a Todo struct, instead of a plain string.

```
```go
package function

import (
	"database/sql"
	"fmt"

	_ "github.com/lib/pq"
)

func connect(user, password, host, dbName, sslMode string, port int) (*sql.DB, error) {
	connStr := "postgres://" + user + ":" + password + "@" + host + ":" + fmt.Sprintf("%d",
		port) + "/" + dbName + "?sslmode=" + sslMode

	db, err := sql.Open("postgres", connStr)
	if err != nil {
		return nil, err
	}

	err = db.Ping()
	if err != nil {
		return nil, err
	}

	return db, nil
}

func create(db *sql.DB, todo Todo) error {
	if len(todo.Description) == 0 {
		return fmt.Errorf("description is required")
	}

	res, err := db.Query(`INSERT INTO
		todo
		(id, description, created_date)
		VALUES
		(DEFAULT, $1, now());`,
		todo.Description)

	if err != nil {
		return err
	}

	defer res.Close()
	return nil
}

func list(db *sql.DB) ([]Todo, error) {
	rows, err := db.Query(`SELECT
		id,
		description,
		created_date,
		completed_date
```
```