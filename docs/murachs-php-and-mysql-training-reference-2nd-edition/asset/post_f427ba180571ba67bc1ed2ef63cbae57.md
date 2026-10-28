
## How to install the book applications and databases

To get the most from this book, you need to run the applications that it presents and do the exercises at the ends of the chapters. To do that, you need to download the book applications and exercise starts from our website, and you need to run a script that installs the databases that the applications use.

### How to install the source code for this book

Figure C-7 shows how to download and install the source code for this book. This includes the source code for the applications that are presented in this book and the source code for the exercise starts and solutions.

When you finish this procedure, the book applications, exercise starts, and exercise solutions should be in the directories shown in this figure. Then, you are ready to do the exercises in this book.

### The Murach website

[www.murach.com](http://www.murach.com)

### The default installation directory for the source code

```text
/opt/lampp/htdocs
```

### The directories for the book applications, exercise starts, and solutions

```text
/opt/lampp/htdocs/book_apps
/opt/lampp/htdocs/ex_starts
/opt/lampp/htdocs/ex_solutions
```

### How to download and install the source code

1. Go to www.murach.com, and go to the page for *Murach’s PHP and MySQL (2nd Edition)*.
2. Click the “FREE Downloads” tab.
3. Select the “All Book Files” link for the regular zip file, and respond to the resulting pages and dialog boxes. This should download a file named `phps_allfiles.zip` onto your hard drive.
4. Open a terminal and change to the Downloads directory.
5. Move the zip file to the htdocs directory. To do that, you can enter:

   ```text
   mv phps_allfiles.zip /opt/lampp/htdocs
   ```

6. Change to the `/opt/lampp/htdocs` directory.
7. Unzip the file and create the directories. To do that, you can enter:

   ```text
   unzip phps_allfiles.zip
   ```

### Description

- All of the source code for this book can be downloaded from [www.murach.com](http://www.murach.com).

Figure C-7 — How to install the source code for this book

## How to create and restore the databases

Before you can run the SQL statements presented in this book, you need to create the database tables and users on the database server. The easiest way to do that is to use phpMyAdmin to run the create_db.sql file as described in figure C-8. When you use phpMyAdmin to run this file, it executes a script that creates the databases and the user described in this figure. This includes all of the tables for the databases.

As you work with the examples in this book, you may make changes to the database tables that you don’t intend to make. In that case, you may want to restore the database to its original state so your results match the results shown in this book. To do that, you can use phpMyAdmin to run the create_db.sql file a second time. This drops both databases and creates them again.

Since the _create_db directory shown in this figure is a subdirectory of the htdocs directory, the scripts within it are available to anyone who requests them from the web server. For these particular scripts, that isn’t a big problem. However, for scripts that contain sensitive data, this is a big security hole. In general, it’s considered a bad practice to store any database scripts in a subdirectory of the htdocs directory. As a result, to follow best practices, you should move the _create_db subdirectory to a directory that isn’t accessible from the web.

### The create_db.sql file

```text
/opt/lampp/htdocs/book_apps/_create_db/create_db.sql
```

### The databases that are created

| Database | Description |
|---|---|
| `my_guitar_shop1` | A simple database that’s used for the applications in sections 1 and 2. |
| `my_guitar_shop2` | An expanded version of the database that is used for the applications in sections 3 and 4. |

### A user that’s created

| User | Description |
|---|---|
| `mgs_user` | A user with privileges that allow only the use of SELECT, INSERT, UPDATE, and DELETE statements. This user is used for the database connections for most of the applications in the book. |

### How to create the databases and users for this book

1. Start phpMyAdmin as described in figure C-4.
2. Log in as the root user.
3. Click on the Import tab, click the Browse button, and select the create_db.sql file shown above. Then, click the Go button.
4. If the script executes successfully, you can use the left column to view both databases. To do that, click the plus (+) sign to expand the “my” node, and click the plus (+) sign to expand the “guitar” node.

### How to restore the databases and users for this book

- Run the procedure for creating the tables and users again. This should drop all of the tables and users before creating them again.

### Description

- If you have any problem following this procedure, chapter 3 provides a more detailed explanation of how to use phpMyAdmin to run scripts such as the create_db.sql script.

Figure C-8 — How to create and restore the databases

## Index

- $_COOKIE variable, 352-353
- $_FILES array, 758-759
- $_GET array, 54-55, 216-217
- $_POST array, 56-57, 68-69, 212, 214-217
- $_SERVER array, 690-691, 704-705
- $_SESSION array, 360-361
- $GLOBALS array, 386-387
- $this variable, 424-425
- 401 (Unauthorized) response header, 705

### A

- abs function, 280-281
- Absolute template (strtotime function), 298-299
- Abstract
  - class, 454-455
  - method, 454-455
- Action query, 106-107
- Ad hoc relationship (SQL), 592-593
- add method (DateTime object), 306-307
- add_tags function, 654-655
- Address format (email address), 492-493
- Advanced Encryption Standard (AES), 706-707
- affected_rows property (mysqli), 636-637
- Aggregate function, 596-597
- Alias
  - column, 578-579
  - table, 594-595
- Alpha
  - blending, 766-767
  - channel, 766-767
- ALTER TABLE statement, 548-549
- Anonymous function, 400-401
- Apache server, 10-11
  - starting and stopping, 24-25
  - with Linux, 846-847
  - with Mac, 826-827
  - with Windows, 810-811
- API, 732-733
  - MySQL, 614-615
- Append a string, 62-63
- Application
  - root directory, 26-27
  - server, 10-11
- Application Programming Interface (see API)
- Applications (see Book applications)
- Argument, 64-65, 382-383
  - creating object, 126-127
  - function, 162
  - list, 382-383
- Arithmetic operator, 60-61
- Array, 132-135, 313-346
  - $_GET, 54-55
  - adding elements, 316-317
  - associative, 320-325
  - built-in, 54-55
  - conversion, 272-273
  - creating, 314-315
  - deleting elements, 316-317
  - index, 314-315
  - jagged, 336-337
  - length, 314-315
  - multi-dimensional, 336-337
  - rectangular, 336-337
  - two-dimensional, 336-339
  - using for loops, 318-319
  - with variable substitution, 316-317
- array function, 134-135
- Array of arrays, 336-339
- array_count_values function, 330-331
- array_fill function, 326-327
- array_key_exists function, 330-331
- array_merge function, 326-327
- array_pad function, 326-327
- array_pop function, 328-329
- array_product function, 330-331
- array_push function, 328-329
- array_rand function, 334-335
- array_reverse function, 334-335
- array_search function, 330-331
- array_shift function, 328-329
- array_slice function, 326-327
- array_splice function, 326-327
- array_sum function, 330-331
- array_unique function, 334-335
- array_unshift function, 328-329
- array_values function, 316-317
- arsort function (array), 332-333
- AS keyword, 578-579
- ASCII character set, 272-273
- asort function (array), 332-333
- ASP.NET, 10-11
- Assertion (regular expression), 472-473
- Assigning
  - a value, 52-53
  - strings, 262-263
- Assignment operator, 52-53
- Associative array, 320-325
  - adding elements, 322-323
  - creating, 320-321
  - deleting elements, 322-323
  - foreach loops, 324-325
  - variable substitution, 322-323
- Atom (email address), 492
