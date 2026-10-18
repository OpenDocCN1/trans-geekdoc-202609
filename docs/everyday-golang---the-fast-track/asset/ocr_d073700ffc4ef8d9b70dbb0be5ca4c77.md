```
```go
return nil, err
}

return db, nil
}
```
```

Here’s how you can perform an insert. Note that the $1 is substituted for `todo` string. By using this syntax instead of `fmt.Sprintf` or string concatenation, we get some level of protection against SQL injection attacks where a user may insert additional SQL statements in a value.

```
```go
func create(db *sql.DB, todo string) error {
    res, err := db.Query(`INSERT INTO
        todo
        (id, description, created_date)
        VALUES
        (DEFAULT, $1, now());`,
        todo)
    if err != nil {
        return err
    }
    defer res.Close()
    return nil
}
```
```

The list function returns a slice of the Todo structs. You can use the same $1 technique to specify keys or sort orders for the SELECT statement.

Finally the Scan function is used to populate the values from the row into the type using the proper typing. See how we didn’t have to parse a date string into a `time.Time` for instance?

```
```go
func list(db *sql.DB) ([]Todo, error) {
    rows, err := db.Query(`SELECT
        id,
        description,
        created_date,
        completed_date
        FROM todo;`)

    if err != nil {
        return []Todo{},
            fmt.Errorf("unable to get from todo table: %w", err)
    }

    todos := []Todo{}
    defer rows.Close()
    for rows.Next() {
        result := Todo{}
        err := rows.Scan(&result.ID,
            &result.Description,
            &result.CreatedDate,
            &result.CompletedDate)
        if err != nil {
            return []Todo{}, fmt.Errorf("row scan error: %w", err)
        }
        todos = append(todos, result)
```
```