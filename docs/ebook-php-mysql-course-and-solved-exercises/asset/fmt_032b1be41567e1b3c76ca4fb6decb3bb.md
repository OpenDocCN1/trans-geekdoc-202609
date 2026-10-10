
Now that we have a basic understanding of databases and MySQL, we'll move on to the practical part: connecting to a MySQL database from a PHP script. In fact, to be able to query a database, it is necessary to first establish a connection with that database. In this part of the book, we'll learn the steps involved in establishing a secure connection, configuring connection parameters, opening and closing a connection, as well as good security practices to protect our credentials.

In short, this section will provide us with the knowledge and skills we need to understand and establish a secure connection to a MySQL database, laying the foundations for our further exploration of database integration in our PHP applications.

There are two main methods commonly used to manage connections to MySQL databases: using the `mysqli_` extension and using the `PDO` (PHP Data Objects) object. Both offer robust functionality for establishing a secure connection and interacting with the MySQL database.

The first method, the `mysqli_` extension, provides a MySQL-specific interface with functions such as `mysqli_connect()` to establish the connection, `mysqli_query()` to execute SQL queries, and `mysqli_fetch_array()` to retrieve results. This extension is directly integrated into PHP and offers high performance for interactions with MySQL.

The second method, the `PDO` extension, provides a more generic interface for working with different databases, including MySQL. `PDO` offers a more general database abstraction, making it easier to switch databases if necessary. It also supports prepared queries, offering greater security against SQL injections.

The choice between `mysqli_` and `PDO` often depends on the developer's preferences and the specific needs of the project. Both methods are widely used and offer comprehensive functionality for interacting with MySQL in PHP. In this book, we focus on the use of the `PDO` object.

## What is PDO?

`PDO` (PHP Data Objects) is an extension introduced in PHP 5 that offers a data abstraction layer, meaning it is not specifically linked to MySQL and is independent of the database used. Thanks to `PDO`, code becomes portable very easily, making it possible to switch from a `MySQL` database to `SQLite`, `PostgreSQL`, `Oracle` and others simply by modifying the connection line.

`PDO` offers a number of advantages, including portability, ease of use and speed. Indeed, this extension offers a uniform interface for interacting with different databases, simplifying code development and maintenance.

## The PDO extension comprises three main classes:

### `PDO` class
Creates objects representing the database connection, and provides methods for essential operations such as sending queries, creating prepared queries and managing transactions.

### `PDOStatement` class
Represents a prepared query or SELECT query result. Its methods manage prepared queries and read query results.

### `PDOException` class
Allows you to manage and display error information using objects, making it easier to debug and manage errors in applications.

## Database connection process

The process of connecting to a MySQL database using `PDO` involves two main steps:

1.  **Creating an instance of the `PDO` class**: First, create an instance of the `PDO` class by specifying the database connection parameters, such as host name, database name, user name and password.
2.  **Error handling**: It is recommended to configure `PDO` to generate exceptions in the event of errors during connection or query execution. This allows errors to be handled appropriately in the code.

To illustrate this process concretely, let's take the example of creating a `library` web application. Before creating the corresponding database, let's create a directory named `library` on your Apache server, i.e. in the `htdocs` folder of XAMPP if you had installed it as explained in Chapter 1.

### Creation of the "library" database

Next, we create a database named `library` and some associated tables:

At this stage, the database comprises three tables:

*   **`books` table**: `book_id`, `title`, `description`, `year_published`, `author_id`, `category_id`
*   **`authors` table**: `author_id`, `last_name`, `first_name`, `email`, `password`, `biography`
*   **`categories` table**: `category_id`, `category_name`

Each table has a unique primary key: `book_id` for the `books` table, `author_id` for the `authors` table, and `category_id` for the `categories` table.

In addition, in the `books` table, the columns `author_id` and `category_id` serve as foreign keys, meaning that they refer to the primary keys of the `authors` and `categories` tables respectively. This structure makes it possible to establish relationships between the various tables. For example, each book is associated with a specific author and a specific category, making it easy to organize and retrieve data according to these relationships.

![Image](images/image-145.png)

To create the database for this application, let's access phpMyAdmin via the following URL: `http://localhost/phpmyadmin/` after starting XAMPP. Next, let's create a new database, which we'll call `library`.

![Image](images/image-146.png)

Next, you create the three tables `authors`, `books` and `categories`. The image below shows the creation of the `authors` table. Note that the `author_id` attribute is the author identifier, of type `INT` (integer) and will be incremented automatically. To do this, check the box in the `AI` (Auto-incremented) column. The `last_name`, `first_name`, `email` and `password` attributes are of type `VARCHAR` (character string). The `biography` attribute is of type `text` to allow up to 65565 characters.

Following the same procedure, you then create the other two tables, `books` and `categories`.

![Image](images/image-147.png)

### Connection to the "library" database

In the `library` project directory, create a new file named `index.php`. Inside this file, we insert the following code to test the connection to the `library` database.

```php
<?php

// Database connection information
$host = 'localhost';
$dbname = 'library';
$username = 'root';
$password = '';

try {
    // Create an instance of the PDO class to establish the connection
    $connection = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);

    // Set PDO to generate exceptions on errors
    $connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    echo "Database connection successfully established";
} catch (PDOException $e) {
    // Connection error handling
    echo "Connection error: " . $e->getMessage();
}
?>
```

In this example:

*   The variables `$host`, `$dbname`, `$username` and `$password` contain the information needed to connect to the MySQL database.
*   Since the `library` application is developed locally, the value of `$host` is `localhost` and that of `$username` is `root`. The `$dbname` variable represents the name of the database, which in this example is `library`. The `$password` variable is empty, as no password has been defined for the `library` database.
*   We then instantiate a `PDO` object using this connection information, using the `new` keyword, which we'll explain in more detail in the section on object-oriented programming in PHP.
*   We use the syntax `mysql:host=$host;dbname=$dbname` to specify the database type (MySQL), host (server) and database name.
*   The method `setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION)` is used to set PDO's error handling mode. Here's what each part of this instruction means:
    *   `PDO::ATTR_ERRMODE` is a constant that indicates the type of attribute we're configuring. In this case, we're configuring the error handling mode.
    *   `PDO::ERRMODE_EXCEPTION` is a constant that defines the error handling mode as exception-based. This means that if an error occurs during the execution of a SQL query, `PDO` will automatically throw a `PDOException`.
