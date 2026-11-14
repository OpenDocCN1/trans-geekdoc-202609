The UPDATE command is utilized to modify existing data within a table, allowing for the specification of the table, the columns to be updated, the new values, and a condition to accurately target the desired records for modification.

+   • Fundamental Syntax:

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

+   • Practical Application: To alter the price of a product with id = 5:

```
UPDATE products SET price = 399 WHERE id = 5;
```

# The DELETE Statement

Utilizing the DELETE FROM command enables the removal of records from a table. Given its potential to irreversibly eliminate data, judicious application of this command is paramount.

+   • Syntax Primer:

```
DELETE FROM table_name WHERE condition;
```