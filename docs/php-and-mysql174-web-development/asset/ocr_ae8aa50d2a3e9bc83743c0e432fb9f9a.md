# Setting Up a Connection

The basic PHP library for connecting to MySQL is called mysqli. The i stands for improved, as there was an older library called mysql. When using the mysqli library in PHP, you can use either object-oriented or procedural syntax.

You use the following line in the script to connect to the MySQL server:

```
$$db = new mysqli('localhost', 'bookoram', 'bookoram123', 'books'); $
```

This instantiates the mysqli class and creates a connection to host localhost username bookoram, and password bookoram123. The connection is set up to use the database books.

Using object-oriented approach, you can now invoke methods on this object to access the database. If you prefer a procedural approach, mysqli allows for this. To connect in a procedural function, you use

```
$$db = mysqli_connect('localhost', 'bookoram', 'bookoram123', 'books'); $
```

This function returns a resource rather than an object. This resource represents the connection to the database, if you are using the procedural approach, you will need to pass the resource in all the other mysqli functions. This is similar to the way file-handling functions, such as fopen().

Most of the functions have an object-oriented interface and a procedural interface. Generally, the differences are the procedural version function names start with mysqli and require you to pass in the resource handle obtained from mysqli_connect(). Database connections are exceptions to this rule because they can be made by the mysqli object's constructor.

The result of your attempt at connection is worth checking because none of the rest of code will work without a database connection. You do this using the following code:

```
if (mysqli_connect_errno()) {
  echo '<p>Error: Could not connect to database.<br>
  Please try again later.</p>';n  exit;
}
```

(This is the code for the object-oriented and procedural versions). The mysqli_errno() function returns an error number on error, or on success.

Note that when you connect to the database, you begin the line of code with the error suppression, @. You can, handle any errors gracefully. (This could also be with exceptions, which we have not used in this example).

Bear in mind that there is a limit to the number of MySQL connections that can exist at the same time. The MySQL parameter max_connections determines what this limit is. The purpose of this parameter and the related Apache parameter MaxClients is to let the server reject new connection requests instead of allowing machine resources to be completely used up at busy times or when software crashed.