
## Part III: Using PHP Practice

So when creating indexes on a table, don't create more than you need. Limit indexed columns to those that will be searched or sorted frequently. If required, you can create additional indexes on a table as you need them to increase performance.

## Introducing SQL Statements

To actually work with databases and tables, you use SQL statements. Common statements include:

- SELECT — Retrieves data from one or more tables
- INSERT — Inserts data into a table
- REPLACE — Replaces data in a table. If the same record exists in the table, the statement overwrites the record with the new data
- UPDATE — Updates data in a table
- DELETE — Deletes data from a table

Other often-used statements create or modify tables and databases themselves, rather than manipulating the data stored in table:

- CREATE — Creates a database, table or index
- ALTER — Modifies the structure of a table
- DROP — Wipes out a database or table

You learn more about these statements as you work through the next few chapters. Just to give you a taste though, let's take a look at the typical form of a MySQL SELECT statement, which retrieves records from a table. Operations performed with SELECT are known as queries (hence the name "Structured Query Language")

```
SELECT field1, field2, ..., fieldn FROM table WHERE condition
```

A statement may extend to multiple lines. Here is a simple example of a real multi-line SQL statement:

```
SELECT lastName, firstName
FROM users
WHERE firstName = 'John'
```

Take a closer look at the FROM and WHERE clauses in query. The query returns any record from the users where the value of the firstName is "John". Assuming there is actually a table called users in the database, the query's output might look like this:

```
Simpleton John
Smith John
Thomas John
```

The returned values are known as the result set. As you see, you can loop through the rows in a result set within your PHP script. If your query finds no results, NULL (discussed in the next section) is returned instead.

Other SQL statements such as DELETE or INSERT do not return a result set.

## Chapter 12: Introducing Databases and SQL

As well as the data types previously mentioned, MySQL can deal with another special value known as NULL.

In a MySQL table, a NULL value for a field represents missing data in that field. NULL doesn't belong to any particular data type, but it can replace any value. Because it is not a data type, even though it be in a field, the concept of a NULL is often difficult to grasp. For example, a common mistake is to think of NULL as zero, which is wrong because zero is a value; NULL strings with one or more blank spaces, and strings of zero length, also be mistaken for NULL. NULL is nothing, no data type, no data.

So what happens if the result of one of your queries contains a NULL and that result is used in your PHP script in subsequent calculations? Generally speaking, NULL propagates throughout the calculations. Any arithmetic operation involving a NULL returns NULL. After all, how could you provide results when all the data needed to perform the calculation are not present?

Don't worry if the concept of NULL seems a bit strange at first. It will make sense once you start using it in earnest.

Now let's put this theory into practice and have some fun with MySQL!

## Setting Up MySQL

The MySQL database system comes with a number of different programs. The two important ones that you learn about are:

- The MySQL server — This is the database engine itself. The program is usually called mysql or similar

- The MySQL command-line tool — You can use this to talk directly to the MySQL server so that you can create databases and tables, and add, view, and delete data. It is handy for setting your databases and for troubleshooting. The program name is mysql

## Starting the MySQL Server

If you followed the instructions in Chapter 2 for installing PHP — using Synaptic on Ubuntu, WampServer on Windows, or MAMP on Mac OS — the MySQL server and command-line tool should already be installed on your computer. In fact, the MySQL server may already be running, but if it's not, here's how to start it:

- Ubuntu — Choose Administration ⇒ In the dialog that appears, look for the "Database server (mysql)" item in the list. If there's a check to the left of the item, it should already be running. If not, click Unlock, type your password, and click Authenticate. Now click the checkbox to the left of "Database server (mysql)" item. The MySQL database server (mysql) should be running

- WampServer on Windows — Examine the WampServer icon in taskbar. If the icon is green and white, your Apache and MySQL servers should be running correctly. If the icon is yellow or red part, then one or both of the servers aren't running. Click the icon to display the WampServer menu, then choose the Start All Services or Restart All Services option to start both the Apache and MySQL servers

- MAMP on Mac OS — Open the MAMP folder inside your Applications folder in Finder, double-click the MAMP icon to launch the application. If the MySQL server has a red light to the left of it, click the Start Servers button to start up the Apache and MySQL servers. Both lights should now be green

## Setting Up the MySQL root Password

Now that the MySQL database engine is running on your computer, it's time to configure the root user.

MySQL, like most networked systems, requires you to log in with a specific user account before doing anything else. It is a fairly obvious security measure, and limits the access. The process of setting a root password can seem a bit long, especially if you're unfamiliar with MySQL. To set a root password, follow these steps:

- 1. Bring up a shell — On Ubuntu, choose Terminal. In Windows, choose Command prompt. On-Mac OS, choose Terminal.

- 2. Change to the correct directory — On Ubuntu, mysql is usually installed in /usr/bin/. With WampServer on Windows, this would be C:\wamp\bin. Using MAMP, the correct directory should be /Applications/bin.

- 3. Start the MySQL command-line tool — On Ubuntu and Windows, type:

```
mysql -u root
```
(that's a period, then a slash, then mysql, followed by a space, a hyphen, the letter "u," another space, and the word root) and press Enter. You should see a message similar to the following, indicating that you are now running the mysql tool:

Welcome to the MySQL monitor. Commands end with ; or \.
Your MySQL connection id is 671
Server version: 5.0.41 Source distribution

Type 'help;' or 'h' for help. Type '\c' to clear the buffer.

```
mysql>
```

If you get an error along the lines of "Access denied for user 'root'@localhost (using password: NO)", your MySQL server's root account already has a password, and you'll need to enter the password -p (as shown in a moment). If you've forgotten the password, you can reset it as described in a moment.

- 4. Inspect the current privileges — Enter the following at the mysql> prompt and press Enter:

```
SELECT Host, User, Password FROM mysql.user;
```

When entering SQL statements in the MySQL command-line program, you need to end each statement with a semicolon.

You'll see a list of the current users and passwords in the MySQL system, presented as a table. It'll probably look similar to the following:

| Host | User | Password |
| :--- | :--- | :--- |
| localhost | root | |
| mattcomputer | root | |
| 127.0.0.1 | root | |
| localhost | | |
| mattcomputer | | |

5 rows in set (0.00 sec)

```
mysql>
```

You should see one or more rows with root in the User column, and an empty Password column. You need to add a password to each one of those rows.
