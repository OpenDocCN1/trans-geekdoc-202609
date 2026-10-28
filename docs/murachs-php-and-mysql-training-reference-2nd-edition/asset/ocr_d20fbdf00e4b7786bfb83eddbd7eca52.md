# How to select rows with a WHERE clause

Another way to limit the number of rows that a SELECT statement retrieves is to code a WHERE clause. When you do that, you often use the comparison operators shown in figure 18-4. If the result of the comparison is TRUE for a row, MySQL includes the row in the result set.

The examples in this figure show how to use some of the comparison operators. For instance, the first WHERE clause uses the equal operator (=) to retrieve only those rows with a categoryID column that has a value of 2. Since the category ID is a numeric literal, it doesn’t need to be enclosed in quotes, although it’s okay to enclose it in quotes. In contrast, a string literal like the one in the second WHERE clause must be enclosed in quotes.

The third WHERE clause uses the less than (<) operator to retrieve only those rows that have a list price that’s less than 499.99. Then, the fourth example uses the greater than or equal to (>=) operator to retrieve those rows that have a list price that’s greater than or equal to 499.99.

The fifth WHERE clause illustrates how you can use comparison operators other than the equal operator with string data. In this example, the less than (<) operator is used to compare the value of the productName column to a string literal that has the letter G in the first position. That causes the query to return all product names that begin with the letters A through F.

You can also use the comparison operators with date literals, as illustrated by the sixth and seventh clauses. The sixth clause retrieves rows that were added before January 31, 2014, and the seventh clause retrieves rows that were added on or after January 31, 2014. Like string literals, date literals must be enclosed in single quotes. MySQL also expects date literals to use this format: yyyy-mm-dd.

When you code a date literal, MySQL adds a default time of 00:00:00, which is the start of the day. As a result, if you’re working with a date/time value that includes a time component, you need to take this into account. If necessary, you can code a date literal that includes a time component. For example, you can code a time component for 4:30pm and 10 seconds like this:

```
```sql
'2014-10-30 16:30:10'
```
```

Note that the time component uses a 24 hour clock where 16 hours is 4pm.

The eighth WHERE clause shows how you can test for a not equal condition. To do that, you code a less than (<) sign followed by a greater than (>) sign. In this example, the WHERE clause only retrieves rows with a discount percent that’s not equal to 30.

Whenever possible, you should compare expressions that have similar data types. If you attempt to compare expressions that have different data types, MySQL may implicitly convert the data types for you. Although implicit conversions are often acceptable, they occasionally yield unexpected results.