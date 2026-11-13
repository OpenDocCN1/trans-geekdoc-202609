```
mysql> use guestbook;
Database changed
mysql> create table guestbook
-> (
-> 	 name 			 varchar(40) null,
-> 	 location 		 varchar(40) null,
-> 	 email 		 varchar(40) null,
-> 	 	 . url 			 varchar(40) null,
-> 	 comments 		 text null
-> ) 
-> ;
Query OK. 0 rows affected (0.00 sec)
mysql>
```

Then you have to give your application permission to use the table:

```
mysql> grant delete, insert, select, update on guestbook
-> 		 to nobody@localhost identified by 'ydobon';
Query OK. 0 rows affected (0.00 sec)
```

Then you issue a quick statement that forces the server to re-read the permissions tables, effectively putting the new ones into effect:

```
mysql> FLUSH PRIVILEGES;
```

So now you have a database named guestbook and a table, also named guestbook, within the database. Now it's time to write an application in PHP that will enable you to insert, edit, and view information kept in this guestbook.

# Your PHP script

Now's the time to move to the text editor. In the course of configuring your Web server, you need to let it know which files should be handed off to PHP so the engine can interpret the page. Most often these files have a .php extension, though it is possible to have PHP interpret anything, including .html files. These scripts live inside the folder designated to hold Web pages. For Apache, this is usually /htdocs.

# BASIC SYNTAX

One neat thing about PHP is that it lets you move between straight HTML and commands that are part of the PHP programming language. It works like this: The sections of your script between the opening tag (<?php) and the closing tag (?>) are interpreted by the PHP engine, and portions not within these tags are treated as plain HTML. Check out the following PHP page.