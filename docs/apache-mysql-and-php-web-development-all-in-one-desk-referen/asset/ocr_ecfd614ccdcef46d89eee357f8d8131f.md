# Moving a database to another computer

If you want to move a database to another computer, I suggest simply copying the files. That's by far the easiest way. The following are the different methods of moving databases, depending on your operating system:

+   In Linux: Go to the mysql installation and look under the data directory. You will see a directory called data that contains a separate subdirectory for each database. You can copy that subdirectory to a shared file system, allowing you to copy it to another computer. If you don't see a data directory, try looking in /var/lib/mysql, which is another common place to find your database subdirectories.

+   In Windows: Go to the directory c:\mysql\data (or wherever you put mysql, for me, the data directory is C:\Program Files\mysql\data). In the directory, look for a subdirectory with the same name as your database. Copy that subdirectory and all its contents to a disk, CD-ROM, or shared drive, or onto the Interplanetary Potato-wave Network Connection (when they invent that). Then switch to the other computer, go to that computer's same mysql\data directory, and copy the database directory into the data directory. Make sure that as you copy, the database directory is created (or that you create it manually).

# Managing Tables

To create a table, you need a database. In this database, you can create as many tables as you want.

A table is a collection of data stored in the form of rows, which some people call records. Each record is made up of a set of columns, which some people call fields. Here's an example of a description for a table called candy:

+   name is a varchar(30).

+   weight is a double.

+   price is an int.

+   quantity is an int.

Each row of information in the candy table has a name, weight, price, and quantity. The name is of type varchar(30) (varchar(30) means a character string up to 30 characters long). The weight is a double (which is a double-precision floating point number). The price is an integer given in cents (never use floating point variables for dollars; instead, use integers for cents because integer math is more accurate than floating point math), and the quantity is an integer.