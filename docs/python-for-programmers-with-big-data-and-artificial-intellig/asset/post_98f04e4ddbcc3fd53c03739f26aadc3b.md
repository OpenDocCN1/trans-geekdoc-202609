
descending order or no particular order at all.

Each column represents a different data attribute. Rows are unique (by primary key) within a table, but particular column values may be duplicated between rows. For example, three different rows in the Employee table’s Department column contain number 413.

## Selecting Data Subsets

Different database users are often interested in different data and different relationships among the data. Most users require only subsets of the rows and columns. Queries specify which subsets of the data to select from a table. You use Structured Query Language (SQL) to define queries. For example, you might select data from the Employee table to create a result that shows where each department is located, presenting the data sorted in increasing order by department number. This result is shown below. We’ll discuss SQL shortly.

click here to view code image

| Department | Location |
|---|---|
| 413 | New Jersey |
| 611 | Orlando |
| 642 | Los Angeles |

## SQLite

The code examples in the rest of section 16.2 use the open-source SQLite database management system that’s included with Python, but most popular database systems have Python support. Each typically provides a module that adheres to Python’s Database Application Programming Interface (DB-API), which specifies common object and method names for manipulating any database.

## 16.2.1 A books Database

In this section, we’ll present a books database containing information about several of our books. We’ll set up the database in SQLite via the Python Standard Library’s sqlite3 module, using a script provided in the ch16 example’s folder’s sql subfolder. Then, we’ll introduce the database’s tables. We’ll use this database in an IPython session to introduce various database concepts, including operations that create, read, update and delete data —the so-called CRUD operations. As we introduce the tables, we’ll use SQL and pandas DataFrames to show you each table’s contents. Then, in the next several sections, we’ll discuss additional SQL features.

## Creating the books Database

In your Anaconda Command Prompt, Terminal or shell, change to the ch16 examples folder’s sql subfolder. The following sqlite3 command creates a SQLite database named books.db and executes the books.sql SQL script, which defines how to create the database’s tables and populates them with data:

```
sqlite3 books.db < books.sql
```

The notation < indicates that books.sql is input into the sqlite3 command. When the command completes, the database is ready for use. Begin a new IPython session.

### Connecting to the Database in Python

To work with the database in Python, first call sqlite3's **connect function** to connect to the database and obtain a **Connection** object:

click here to view code image

```
In [1]: import sqlite3

In [2]: connection = sqlite3.connect('books.db')
```

### authors Table

The database has three tables—authors, author_ISBN and titles. The authors table stores all the authors and has three columns:

- **id**—The author's unique ID number. This integer column is defined as **autoincremented**—for each row inserted in the table, SQLite increases the id value by 1 to ensure that each row has a unique value. This column is the table's primary key.
- **first**—The author's first name (a string).
- **last**—The author's last name (a string).

### Viewing the authors Table's Contents

Let's use a SQL query and pandas to view the authors table's contents:

click here to view code image

```
In [3]: import pandas as pd

In [4]: pd.options.display.max_columns = 10

In [5]: pd.read_sql('SELECT * FROM authors', connection,
   ....:               index_col=['id'])
   ....:
```

| id | first | last |
|---|---|---|
| 1 | Paul | Deitel |
| 2 | Harvey | Deitel |
| 3 | Abbey | Deitel |
| 4 | Dan | Quirk |
| 5 | Alexander | Wald |

Pandas function **read_sql** executes a SQL query and returns a **DataFrame** containing the query's results. The function's arguments are:

- a string representing the SQL query to execute,
- the SQLite database's **Connection** object, and in this case
- an index_col keyword argument indicating which column should be used as the DataFrame's row indices (the author's id values in this case).

As you'll see momentarily, when index_col is not passed, index values starting from 0 appear to the left of the DataFrame's rows.

A SQL SELECT query gets rows and columns from one or more tables in a database. In the query:

```
SELECT * FROM authors
```

the asterisk (*) is a wildcard indicating that the query should get all the columns from the authors table. We'll discuss SELECT queries in more detail shortly.

### titles Table

The titles table stores all the books and has four columns:

- isbn—The book's ISBN (a string) is this table's primary key. ISBN is an abbreviation for "International Standard Book Number," which is a numbering scheme that publishers use to give every book a unique identification number.
- title—The book's title (a string).
- edition—The book's edition number (an integer).
- copyright—The book's copyright year (a string).

Let's use SQL and pandas to view the titles table's contents:

click here to view code image

```
In [6]: pd.read_sql('SELECT * FROM titles', connection)
```

| isbn | title | edition | copyright |
|---|---|---|---|
| 0135404673 | Intro to Python for CS and DS | 1 | 2020 |
| 0132151006 | Internet & WWW How to Program | 5 | 2012 |
| 0134743350 | Java How to Program | 11 | 2018 |
| 0133976890 | C How to Program | 8 | 2016 |
| 0133406954 | Visual Basic 2012 How to Program | 6 | 2014 |
| 0134601548 | Visual C# How to Program | 6 | 2017 |
| 0136151574 | Visual C++ How to Program | 2 | 2008 |
| 0134448235 | C++ How to Program | 10 | 2017 |
| 0134444302 | Android How to Program | 3 | 2017 |
| 0134289366 | Android 6 for Programmers | 3 | 2016 |

### author_ISBN Table

The author_ISBN table uses the following columns to associate authors from the authors table with their books in the titles table:

- id—An author's id (an integer).
- isbn—The book's ISBN (a string).

The `id` column is a **foreign key**, which is a column in this table that matches a *primary-key* column in another table—in particular, the `authors` table's `id` column. The `isbn` column also is a foreign key—it matches the `titles` table's `isbn` primary-key column. A database might have many tables. A goal when designing a database is to *minimize data duplication* among the tables. To do this, each table represents a specific entity, and foreign keys help link the data in *multiple* tables. The primary keys and foreign keys are designated when you create the database tables (in our case, in the `books.sql` script).

Together the `id` and `isbn` columns in this table form a *composite primary key*. Every row in this table *uniquely* matches *one author* to *one book's ISBN*. This table contains many entries, so let's use SQL and pandas to view just the first five rows:

click here to view code image

```
In [7]: df = pd.read_sql('SELECT * FROM author_ISBN', connection)

In [8]: df.head()
```

| id | isbn |
|---|---|
| 0 | 0134289366 |
| 2 | 0134289366 |
| 5 | 0134289366 |
| 1 | 0135404673 |
| 2 | 0135404673 |

Every foreign-key value must appear as the primary-key value in a row of another table so the DBMS can ensure that the foreign-key value is valid. This is known as the **Rule of Referential Integrity**. For example, the DBMS ensures that the `id` value for a particular `author_ISBN` row is valid by checking that there is a row in the `authors` table with that `id` as the primary key.

Foreign keys also allow *related data* in *multiple tables* to be *selected* from those tables and combined—this is known as **joining** the data. There is a **one-to-many relationship** between a primary key and a corresponding foreign key—one author can write many books, and similarly one book can be written by many authors. So a foreign key can appear *many* times in its table but only *once* (as the primary key) in another table. For example, in the `books` database, the ISBN 0134289366 appears in several `author_ISBN` rows because this book has several authors, but it appears only once as a primary key in `titles`.

### Entity-Relationship (ER) Diagram

The following **entity-relationship (ER) diagram** for the `books` database shows the database's *tables* and the *relationships* among them:

![](img/34b7fc2f1ee27beb73bca14927d42340_737_0.png)
