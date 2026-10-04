These arguments are used to fill the query string. Observe that the main difference between the create_table and the insert_rows functions is that the second one uses the Result value returned from the query. If we get the same value when creating the table, this will be set to zero because it does not affect any existing row.

# Example 18.2: Modifying data statements (excerpt).

```
35
36 const (
37 US_TABLE='CREATE TABLE users (
38 name varchar(250) PRIMARY KEY,
39 email varchar(250)
40 )\)
41 USERS_INSERT="INSERT INTO users (name, email) VALUES(?,?)"
42 )
43
44 func create_table(db *sql.DB) {
45 ctx := context.Background()
46 err := db.ExecContext(ctx, USERS_TABLE)
47 if err != nil {
48 panic(err)
49 }
50\51\52
53 func insert_rows(db *sql.DB) {
54 ctx := context.Background()
55 result, err := db.ExecContext(ctx, USERS_INSERT,
56 "John","john@gmail.com"
57 if err != nil {
58 panic(err)
59 }
60 lastUserID, err := result.LastInsertId()
61 if err != nil {
62 panic(err)
63 }
64 numRows, err := result.RowsAffected()
65 if err != nil {
66 panic(err)
67 }
68 fmt.Printf("Row ID: %d, Rows: %d\n", lastUserID, numRows)
69 }
```

| Database responds |
| Row ID: 1, Rows: |
| 1 |

The query syntax may vary depending on the target database. For example the insert query used in the example has been written differently for MySQL, PostgreSQL, and Oracle.

+   - MySQL: INSERT INTO users (name, email)VALUES(?,?)
- PostgreSQL: INSERT INTO users (name, email)VALUES($val1,$val2)
- Oracle: INSERT INTO users (name, email)VALUES(:val1,:val2)