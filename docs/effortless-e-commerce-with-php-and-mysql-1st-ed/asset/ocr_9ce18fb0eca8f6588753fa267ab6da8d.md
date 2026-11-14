The most important of these is security. Because routines are stored within the database itself, the programming interface—PHP in this case—will not have direct access to the underlying tables and data. In fact, the interface wouldn’t even need to know what tables and columns exist when stored procedures are used.

You can get better performance with a stored procedure in two ways. First, as you’ll see, stored procedures require that less data be sent to the database, because you’ll mostly be sending just values without any SQL (this is another security benefit). Second, stored procedures can be cached and managed so that the database executes them as efficiently as possible.

The cleaner model-controller separation is obvious: more logic goes into the database, removing SQL from the PHP code.

As for the increased application portability, this is both true and not. Because the logic will be stored in the database, other interfaces, like a Java application or the command line, can invoke the stored procedures in exactly the same way (this may or may not be beneficial to you). On the other hand, with the logic stored in the database, you could not as easily change the database application in use. But to be frank, I’ve been doing Web development for over a decade now and have had to change a Web application from one database server to another...just about never.

Stored procedures are created using this SQL command:

```
```
CREATE PROCEDURE name (arguments)
BEGIN
CODE
END
```
```

The procedure’s name can contain letters, numbers, and the underscore, but avoid using the same name as an existing MySQL function, keyword, database name, or table name.

For the procedure’s arguments, give each argument a name and a MySQL-defined type, with multiple arguments separated by a comma:

```
```
CREATE PROCEDURE do_this(age INT, name VARCHAR(20)...
```
```

Again, stick to letters, numbers, and the underscore, and avoid using existing names and keywords for the argument names. Note that these are MySQL stored procedure variables, not PHP ones, so there are no dollar signs. The variable types are also basic, omitting extra qualities such as UNSIGNED or NOT NULL.

> **note**
> 
> I ran a few informal benchmarks and saw this book's stored procedures running significantly faster than the literal queries.

> **note**
> 
> Stored procedures are associated with a specific database and become part of its definition.

> **note**
> 
> As stored procedures transfer more of the processing load from the Web server to the database server, you may find the database server becomes overloaded more quickly.

> **note**
> 
> Banks and other extremely secure environments rely on stored procedures for increased security.

> **note**
> 
> You must use parentheses for the procedure’s arguments, even if there are none.