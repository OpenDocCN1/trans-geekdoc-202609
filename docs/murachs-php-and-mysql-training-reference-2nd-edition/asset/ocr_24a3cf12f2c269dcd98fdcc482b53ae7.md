# A statement that renames a table

```
ALTER TABLE products RENAME TO product;
```

# A statement that adds a new column at the end of the table

```
ALTER TABLE customers ADD lastTransactionDate DATE;
```

# A statement that adds a new column after a specified column

```
ALTER TABLE customers ADD lastTransactionDate DATE
AFTER emailAddress;
```

# A statement that drops a column

```
ALTER TABLE customers DROP lastTransactionDate;
```

# A statement that renames a column

```
ALTER TABLE customers
CHANGE emailAddress email VARCHAR(255) NOT NULL UNIQUE;
```

# A statement that changes the definition of a column

```
ALTER TABLE customers MODIFY firstName VARCHAR(100) NOT NULL;
```

# A statement that changes the data type of a column

```
ALTER TABLE customers MODIFY firstName CHAR(100) NOT NULL;
```

# A statement that may cause data to be lost

```
ALTER TABLE customers MODIFY firstName VARCHAR(8);
```

# A statement that sets the default value of a column

```
ALTER TABLE customers ALTER firstName SET DEFAULT '';
```

# A statement that drops the default value of a column

```
ALTER TABLE customers ALTER firstName DROP DEFAULT;
```

# Description

+   - You can use the ALTER TABLE statement to modify the columns of an existing table.

# Warning

+   - You should never alter a table or other database object in a production database without first consulting the DBA, but you probably won’t have the privileges for doing that.

Figure 17-5 How to alter a table