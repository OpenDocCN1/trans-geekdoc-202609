I specified the database name, phpbase, but I had to put .* after the name, meaning I'm granting these privileges to all tables inside the phpbase database. And yes, in this case you use the * wildcard rather than the % wildcard as you do elsewhere. It's just an annoying rule to follow; that's all. (You can't leave off the .*, or mysql will think you're referring to a table called phpbase, which you're not, and you'll get an error.)

Now you can test the restrictions. Exit mysql by typing quit and then log back in as the phpuser user:

```
mysql -u phpuser -p
```

You will be prompted for a password; go ahead and enter it. Then, after you're inside mysql, you should be limited on what you can do as the phpuser user. For example, try accessing the system database:

```
use mysql
```

If the restrictions are working, you will see an error message:

```
ERROR 1044: Access denied for user: 'phpuser@localhost' to database 'mysql'
```

However, you can access the phpbase database:

```
use phpbase
```

which results in this message:

```
Database changed
```

But you can't create a new table from this username. Generally that's fine, because you probably don't want your .php files creating a new table. Instead, you'll create the table while logged into mysql as root, and then later, your .php files will modify the table only by adding data, removing data, or modifying the data in the table.

In this section, I showed you how to set the privileges. Now, you'll be able to perform the basic access typically required by a PHP program, as I explain in Book VI, Chapter 4.