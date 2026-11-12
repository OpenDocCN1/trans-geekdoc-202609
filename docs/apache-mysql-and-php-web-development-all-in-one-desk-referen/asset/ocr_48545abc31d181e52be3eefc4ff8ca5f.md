This statement selects rows from the category table found in the database called phpbase. The statement retrieves only those rows where categoryID is 3. In this case, only one row has categoryID equal to 3, the row where category_name is books.

Next, I make sure that the mysql_query call succeeded by checking its result. If so, I call mysql_num_rows, passing the result of mysql_query. This function tells me how many rows are in the result set. (A result set is a set of rows that you get back from a select statement.) If at least one row is present in the result set, I grab the first row by calling mysql_fetch_assoc. This function is really cool: It returns an array where the keys are the names of the columns in the table. Thus, I can check the columns in this particular row by inspecting the values of $row["categoryID"] and $row["category_name"]. And, in fact, that's what I do, and I print out the values of these two columns.

Finally, I call mysql_free_result, which releases the memory held in the result from the query, and I call mysql_close, which closes the connection.

In the following sections, I give you more detail on how to work with the mysql_query function, the mysql_fetch_assoc function, and many others. For now, remember the two following points:

+   * Call mysql_connect to connect to the MySQL system, passing the host name, the username, and the password.
+   * Call mysql_close to end your connection with the MySQL system.

# Adding MySQL Data with PHP

The mysql_query function in PHP is a general-purpose statement for performing SQL statements on a MySQL database. Although the name contains the word query, which usually implies looking up data, you can use this function for all your SQL work, not just queries.

Here's a simple .php file that adds a row to the customer table in the phpbase database:

```
<html><title>Simple Insert...</title>
<body>
<?php
mysql_connect("localhost", "phpuser", "phppass");
$result = mysql_query(
"insert into phpbase.customer
(name, email, signup, last_access) values
('Jeff', 'me@domain.com', '2003-06-21',
'2003-06-21')"
);
if ($result) {
```