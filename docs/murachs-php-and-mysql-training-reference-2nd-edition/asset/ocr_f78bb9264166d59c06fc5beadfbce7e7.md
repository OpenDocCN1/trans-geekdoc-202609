# The syntax of the CREATE INDEX statement

```
```sql
CREATE [UNIQUE] INDEX|KEY indexName
ON tableName (columnName1 [ASC|DESC] [, columnName2 [ASC|DESC] ]...)
```
```

# A statement that creates an index based on a single column

```
```sql
CREATE INDEX customerID
ON orders (customerID);
```
```

# A statement that creates a unique index

```
```sql
CREATE UNIQUE INDEX emailAddress
ON customers (emailAddress);
```
```

# A statement that creates an index based on two columns

```
```sql
CREATE UNIQUE INDEX customerIDorderNumber
ON orders (customerID, orderNumber);
```
```

# A statement that creates an index that’s sorted in descending order

```
```sql
CREATE INDEX orderTotal
ON orders (orderTotal DESC);
```
```

# A CREATE TABLE statement that also creates indexes

```
```sql
CREATE TABLE customers (
    customerID      INT             NOT NULL     AUTO_INCREMENT,
    emailAddress    VARCHAR(255)    NOT NULL,
    firstName       VARCHAR(60)     NOT NULL,

    PRIMARY KEY (customerID),
    UNIQUE INDEX emailAddress (emailAddress),
    INDEX firstName (firstName)
);
```
```

# A DROP INDEX statement that drops an index

```
```sql
DROP INDEX firstName ON customers;
```
```

# Description

+   - An *index* improves performance when MySQL searches for rows in the table.
+   - MySQL automatically creates an index for primary keys and for unique constraints.
+   - You can use the CREATE TABLE statement to create indexes for a table.
+   - You can use the CREATE INDEX statement to add an index to a table.
+   - You can use the DROP INDEX statement to drop an index.