# 4. Click the Submit Query button.

The query is executed, and a page is displayed, showing the results of the query. If your query had an error, the error message is displayed.

You can test the mysql_send.php program by entering this test query in Step 2 of the preceding steps:

```
SHOW DATABASES
```

This query does not require you to enter a database name, so you can skip Step 3. When you click the Submit Query button in Step 4, a listing of the existing databases is displayed. In most cases, you see a database called Test, which is installed automatically when MySQL is installed. Also, you'll probably see a database called mysql, which MySQL uses to store information that it needs, such as account names, passwords, and permissions. Even if there are no existing databases, your SQL query will execute correctly. If a problem occurs, an error message is displayed. MySQL error messages are usually pretty helpful in finding the problem.

![](bbox=[0.07, 0.44, 0.16, 0.52])

# A quicker way to send SQL queries to the MySQL server

When MySQL is installed, a simple, text-based program called mysql (or sometimes the terminal monitor or the monitor) is also installed. Programs that communicate with servers are client software; because this program communicates with the MySQL server, it's a client. When you enter SQL queries in this client, the response is returned to the client and displayed onscreen. The monitor program can send queries across a network; it doesn't have to be running on the machine where the database is stored.

To send SQL queries to MySQL by using the mysql client, follow these steps:

# 1. Locate the mysql client.

By default, the mysql client program is installed in the subdirectory bin, under the directory where MySQL was installed. In Unix/Linux, the default is /usr/local/mysql/bin or /usr/local/bin. In Windows, the default is c:\mysql\bin. However, the client might have been installed in a different directory. Or, if you're not the MySQL administrator, you might not have access to the mysql client. If you don't know where MySQL is installed or can't run the client, ask the MySQL administrator to put the client somewhere where you can run it or to give you a copy that you can put on your own computer.

# 2. Start the client.

In Unix/Linux, type the path/filename (for example, /usr/local/mysql/bin/mysql). In Windows, open a command prompt window and then type the path/filename (for example, c:\mysql\bin\mysql.exe). Press Enter after typing the path/filename unless you're using the parameters shown in Step 3.