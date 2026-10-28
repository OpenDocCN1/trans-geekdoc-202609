
## A database design tool

### An introduction to MySQL Workbench

We chose to introduce MySQL Workbench in this book partly because it’s available for free and runs on most modern operating systems. However, it also makes it easy to create visually appealing database diagrams as summarized in figure 16-14. In addition, it provides functionality that allows you to generate a diagram from an existing MySQL creation script or to generate a creation script from a database diagram. Beyond that, MySQL Workbench lets you run SQL queries and administer the MySQL server.

To install MySQL Workbench, you can go to the MySQL Workbench website and follow the instructions there. This is similar to installing other programs for your operating system. Then, when you start MySQL Workbench, it displays the Home page that’s shown in this figure. To work with database diagrams (also known as models), you click on one of the options in the Models section.

**The MySQL Workbench website**

http://www.mysql.com/products/workbench/

**The Home page**

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_556_0.png)

**MySQL Workbench...**

- Lets you create and edit diagrams.
- Lets you define the tables, columns, and indexes for a database.
- Lets you define the relationships between the tables in a database.
- Lets you generate a diagram from a SQL creation script.
- Lets you generate a SQL creation script from a diagram.

**How to install MySQL Workbench**

1. Go to the MySQL Workbench website shown above.
2. Download the version for your system.
3. Run the installer or setup file and respond to the prompts.

**Description**

- MySQL Workbench is a database design tool that’s available for free and runs on most modern operating systems.

Figure 16-14   An introduction to MySQL Workbench

**MySQL Workbench**

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_558_0.png)

**Description**

- To create a new model, select the File→New Model command.
- To create a new diagram, select the Model→Add Diagram command.
- To import tables from an existing creation script, select the File→Import→Reverse Engineer MySQL Create Script command.
- To export a database creation script from the diagram, select the File→Export→Forward Engineer MySQL Create Script command.
- To add a table to a diagram, click the Place New Table button in the toolbar. Then, click on the diagram where you want to add the table.
- To edit a table, double-click on the table. Then, use the pane that appears across the bottom of the window to modify the properties of the table, its columns, its indexes, and its foreign keys.
- To define the relationships between tables, click one of the relationship buttons in the toolbar. Then, click on the tables. To edit or delete a relationship, right-click on the relationship icon and select the appropriate command.

### Perspective

Database design is a complicated subject. Because of that, it’s impossible to teach you everything you need to know in a single chapter. With the skills you’ve learned in this chapter, however, you should be able to design databases of your own.

One aspect of database design that isn’t covered in this chapter is designing the security of the database. Among other things, that involves creating database users and assigning permissions for each user. In the next chapter, you’ll learn how to get started with database security.

### Terms

- database administrator (DBA)
- data structure
- entity
- attribute
- instance
- entity-relationship (ER) modeling
- computer-aided software engineering (CASE)
- primary key
- composite key
- foreign key
- one-to-many relationship
- many-to-many relationships
- linking table
- one-to-one relationship
- referential integrity
- orphaned row
- declarative referential integrity (DRI)
- foreign key constraint
- normalization
- data redundancy
- normal forms
- index
- composite index
- derived data
- denormalization

### Summary

- Databases are often designed and maintained by *database administrators (DBAs)*.
- A table in a relational database typically represents an object, or *entity*, in the real world. Each column of a table is used to store an *attribute* associated with the entity, and each row represents one *instance* of the entity.
- To model a database and the relationships between its tables after a real-world system, you can use a technique called *entity-relationship (ER) modeling*.
- You can use a *CASE (computer-aided software engineering) tool* to help you design a database.
- Each table should have a *primary key* that uniquely identifies each row. If two tables have a *one-to-many relationship*, you may need to add a *foreign key* column to the table on the “many” side.

5. Look on the left side of the window until you find the seven tables that were created. Drag all seven tables from the catalog tree to the diagram.

6. Double-click the Products table to display a pane across the bottom of the window. Click the Columns tab to review the column definitions for that table. Then, click the close button on the Products tab to close the pane.

7. Add the arrows that show the relationships between these tables. To do that, click the “Place a relationship using existing columns” link, click the column for the foreign key, and click the column for the primary key. Note how this identifies the foreign keys in the tables. If you make a mistake, you can right-click on the relationship arrow to delete it.

8. Save the diagram with a name of my_guitar_shop3.mwb.

9. When you’re done, review the diagram. There should be a one-to-many relationship between six of the tables. However, the administrators table is a supporting table that isn’t related to any of the other tables.

### Exercise 16-2   Create some simple database designs

In this exercise, you can use your preferred database design tool. If you don’t already have a preference, we recommend using MySQL Workbench.

1. Create a diagram for a database of music albums created by music artists. Each artist may have one or more albums, and each album may have one or more tracks. Keep track of this data: artist name, album name, album release date, track name, and track time.

2. Create a diagram for a database of members of groups within an association. Assume that each member can belong to any number of groups and that each group can have any number of members. Keep track of this data: member name, member email address, member phone number, group name, and group description.

## 17 How to use SQL to create a database

Now that you’ve learned how to design a database, you’re ready to learn how to implement your design. To do that, you use the set of SQL statements that are known as the data definition language (DDL). In this chapter, you’ll learn how to use the DDL statements that work with tables and indexes. You’ll also learn how to use the DDL statements that work with users and privileges.

If you use MySQL Workbench to design your database, you can generate a SQL script that contains the DDL statements needed to create the database. Then, you can run that script to create the database. However, it’s still important to understand DDL statements for several reasons. First, understanding DDL statements helps you understand how to use MySQL Workbench. Second, you may need to edit the DDL statements in a generated script. Third, you may need to write DDL statements on your own to modify a database that already exists.

- **How to work with databases** ........................................540
  - How to create a database .............................................540
  - How to select a database .............................................540
  - How to drop a database ...............................................540
- **How to work with tables** ............................................542
  - An introduction to MySQL data types ................................542
  - How to create a table ................................................544
  - How to code a primary key ............................................546
  - How to alter a table ..................................................548
  - How to drop a table ...................................................550
- **How to work with indexes** ............................................552
  - How to create an index ................................................552
  - How to drop an index ..................................................552
- **How to work with users and privileges** ..............................554
  - A summary of privileges ..............................................554
  - How to create, rename, and drop users ................................556
  - How to grant privileges ..............................................558
  - How to revoke privileges .............................................560
  - How to view privileges ................................................562
- **Other skills for creating a database** ...............................564
  - How to load data from text files .....................................564
  - How to dump a database to a SQL script ................................566
- **The script for the Guitar Shop database** ............................568
- **Perspective** ........................................................572
