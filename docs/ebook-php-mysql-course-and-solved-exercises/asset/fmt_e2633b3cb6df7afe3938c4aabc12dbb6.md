
By using this error handling mode, errors related to the execution of SQL queries will be automatically converted into `PDOException` exceptions, making them easier to handle in the code using `try-catch` blocks. This makes error handling more explicit and efficient.

Finally, we display a message indicating that the connection to the database has been successfully established, or an error message in the event of a connection problem.

If you test this code by executing the `index.php` script, and if the connection is successful, you will obtain the following result:

![Image](images/image-148.png)

However, if an error occurs in the database connection information, you will receive a message similar to the following result:

![Image](images/image-149.png)

## Conclusion

This chapter has given us a detailed understanding of the process of connecting to a MySQL database using PHP. We've explored the `PDO` object method in detail. We've learned how to configure and handle connection errors effectively. We also explored the concepts of primary and foreign keys in database design, as well as practical steps for creating a database and tables in phpMyAdmin. Finally, we look at a concrete example of database connection and error handling. This chapter is a first step towards understanding MySQL database management in the context of web development with PHP. In subsequent chapters, we'll look at SQL queries for database management.

# Chapter 11: Inserting, retrieving and displaying data from a database

In this chapter, we'll cover the various steps involved in inserting, retrieving and displaying data from a MySQL database using PHP and the `PDO` extension. We'll explore SQL queries for inserting new data, as well as `PDO` methods for executing these queries and displaying the results efficiently in our web applications.

We'll explore `PDO` methods for executing SQL insert queries and inserting new data into a database. This will include using SQL queries prepared with parameters and executing the query with `execute()`.

We'll discuss various techniques for retrieving data inserted in a database and displaying it in our web applications. This will also include the use of loops to browse result records and display data in HTML tables, as well as other presentation formats.

This chapter will be covered by developing a mini library project and will provide you with a practical, in-depth understanding of how to insert, retrieve and display data from a MySQL database in their PHP web applications using the `PDO` extension, while focusing on security and good development practices.

## Data insertion with SQL

To illustrate the process of inserting data into a MySQL database, we're going to create an attractive insert form for the "authors" table in our "library" database. The first step is to create the Insert form in the `index.php` file, and we'll use CSS code to style the form. I'm assuming you know the basics of CSS, but if not, I suggest you consult my book "HTML & CSS: from Beginner to Expert".

### Insertion form (index.php)

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Author Inscription</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
 <form action="author_registration.php" method="POST">
 <h2>Author registration</h2>
 <input type="text" name="lastname" placeholder="Last Name"><br>
 <input type="text" name="firstname" placeholder="First Name"><br>
 <input type="email" name="email" placeholder="Email"><br>
 <input type="password" name="password" placeholder="Password"><br>
 <textarea name="biography" placeholder="biography"></textarea><br>
 <input type="submit" value="Save">
 </form>
</body>
</html>
```

This HTML code creates an author inscription form with fields for last name, first name, email and password. When the form is submitted, the data is sent to the file `author_registration.php` page via the `POST` method. The form is styled using an external style sheet `style.css` with the code line:

```
<link rel="stylesheet" href="style.css">
```

### CSS style sheet

Next, we create a new `style.css` file in which we put the following code to style the form:

```
body {
 font-family: Arial, sans-serif;
 background-color: #f4f4f4;
 margin: 0;
 padding: 0;
 display: flex;
 justify-content: center;
 align-items: center;
 height: 100vh;
}
form {
 background-color: #fff;
 padding: 20px;
 border-radius: 8px;
 box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
 width: 400px;
 margin: auto; /* Ajout de cette ligne */
}
input {
 width: calc(100% - 20px);
 padding: 10px;
 border: 1px solid #ccc;
 border-radius: 4px;
 margin-bottom: 15px;
}
textarea {
 width: calc(100% - 20px);
 padding: 10px;
 border: 1px solid #ccc;
 border-radius: 4px;
 margin-bottom: 15px;
}
input[type="submit"] {
 background-color: #007bff;
 color: #fff;
 border: none;
 padding: 10px 20px;
 cursor: pointer;
 border-radius: 4px;
 display: block;
 margin: 0 auto;
}
input[type="submit"]:hover {
 background-color: #0056b3;
}
```

The form's `action` attribute indicates the path to a file called `author_registration.php`, responsible for retrieving the data submitted by the form and inserting it into the `authors` table of the `library` database. Let's create this file at the root of the `library` project.

Running `index.php` displays the following form:

![Image](images/image-150.png)

### Data processing and insertion

#### author_registration.php

```
<?php
 // Retrieve form data
 $lastname = $_POST['lastname'];
 $firstname = $_POST['firstname'];
 $email = $_POST['email'];
 $password = $_POST['password'];
 $biography = $_POST['biography'];
 // Database connection
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");
 $connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
 // Prepare insertion request
 $request = $connection->prepare("INSERT INTO authors (last_name, first_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)");
 // Bind values to query parameters
 $request->bindParam(':lastname', $lastname);
 $request->bindParam(':firstname', $firstname);
 $request->bindParam(':email', $email);
 $request->bindParam(':password', $password);
 $request->bindParam(':biography', $biography);
 // Execute query
 $result = $request->execute();
 // Verify successful insertion
 if ($result) {
 echo "Author is registered successfully!";
 } else {
 echo "Error registered author.";
 }
?>
```

This PHP code begins by retrieving the data transmitted from the previous HTML form via the `POST` method. Next, a connection to the MySQL database is established using the `PDO` object with the credentials provided (host name, database name, username and password).

Next, an insertion SQL query is prepared with the `INSERT INTO` statement to add a new row to the `authors` table. The values of the `lastname`, `firstname`, `email` and `password` fields are bound to the query parameters using the `bindParam()` method.

Once the values have been bound to the parameters, the query is executed with the `execute()` method, and the result of the execution is stored in the `$result` variable.

Finally, the code checks whether the insertion was successful by verifying the value of `$result`. If true, a message is displayed indicating that the author has been registered successfully. Otherwise, an error message is displayed, indicating that there was a problem registering the author.

Detailed explanation:
