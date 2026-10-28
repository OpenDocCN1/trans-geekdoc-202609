# How to create a user with limited privileges on a single table

```
```sql
GRANT SELECT
ON my_guitar_shop1.products
TO mgs_tester@localhost
IDENTIFIED BY 'pa55word'
```
```

# How to create a user with limited privileges on all tables in a database

```
```sql
GRANT SELECT, INSERT, DELETE, UPDATE
ON my_guitar_shop1.*
TO mgs_user@localhost
IDENTIFIED BY 'pa55word'
```
```

# Common privileges

| Privilege | Description |
|---|---|
| `SELECT` | Lets the user select data. |
| `UPDATE` | Lets the user update data. |
| `INSERT` | Lets the user insert data. |
| `DELETE` | Lets the user delete data. |
| `CREATE TABLE` | Lets the user create a table. |
| `DROP TABLE` | Lets the user drop a table. |

# The SQL tab for mgs_tester after an UPDATE statement failed

![](bbox=[0.07, 0.497, 0.709, 0.79])

# Description

+   - You should restrict the privileges for most users of a database to prevent the user from accidentally or intentionally damaging the database.
+   - You can use the GRANT statement to create a user, specify a password for that user, and grant privileges to the user.
+   - For more on creating users and granting privileges, see chapter 17.

Figure 3-13   How to create users with limited privileges