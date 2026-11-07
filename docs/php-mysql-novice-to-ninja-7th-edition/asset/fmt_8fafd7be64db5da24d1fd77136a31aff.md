
# MySQL Workbench Basics

Most MySQL commands are not case-sensitive, which means you can type `CREATE DATABASE`, `create database`, or even `CrEaTe DaTaBaSe`, and it will know what you mean. Database names and table names, however, are case-sensitive when the MySQL server is running on an operating system with a case-sensitive file system (such as Linux, macOS, or when running inside Docker).

Additionally, table, column, and other names must be spelled exactly the same when they’re used more than once in the same query.

For consistency, this book will respect the accepted convention of typing database commands in all capitals, and database entities (databases, tables, columns, and so on) in all lowercase.

This also makes it easier for people (like you!) to read the queries. MySQL doesn’t care, but you’ll be able to identify a command quickly and easily because it’s in capitals, and a reference to a table, column or database because it’s in lowercase.

Once your database has been created, it will appear in the `SCHEMAS` list on the left-hand side.

![The Internet Joke Database schema](Images/mysql-workbench-schema-ijdb.png)

Now that you have a database, you need to tell MySQL Workbench that you want to use it. To do this, simply double-click the newly created schema and its name will go bold. You can only have one schema selected at a time, and you need to tell MySQL Workbench which you’d like to use.

![The ijdb schema selected](Images/mysql-workbench-schema-selected.png)

You’re now ready to use your database. Since a database is empty until you add tables to it, our first order of business is to create a table that will hold your jokes. (Now might be a good time to think of some!)

## Creating a Table

If you expand your newly created `ijdb` schema by pressing the arrow next to the name, you’ll see a few entries.

![The ijdb schema expanded](Images/mysql-workbench-schema-expanded.png)

The only one we’re concerned with for the purposes of this book is the `Tables` entry. Because your schema has just been created, it doesn’t have any tables.

A table describes the format of your data. You’ll need to know the *structure* of the data you’d like to store. Before creating a table, you need to think about exactly what you want to store. For the jokes example, we want to store these pieces of information:
*   the text of the joke
*   the date it was added

Along with the text and date, we’ll also need some way to identify each joke. To do this, we’ll give each joke a unique ID.

Each piece of information is placed in a field in the table, and each field has a “type”. **Types** can be used to store data in different formats like numbers, text and dates.

There are three main kinds of types that you’ll encounter:
*   numbers, for storing numeric values
*   text, for storing strings
*   dates/times, for storing timestamps

There are lots of column types in MySQL, but you only really need an understanding of three for most purposes!

To create a table using MySQL Workbench, expand the database in the `SCHEMAS` list, then right-click on the `Tables` entry and select `Create Table`.

The middle panel of the window will change to show you something like what’s pictured below.

![MySQL Workbench New Table window](Images/mysql-workbench-newtable.png)

Every table is given a name to identify it and a series of columns. Firstly, enter the table’s name as `joke` and add the following columns in the column list:
*   `id`, which will act as a unique identifier for each joke so we can retrieve it later
*   `joketext`, which will store the text of the joke
*   `jokedate`, which will store the date the joke was added

![Creating the joke table](Images/mysql-workbench-newtable-1.png)

You’ll notice there’s a second column called `Datatype`. Each column in a database table must be assigned a type. The three types we will need are:
*   `INT`, meaning “integer” for the numeric `jokeid`
*   `TEXT`, to store some text for the joke
*   `DATE`, to store the date the joke was published

This helps to keep your data organized, and allows you to compare the values within a column in powerful ways, as we’ll see later.

If we were to stop setting up the table at this point, you could start adding records to the table (and I’ll show you how to do that very shortly!). However, you’d have to provide all three pieces of information: the joke ID, the joke text, and the joke date. This means that, to add the next joke, you’d need to keep track of how many were in there in order to assign the next ID.

This sounds like extra work, but fortunately MySQL Workbench provides a convenient way of avoiding it. Along with the name of the column and data type it stores, you’ll notice there’s a series of checkboxes for each field in the table.

There are three we’re interested in here for our ID field:
*   `PK`. This means “primary key”. Ticking this box specifies that this column is to act as a unique identifier for the entries in the table, so all values in this column must be unique, ensuring that no two jokes will share the same ID.
*   `NN`. This stands for “Not Null”, and means that when a record is added, a value must be placed in the field. For our ID column, ticking this box tells MySQL not to accept jokes that don’t have an ID.
*   `AI`. This is the clever bit that will save us work. No, “AI” is not “Artificial Intelligence”, some kind of computer-brain doing our work for us. In this case, it stands for “Auto Increment”, and by checking this box (and it’s only allowed on `INT` fields!), whenever a record (in our case, a joke) is added to the table, it will automatically be assigned the next available ID. This is a real time saver and a feature worth remembering.

Your table should now look like the one pictured below.

![The joke table complete](Images/mysql-workbench-newtable-2.png)

Press the `Apply` button, and the joke table will be created. You’ll see the following query appear in the window:
```
CREATE TABLE `ijdb`.`joke` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `joketext` TEXT NULL,
  `jokedate` DATE NULL,
  PRIMARY KEY (`id`));
```

You’ll notice a lot of the same information has been repeated that we entered into the GUI. The GUI just generates this code for us, which is a much quicker and easier way of creating tables than remembering all of the syntax and vocabulary needed to write the query yourself.

As a developer, you don’t need to create tables often. But you *will* need to interact with them—adding and removing records and retrieving them from the database—so it’s worth spending time learning how to write queries to do this. For creating tables, however, it’s usually a lot quicker and easier to use the MySQL Workbench GUI, because once a table has been created, you won’t need to write another `CREATE TABLE` statement.

We need to look at just one more task: deleting a table. This task is frighteningly easy, so be careful! If you delete a table, you can’t get it back.

In the `SCHEMAS` list, right-click on the table you want to delete and select `Drop Table`. *Don’t* run this command with your joke table unless you actually do want to be rid of it. If you really want to try it, be prepared to recreate your joke table from scratch. When you delete a table, the table is removed permanently, along with any data stored inside it. *There’s no way to recover the data after the table has been dropped*, so be very careful when using this command!

## Adding Data

Now that the table has been created, it’s time to add some data to it. Although this can be done using MySQL Workbench’s GUI, this time we’re going to write the query ourselves. Eventually, we’ll need to be able to write our own database queries directly from `PHP`, so it’s good to get some practice writing them.
