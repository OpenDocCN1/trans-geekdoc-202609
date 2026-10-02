```
ON orders.customer_id = customers.customer_id;
```

In this example, we retrieve the order ID from the "orders" table and the customer name from the "customers" table, joining them on the common column "customer_id."

# Section 3: Left Join

The LEFT JOIN returns all rows from the left table and the matching rows from the right table. If there are no matches, NULL values are included for the columns of the right table. The syntax for a left join is as follows:

```
```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
```

Example: