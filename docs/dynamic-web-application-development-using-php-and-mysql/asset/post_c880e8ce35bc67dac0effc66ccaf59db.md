
to be as follows:

| Field | Type |
|---|---|
| Id | Integer |
| customers_Id | Integer |
| Day | Integer |
| Month | Integer |
| Year | Integer |

The customers_Id field is the same as the id field in the Customers table and it allows us to form a relationship between the Customers table and the Purchases table as we need to be able to know when reading the Purchases table which customer made the purchase. Our database design now looks like that shown in Figure 14.34.

Now the Purchases table holds its own unique Id as well as the Id of the customer who made the purchase. It also has three fields to store the date that the purchase was made. We could have used a single date field but it will be easier for us later if we keep these as three separate integer fields. However, the design doesn't yet allow us to store which products were purchased at that time. To do this we need to create a new table called purchaseProducts. The purchaseProducts table will contain the following data fields and types:

| Field | Type |
|---|---|
| products_Id | Integer |
| purchases_Id | Integer |
| Quantity | Integer |
| Cost | Float |

The products_Id field is the Id field from the Products table; it allows us to determine which product was bought. The purchase_Id is the Id field from the Purchases table.

## FIGURE 14.34 Revised database design

![](img/b2471264f405d17994ef173e4b9cec92_448_0.png)

The Quantity field stores how many products were purchased and the Cost field is the price. We have included the cost field in this table as well as in the Products table as it is possible that the cost of a product may change over time but we would want to record the cost for which it was actually purchased, hence why this field is included in the purchaseProducts table. Our database design is now as shown in Figure 14.35.

It is time to create these new tables in our MySQL database using phpMyAdmin. Click on the database name on the left of the screen and, as shown in Figure 14.7, enter the name of the first new table. This will be purchaseProducts and it contains the four fields mentioned above. This table doesn't have its own primary index but it does have two indexes from other tables. These are the products_Id and purchases_Id fields. To indicate these we need to ensure that the 'Index' radio button is selected. This is the second radio button along on the far right of the screen. This radio button should be selected for both of these fields as indicated in Figure 14.36. After you have entered the data as shown, click the Save button to create the table.

Next we create the Purchases table by clicking on the database name of the left of the screen and entering the name 'Purchases' along with the value 5 for the number of fields.

Clicking the Go button will display the create table screen for the Purchases. This is completed as shown in Figure 14.37.

> NOTE
> Note that the id field is auto_increment and is a Primary key. Also, that customer_Id is an Index.

## FIGURE 14.35 purchaseProducts table added to design

![](img/b2471264f405d17994ef173e4b9cec92_449_0.png)

## FIGURE 14.36 Adding the purchaseProducts table

![](img/b2471264f405d17994ef173e4b9cec92_450_0.png)

## FIGURE 14.37 Adding the Purchases table

![](img/b2471264f405d17994ef173e4b9cec92_450_1.png)

We have now finished creating our database structure and can add some data to these new fields.

## Our data

The next step in our database creation is to include some new records for the tables we have just created. The data to be entered into the Purchases table is shown in Figure 14.38 and the data to be entered into the purchaseProducts table in Figure 14.39. Enter all of this data into the correct database tables.

That's it, we have now completed our database structure and data content. In the next lesson we shall learn how to use PHP scripts to interact with the MySQL database and extract and manipulate this data.

## FIGURE 14.38 Purchases table data

| Id | customers_id | Day | Month | Year |
|---|---|---|---|---|
| 1 | 2 | 3 | 9 | 2006 |
| 2 | 4 | 6 | 9 | 2006 |
| 3 | 6 | 13 | 9 | 2006 |
| 4 | 2 | 22 | 9 | 2006 |
| 5 | 1 | 28 | 9 | 2006 |
| 6 | 9 | 1 | 10 | 2006 |
| 7 | 7 | 1 | 10 | 2006 |

## FIGURE 14.39 purchaseProducts table data

