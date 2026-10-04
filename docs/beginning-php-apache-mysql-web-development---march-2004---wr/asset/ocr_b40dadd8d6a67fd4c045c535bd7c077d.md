# Chapter 12

![](bbox=[0.068, 0.085, 0.845, 0.565])

# How It Works

Nineteen files make up this CMS application. An additional file is used once to create the tables, making 20 files in all. That may seem like a lot to you, but the use of transaction pages and include files increases the number substantially. If you did not have the application broken out into separate files, you would have fewer files, but each file would be much larger. Our primary purpose in separating the application into many files is to reduce redundancy.

# Connect to the Data Source

Your first step in creating this application is to connect to the database. Most of your pages will require this connection, so putting it in a separate included file is the best solution. File is `conn.php`:

```
define('SQL_HOST', 'yourhost');
define('SQL_USER', 'jouser');
define('SQL_PASS', 'yourpassword');
define('SQL_DB', 'yourdatabase');

$conn = mysqli_connect(SQL_HOST, SQL_USER, SQL_PASSWORD);
```

390