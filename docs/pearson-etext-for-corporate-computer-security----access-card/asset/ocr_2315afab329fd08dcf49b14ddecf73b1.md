A SQL query is one of the most common SQL statements. It uses the SELECT clause. For example, suppose you are looking for a new car. You want a red car in a specific price range. In your mind you might think, “Select from this car lot all of the cars where the color is red and order them by price.” This might sound awkward, but all of the elements for a SQL query are present. Below is how this would look if it were written as a SQL statement.

```
SELECT * FROM Cars WHERE
color='red' ORDER BY price;
```

In this case, the SQL query retrieved information from a database containing information about cars. The table was named Cars, the column name was color, it returned information about all red cars, and it ordered the results based on values from the price column.

> ***Warning***: SQL injection can cause tremendous damage and harm. It is illegal to do on other systems, and you will be prosecuted. Do not use SQL injection on any system without permission. This is only for informational purposes.

# Passing SQL Statements

Typically, users are not allowed to submit their own SQL statements through webpages. This would be too difficult for users. It would also give them too much control over the database. Users usually select values from controls such as drop-down lists, combo boxes, or check boxes. They can also enter values such as a username or a password. These values are then sent to the webserver and web application (middleware) and eventually passed to the database.

The middleware server is responsible for accepting values passed from users and formatting the SQL statements. However, using SQL injection it is possible to send malformed input that can alter the statement created by the web application. As shown in Figure 8-8, the altered SQL statement is then sent to the database. The subsequent results are sent directly back to the user.

In the example below, you will see how values from a login screen (username and password) are entered and passed to the web application correctly. You’ll then see an example of how SQL injection could be used maliciously. SQL statements are usually written on a single line. To make the statements easier to read, the clauses have been placed on separate lines.

# Normal SQL Statements

Login screens require users to enter a username and password. These values are then passed to the web application and checked against values in the database. The SQL statement below shows how these parameters might be passed to a database for a legitimate login shown in Figure 8-9.

# Figure 8-8 Simplified SQL Injection Path

![](bbox=[0.29, 0.77, 0.9, 0.95])