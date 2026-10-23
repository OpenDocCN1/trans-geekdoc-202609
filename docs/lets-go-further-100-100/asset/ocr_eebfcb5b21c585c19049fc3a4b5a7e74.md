# Additional Information

# $N notation

A nice feature of the PostgreSQL placeholder parameter $N notation is that you can use the same parameter value in multiple places in your SQL statement. For example, it's perfectly acceptable to write code like this:

```
// This SQL statement uses the $1 parameter twice, and the value `123` will
be used in
// both locations where $1 appears.
stmt := "UPDATE foo SET bar = $1 + $2 WHERE bar = $1"
err := db.Exec(stmt, 123, 456)
if err != nil {
...
}
```

# Executing multiple statements

Occasionally you might find yourself in the position where you want to execute more than one SQL statement in the same database call, like this:

```
stmt := `
    UPDATE foo SET bar = true;
    UPDATE foo SET baz = false;`
```