| products_id | purchase_ID | Quantity | Cost |
|---|---|---|---|
| 2 | 1 | 20 | 2.99 |
| 3 | 2 | 10 | 3.50 |
| 8 | 2 | 30 | 4.50 |
| 6 | 3 | 25 | 2.50 |
| 3 | 4 | 10 | 3.50 |
| 4 | 4 | 100 | 1.50 |
| 5 | 4 | 40 | 3.00 |
| 1 | 5 | 22 | 3.99 |
| 1 | 6 | 6 | 3.99 |
| 3 | 7 | 15 | 3.50 |
| 4 | 7 | 25 | 2.00 |
| 5 | 7 | 10 | 2.50 |
| 7 | 7 | 55 | 2.50 |
| 8 | 7 | 1 | 3.99 |

## Exercises

14.1 Back up your completed database to a .sql file and keep this safe.

## SUMMARY

In this chapter, we began by introducing the concept of databases. We described the concept of database tables and their fields. We examined the different field types that a database such as MySQL supports. Next we introduced the phpMyAdmin tool and illustrated how this can be used to manipulate MySQL databases. We showed the creation of a database through the creation of the ‘glassesrus’ database. We examined how records can be added, amended and deleted and how the database can be backed up to a dump file. Finally, we illustrated the MySQL Workbench tool and extended our database.

## References and further reading

- MySQL. Home Page. http://www.mysql.com/
- MySQL. Documentation. http://dev.mysql.com/doc/
- Php editors.com. Learning SQL using phpMyAdmin http://www.php-editors.com/articles/sql_phpmyadmin.php
- phpMyAdmin. Home Page. http://www.phpmyadmin.net/home_page/index.php
- Wikipedia. Databases. http://en.wikipedia.org/wiki/Database

## Linking PHP to a Database

## LEARNING OBJECTIVES

- To understand how to connect to a MySQL database using PHP
- To understand how to read a single record from a database
- To understand how to read multiple records from a database
- To understand how to read records which match to specific requirements
- To understand how to sort returned records
- To understand how to delete, insert and amend records
- To understand how to count the number of occurrences of records which match a search criteria

## INTRODUCTION

In Chapter 14, we introduced the MySQL relational database management system. We showed that using the phpMyAdmin interface to MySQL we were able to create new databases. Within these databases we created tables and specified the field names and types which hold the data we included within the tables. We needed to undertake these tasks because this was preparation for what we are about to learn in this chapter.

We are now going to see how PHP can interact with the database we have created, extracting information from the database as well as updating it. We shall show how easy it is to do this and how the database can assist us in producing truly dynamic and useful web-enabled applications.

## 15.1 Connecting to a MySQL DBMS

In order for a PHP script to access a database we need to form a connection from the script to the database management system (DBMS). Connecting a PHP script to a DBMS is a

The mysql_error() function requires no parameters and returns an error message string. Combining function die() and function mysql_error() looks like this:

```
die("Could not connect: " . mysql_error() )
```

Combining the die() function with the mysql_connect() function requires us to use the ‘or’ construct like this:

```
$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );
```

The above code fragment should now be read as ‘form a mysql connection to localhost and if this doesn’t work stop the script’.

We are now ready to form these functions together into our first PHP script and here it is:

```
<?php
// File: example15-1.php

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("glassesrus", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );
echo "<h1>Connected To Database</h1>";
?>
```

The above script opens a connection to the DBMS server and then attempts to select database ‘glassesrus’ the database we created in Chapter 14. If something goes wrong in either operation an error message is generated and the script terminates. If all goes well, the output from running the above script will appear to be nothing.

## 15.2 Reading from a database

The next step in linking PHP to a database is to get it to send a Structured Query Language (SQL) statement to the database in order to begin to retrieve data records. To do this we need to introduce a new function that of mysql_query():

```
resourceRecords = mysql_query (query, resourceId);
```

Function mysql_query() requires two parameters; the first is an SQL query string (more on this in a minute) and the second is the database resource identifier returned from the mysql_connect() function. The function returns a resource identifier to the returned data.

| NOTE | Function mysql_query() will fail and return ‘false’ if table(s) referenced by the query do not exist. |

The following is an example of a valid use of the function:

```
$dbRecords = mysql_query("SELECT * FROM customers", $dbLocalhost)
```
