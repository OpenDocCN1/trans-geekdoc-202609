In this example, we modify the "email" column of the "customers" table to disallow NULL values.

# 3. Dropping Columns: Use the ALTER TABLE statement with the DROP COLUMN clause to remove columns from an existing table.

Example:

```
```sql
ALTER TABLE customers

DROP COLUMN phone_number;
```
```

In this example, we remove the "phone_number" column from the "customers" table.

# Section 4: Inserting Data into Tables

Now that we have created our tables, we can start populating them with data. The INSERT statement allows us to add new records into a table. Here's how you can insert data:

+   1. Identify the table into which you want to insert data.