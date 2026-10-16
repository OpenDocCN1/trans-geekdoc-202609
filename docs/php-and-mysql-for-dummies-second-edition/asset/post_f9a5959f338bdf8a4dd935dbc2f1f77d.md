
## Part II
### MySQL Database
### The 5th Wave
By Rich Tennant

![](img/d82df0828cfbc6d6be1e9a991861f3b7_83_0.png)

> > “Our automated response policy to a large, company-wide data crash is to notify management, back up existing data and sell 90% of my shares in the company.”

### In this part . . .
This part provides the details of working with a MySQL database. You find out how to use SQL to communicate with MySQL. In addition, you discover how to create a database, change a database, and move data in and out of a database.

## Chapter 4
### Building the Database
### In This Chapter
- Using SQL to make requests to MySQL
- Creating a new database
- Adding information to an existing database
- Looking at information in an existing database
- Removing information from an existing database

After completing your database design (see Chapter 3 if you haven't done this yet), you're ready to turn it into a working database. In this chapter, you find out how to build a database based on your design — and how to move data in and out of it.

The database design names the database and defines the tables that make up the database. In order to build the database, you must communicate with MySQL, providing the database name and the table structure. Later on, you must communicate with MySQL to add data to (or request information from) the database. The language that you use to communicate with MySQL is SQL. In this chapter, I explain how to create SQL queries and use them to build new databases and interact with existing databases.

### Communicating with MySQL
The MySQL server is the manager of your database:
- It creates new databases.
- It knows where the databases are stored.
- It stores and retrieves information, guided by the requests (*queries*) that it receives.

To make a request that MySQL can understand, you build an SQL query and send it to the MySQL server. (For a more complete description of the MySQL server, see Chapter 1.) The next two sections detail how to do this.

### Building SQL queries
*SQL (Structured Query Language)* is the computer language that you use to communicate with MySQL. SQL is almost English; it is made up largely of English words, put together into strings of words that sound similar to English sentences. In general (fortunately), you don’t need to understand any arcane technical language to write SQL queries that work.

The first word of each query is its name, which is an action word (a verb) that tells MySQL what you want to do. The queries that I discuss in this chapter are `CREATE`, `DROP`, `ALTER`, `SHOW`, `INSERT`, `LOAD`, `SELECT`, `UPDATE`, and `DELETE`. This basic vocabulary is sufficient to create — and interact with — databases on Web sites.

The query name is followed by words and phrases — some required and some optional — that tell MySQL how to perform the action. For instance, you always need to tell MySQL what to create, and you always need to tell it which table to insert data into or to select data from.

The following is a typical SQL query. As you can see, it uses English words:

```sql
SELECT lastName FROM Member
```

This query retrieves all the last names stored in the table named `Member`. Of course, more complicated queries (such as the following) are less English-like:

```sql
SELECT lastName,firstName FROM Member WHERE state="CA" AND
             city="Fresno" ORDER BY lastName
```

This query retrieves all the last names and first names of members who live in Fresno and then puts them in alphabetical order by last name. This query is less English-like but still pretty clear.

Here are some general points to keep in mind when constructing an SQL query, as illustrated in the preceding sample query:

![](img/d82df0828cfbc6d6be1e9a991861f3b7_86_0.png)

- **Capitalization:** In this book, I put the SQL language words in all caps; items of variable information (such as column names) are usually given labels that are all or mostly lowercase letters. I did this to make it easier for you to read — not because MySQL needs this format. The case of the SQL words doesn’t matter; *select* is the same as `SELECT`, and *from* is the same as `FROM`, as far as MySQL is concerned. On the other hand, the case of the table names, column names, and other variable information does matter if your operating system is Unix and Linux. When using Unix or Linux, MySQL needs to match the column names exactly, so the case for the column names has to be correct — *lastname* is not the same as *lastName*. Windows, however, isn’t as picky as Unix and Linux; from its point of view, *lastname* and *lastName* are the same.

**Spacing:** SQL words need to be separated by one or more spaces. It doesn't matter how many spaces you use; you could just as well use 20 spaces or just 1 space. SQL also doesn't pay any attention to the end of the line. You can start a new line at any point in the SQL statement or write the entire statement on one line.

**Quotes:** Notice that CA and Fresno are enclosed in double quotes (") in the preceding query. CA and Fresno are series of characters called *text strings* or *character strings*. (I explain strings in detail later in this chapter.) You are asking MySQL to compare the text strings in the SQL query with the text strings already stored in the database. Text strings are enclosed in quotes. When you compare numbers (such as integers) stored in numeric columns, you don't enclose the numbers in quotes. (In Chapter 3, I explain the types of data that can be stored in a MySQL database.)

### Sending SQL queries
This book is about PHP and MySQL as a pair. Consequently, I don't describe the multitude of ways in which you can send SQL queries to MySQL — many of which have nothing to do with PHP. Rather, I provide a simple PHP program that you can use to execute SQL queries. (For the lowdown on PHP and how to write PHP programs, check out Part III of this book.)

The program `mysql_send.php` has one simple function: to execute queries and display the results. Enter the program into the directory where you're developing your Web application (or download it from my Web site at `janet.valade.com`), change the information in lines 9–19, and then point your browser at the program. Listing 4-1 shows the program.

### Listing 4-1: PHP Program for Sending SQL Queries to MySQL

```html
<!-- Program: mysql_send.php
Desc: PHP program that sends an SQL query to the MySQL server and displays the results.
-->
<html>
<head><title>SQL Query Sender</title></head>
<body>
<?php
$host="hostname";
$user="mysqlaccountname";
$password="mysqlpassword";

/* Section that executes query */
if(@$_GET['form'] == "yes")
{
```

### Listing 4-1 (continued)

```php
mysql_connect($host,$user,$password);
mysql_select_db($_POST['database']);
$query = stripslashes($_POST['query']);
$result = mysql_query($query);
echo "Database Selected: <b>{$_POST['database']}</b><br>
     Query: <b>$query</b><h3>Results</h3><hr>";

if($result == 0)
    echo "<b>Error ".mysql_errno().": ".mysql_error().
         "</b>";
elseif (@mysql_num_rows($result) == 0)
    echo("<b>Query Completed. No results returned.
          </b><br>");
else
{
    echo "<table border='1'>
          <thead>
            <tr>";
              for($i = 0;$i < mysql_num_fields($result);$i++)
              {
                  echo "<th>".mysql_field_name($result,$i).
                       "</th>";
              }
    echo "  </tr>
          </thead>
          <tbody>";
          for ($i = 0; $i < mysql_num_rows($result); $i++)
          {
              echo "<tr>";
              $row = mysql_fetch_row($result);
              for($j = 0;$j<mysql_num_fields($result);$j++)
              {
                  echo("<td>" . $row[$j] . "</td>");
              }
              echo "</tr>";
          }
    echo "</tbody>
          </table>";
}   //end else
echo
 "<hr><br>
 <form action=\"{$_SERVER['PHP_SELF']}\" method=\"POST\">
   <input type='hidden' name='query' value='$query'>
   <input type='hidden' name='database'
          value='{$_POST['database']}'>
   <input type='submit' name=\"queryButton\"
          value=\"New Query\">
   <input type='submit' name=\"queryButton\"
          value=\"Edit Query\">
 </form>";
unset($form);
exit();
}   // endif form=yes
```
