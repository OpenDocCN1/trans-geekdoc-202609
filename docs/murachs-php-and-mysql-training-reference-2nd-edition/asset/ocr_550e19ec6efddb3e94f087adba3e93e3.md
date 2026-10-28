# The code

The database.php file contains the code that creates the PDO object and stores it in the variable named $db. This file is executed by the index.php file that’s shown on the next page.

However, if an error occurs when this file is executed, the catch block stores the error message in a variable named $error_message. Then, the catch block uses the include function to include the database_error.php file, which displays a page that contains the error message. Last, the catch block exits the script.

Note that in the database.php file that the username for the connection is “mgs_user” and the password is “pa55word”. For this connection to work, then, a user with this username and password must be stored with the MySQL database. In fact, as you learned in chapter 3, this user is created by the SQL script that creates the databases for this book. Also, this user is given the privileges that are needed for running SELECT, INSERT, UPDATE, and DELETE statements against any table in the my_guitar_shop1 database. As a result, this connection will work for this application.