
## Using Group By clause

The group by widely used with aggregate functions like sum, avg, max min count etc. it create unique group of each element present in the column.

## Example

```
select dept, sum(salary) from emp_table group by dept;
```

*Above query will display the sum of salary from each department in a pivot view.*

## Group By clause and Distinct keyword

| Group By | Distinct |
|---|---|
| Group by clause widely used with aggregate functions like sum, avg, max min count etc. it create unique group of each element present in the column | Distinct keyword used in simple query to fetch with where clause to get unique records. Distinct cannot use for calculation or aggregation purpose. |

## The Having Clause:

The HAVING clause can be used to filter records after a GROUP BY clause is applied. So it can be used to summarize group records. So Only the groups(created after group by clause) that meet the HAVING criteria will be returned as a result.

## How the having clause is different from where clause?

HAVING applies to summarized group records, whereas WHERE applies to individual records. In short " where clause never work with aggregate function with group by ".

The where clause filter record before the aggregate of data while the having perform after aggregation/calculations is performed.

## The Having Clause syntax

```
SELECT column-names FROM table-name WHERE condition
GROUP BY column-names HAVING condition
```

**Example:** List the number of employees in each department.

Only include department with more than 15 employees.

```
SELECT COUNT(name), dept FROM mytable GROUP BY dept
HAVING COUNT(name) > 15
```

## Example 2

```
select min(salary) from emp group by emp_name having min(salary)<15000;
```

## Example 3

```
select dept,count(*) from emp group by dept having count(*)>3;
```

## Subqueries in MySQL:

A subquery or inner query sometimes called as nested query, is a query within another SQL query and embedded within the WHERE clause. In simple words, a subquery is an inner query which is placed within an outer query using different SQL clauses.

We can use subquery anywhere mostly with select command in MySQL enclosed within parentheses. An ORDER BY command cannot be used in a subquery, although the main query can use an ORDER BY. The GROUP BY command can be used to perform the same thing.

Example: Find list of names from a department who have more than 3 employees in the dept.

```
select name from emp where dept in(select dept from emp group by dept having count(*)>3);
```

Example 2: Display highest salary department wise and names who is taking maximum salary.

```
select emp_name from emp where salary in(select dept, max(salary) from emp group by dept);
```

```
SELECT employee_id,first_name,last_name,salary
FROM employees WHERE salary >
(SELECT AVG(SALARY) FROM employees);
```

## Notes

## PHP-Insert Data into MariaDB/MySQL

In the previous tutorial we learned how to send HTML form data to a PHP Page. Now we have to store the same information into MySQL or MariaDB database.

To complete the above task we have to follow the below steps-

- Design a HTML Page containing HTML Form fields
- Receive form field data to the PHP page using $_GET, $_REQUEST or $_POST
- Prepare a database connection
- Place appropriate query to insert record into Mysql table

## So let’s create a sample HTML page containing essential form fields

## add-employee.html

```html
<html>
<head>
<title>Add Employee Details</title>
</head>
<body>
<form method="post" action="thanks.php">
<table border="1" width="350">
<tr>
<td>Enter Name</td>
<td><input type="text" name="txtName"></td>
</tr>
<tr>
<td>Enter Email</td>
<td><input type="email" name="txtEmail"></td>
</tr>
<tr>
<td>Enter Password</td>
<td><input type="text" name="txtPassword"></td>
</tr>
<tr>
<td>Enter Phone</td>
<td><input type="text" name="txtPhone"></td>
</tr>
<tr>
<td colspan="2" align="center">
<input type="submit" value="Add Record">
</td>
</tr>
</table>
</form>
</body>
</html>
```

Now let‘s create an action page called – thanks.php to receive data from the above HTML Form Page. Make sure that you should have a submit button to proceed.

## thanks.php

```php
<?php
// create a variable
$name=$_REQUEST['txtName'];
$email=$_REQUEST['txtEmail'];
$password=$_REQUEST['txtPassword'];
$phone=$_REQUEST['txtPhone'];
// create a database connection
$con=mysqli_connect("localhost","root","","mydb");
// test database connectivity
if(mysqli_connect_errno($con))
{
echo 'Failed to connect...';
}
//Prepare and execute the insert query
$q= mysqli_query($con, "insert into employees(name,email,password,phone) values ('$name','$email','$password','$phone')");
if($q)
{
echo "Record inserted successfully";
}
else
{
echo mysqli_error($con);
}
mysql_close($con);
?>
```

Now let‘s create a Database and table (Open MySQL localhost://phpmyadmin) as required below

**Database Name:** mydb

**Table Name:** employees

**Column List:** name, email, password, phone

## To create the above database mydb run the following command

```
Create database mydb;
```

## To create table employees containing columns as mentioned above run the following command -

```
Create table employees (name varchar(20), email varchar(30),
password varchar(20), phone varchar(25));
```

## Connecting to the MySQL Server

Before you can do anything with MySQL, you must first connect to the MySQL server using your specific connection variables. Connection variables consist of the following parameters, which you must know before you make connectivity to the server:

**Host name**- In our case, it‘s the localhost because we‘ve installed everything locally. You will need to change this to whatever host is acting as your MySQL server.

**User name**- We‘ve used just the root user for local computer, but you may have another user name that you‘ll need to create username while making site live.

**Password**- We have just blank " " password for local computer, but you need to use your own password while making site live.

So you may put the same configuration into PHP Page something like this-

```php
<?php

$host = "localhost";

$user = "root";

$pass = " ";

$db="mydb";

$connect = mysqli_connect($host, $user, $pass,$db);

OR

$connect = mysqli_connect("localhost", "root", "","mydb");

?>
```

![](img/9ab4a56a650535285811bb802190e58f_84_0.png)

## Notes

## Retrieving Data from MySQL/MariaDB

In the previous lesson, we learnt how to send data to the database. Now it's time to retrieve data from our database to our PHP pages.

This is really one of the most important lessons in this book. Once you have read and understood this lesson, you will realize why database-driven web applications are so robust.

To retrieve data from a database, you use select queries like -

```
SELECT * FROM employees
```

Data display from database to the web page will process in two steps -

- The very first it will count the number of rows. You should know the number of the records in your table.
- Secondly we have to set the loop accordingly. Each time it will be incremented by one. It will fetch each row of the result and print the data stored there.

There are some popular methods to retrieve records from the database in PHP-

mysql_fetch_row(): It will fetch result row as an numeric way. it returns a row where the values will come in the same order as they are defined in the SQL query.

mysql_fetch_assoc(): It will fetch a result row as an associative array. This function will return a row as an associative array where the column names will be the keys storing corresponding value.

Means we can fetch our record through the table column name.

mysql_fetch_array(): It will fetch a result row as an associative array or a numeric array. So this is the combination of both the method of mysql_fetch_row and mysql_fetch_assoc.

mysql_fetch_object(): It will fetch a result row as an object

## Example 1: To retrieve data from MySQL Table - Let's retrieve records of recently added table as below-

Database Name: mydb

Table Name: employees

Column List: name, email, password, phone

```php
<?php

// Prepare a database connectivity first
$con = mysqli_connect("localhost", "root", " ", "mydb");

// Prepare SQL Statements to fetch record
$query = mysqli_query("SELECT * from employees");

// Use any fetch method to retrieve records
    while ($row = mysqli_fetch_assoc($query))
{
/* Now you can display columns using $row variable as all records
to be processed by the $row variable */
```
