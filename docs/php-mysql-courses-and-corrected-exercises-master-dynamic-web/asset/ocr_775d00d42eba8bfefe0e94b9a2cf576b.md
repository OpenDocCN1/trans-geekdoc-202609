Finally, the code checks whether the insertion was successful by verifying the value of $result. If true, a message is displayed indicating that the author has been registered successfully. Otherwise, an error message is displayed, indicating that there was a problem registered the author.

# Detailed explanation:

```
$query = $connection->prepare("INSERT INTO authors (last_name, first_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)");
```

This line of code prepares an insert SQL query to be executed later in the database. Here's a detailed explanation:

**$connection->prepare()** : This is a method of the PDO object that prepares a SQL query for execution. It returns a PDOStatement object representing the prepared query.

"INSERT INTO authors (last_name, first_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)" : This is the prepared insertion SQL query. It tells the database to insert a new row in the "authors" table with the values supplied for the "last_name", "first_name", "email", "password" and "biography" columns. The column values are represented by named parameter tags (":lastname", ":firstname", ":email", ":password", ":biography"), which will be linked to the values supplied when the query is run.

The query structure is as follows:

+   • INSERT INTO authors: Indicates an insertion request in the "authors" table.