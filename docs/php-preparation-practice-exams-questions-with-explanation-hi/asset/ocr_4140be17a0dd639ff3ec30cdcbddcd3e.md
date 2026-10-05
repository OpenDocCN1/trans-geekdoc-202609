prevent data loss allows for a quick recovery in case of errors during the migration process.

# Question 11. Which of the following PHP functions is used to establish a connection to a MySQL database using the mysqli extension, and what are the required parameters for the function to execute successfully?

+   A. connect_to_db($host, $username, $password)
B. mysqli_connect($host, $username, $password, $database)
C. db_connect($host, $user, $pass)
D. mysql_connect($host, $user, $pass, $dbname)

Correct Answer: B

Explanation: The correct function to establish a connection to a MySQL database using the mysqli extension is mysqli_connect(), which requires four parameters: the host, user name, password, and database name. This function returns a connection object on success, which can be used for further database operations. Using mysql_connect() is outdated as it is deprecated in favor of mysqli and PDO.

# Question 12. In the context of PHP and database integration, what is the purpose of prepared statements, and how do they enhance security in database operations?

+   A. They are used to format SQL queries in PHP.
B. They help prevent SQL injection attacks by separating SQL logic from data.
C. They optimize query execution by caching results.
D. They allow dynamic table creation in MySQL databases.

Correct Answer: B

Explanation: Prepared statements are a feature used to enhance security by separating SQL code from the data being processed. This separation helps prevent SQL injection attacks, where malicious input can manipulate the query. By binding parameters, prepared statements ensure that the input is treated as data rather than executable code, significantly improving security.