# # Perspective

Now that you’ve finished with this chapter, you have the skills that you need for using PHP to work with a MySQL database at a professional level. In the next chapter, you’ll learn more about how you can apply those skills.

# # Terms

+   - Application Programming Interface (API)
+   - PHP extension for the MySQL API
+   - PHP Data Objects (PDO)
+   - database abstraction layer
+   - dynamic SQL statement
+   - prepared SQL statement
+   - named parameter
+   - question mark parameter
+   - unnamed parameter
+   - object-oriented style
+   - procedural style
+   - error suppression operator

# # Summary

+   - MySQL provides an *Application Programming Interface (API)* that specifies how any application can work with MySQL.
+   - PHP provides three *extensions* for working with the MySQL API: the mysql extension, the mysqli extension, and the PDO MySQL driver extension.
+   - *PHP Data Objects (PDO)* is a *database abstraction layer* specifically for database applications. PDO uses the PDO MySQL driver extension to communicate with MySQL, but it can use other drivers to communicate with other databases.
+   - When you use PDO to execute SQL statements, you can choose between three error modes.
+   - When compared to *dynamic SQL statements*, using *prepared statements* provides improved performance and security.
+   - A *named parameter* begins with a colon (:) followed by the name of the parameter.
+   - An *unnamed parameter* (also known as a *question mark parameter*) uses a question mark (?) to indicate the location of the parameter in the SQL statement.
+   - The mysqli extension includes a *procedural style* that uses functions to work with the database, and it includes an *object-oriented style* that uses objects, methods, and properties to work with the database.