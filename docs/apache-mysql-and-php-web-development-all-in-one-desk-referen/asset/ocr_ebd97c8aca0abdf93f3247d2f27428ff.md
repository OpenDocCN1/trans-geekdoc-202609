# # Chapter 2: Managing Databases and Tables

# ## In This Chapter

+   - Finding out what databases are available
+   - Creating, deleting, backing up, and moving a database
+   - Setting user privileges for a database
+   - Creating a table and dropping (or deleting) a table
+   - Adding data to a table and looking at the data in a table
+   - Getting information about a table
+   - Seeing what tables are in a database

Before going any further, I want to clear up some definitions. In the world of databases, people have different definitions for the same words. (Isn't that just like a bunch of computer people?) However, most companies that develop database products all agree on the definitions of these terms. I want to share these definitions with you so you, me, and all the other database people on the planet can see eye to eye (or at least computer-interface-to-computer-interface, as the case may be).

The following are informal definitions that most people agree on:

+   - **Table**: A set of data organized into rows and columns.
+   - **Database**: A collection of tables. In MySQL, you can have several distinct databases.
+   - **Row**: A single record within a database. The term *record* has become nonstandard, and today, people prefer the term *row*.
+   - **Column**: A single field within a database. A row (or record) is made up of several columns (or fields) such as `name`, `email_address`, and `phone_number`. As with *record*, the term *field* has become nonstandard; these days people prefer the term *column*.

In this chapter, I talk about various issues involved in setting up databases and tables in MySQL, along with such important topics as how to back up your databases and how to automate various tasks.