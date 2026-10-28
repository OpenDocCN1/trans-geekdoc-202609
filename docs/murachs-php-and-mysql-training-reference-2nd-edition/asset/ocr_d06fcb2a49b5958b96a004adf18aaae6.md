# The create_db.sql file

```
`C:\xampp\htdocs\book_apps\_create_db\create_db.sql`
```

# The databases that are created

| Database | Description |
|---|---|
| `my_guitar_shop1` | A simple database that's used for the applications in sections 1 and 2. |
| `my_guitar_shop2` | An expanded version of the database that is used for the applications in sections 3 and 4. |

# A user that's created

| User | Description |
|---|---|
| `mgs_user` | A user with privileges that allow only the use of SELECT, INSERT, UPDATE, and DELETE statements. This user is used for the database connections for most of the applications in the book. |

# How to create the databases and users for this book

+   1. Start phpMyAdmin as described in figure A-4.
+   2. Log in as the root user.
+   3. Click on the Import tab, click the Choose File button, and select the create_db.sql file shown above. Then, click the Go button.
+   4. If the script executes successfully, you can use the left column to view both databases. To do that, click the plus (+) sign to expand the “my” node, and click the plus (+) sign to expand the “guitar” node.

# How to restore the databases and users for this book

+   - Run the create_db.sql script again. This drops both databases and creates them again.

# Description

+   - If you have any problem following this procedure, chapter 3 provides a more detailed explanation of how to use phpMyAdmin to run scripts such as the create_db.sql script.

Figure A-7 — How to create and restore the databases