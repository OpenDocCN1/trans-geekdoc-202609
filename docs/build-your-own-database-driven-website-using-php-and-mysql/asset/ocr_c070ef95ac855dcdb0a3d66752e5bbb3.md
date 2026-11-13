occur if the server is in the middle of making changes to the files at the time of the disturbance, as the files may be left in a corrupt or inconsistent state. Since this type of damage can be subtle, it can go undetected for days, weeks, or even months. As a result, by the time you do finally discover the problem, all your backups may contain the same corruption.

Chapter 15 of the MySQL Reference Manual (http://www.mysql.com/documentation/mysql/commented/manua1.php?section=Maintenance) describes the myisamchk utility that comes with MySQL, and how to use it to check and repair your MySQL data files. While that chapter is recommended reading for anyone who wants to set up a heavy-duty preventive maintenance schedule for their MySQL server, we'll cover all the essentials here.

Before we go any further, though, it's important to realize that the myisamchk program expects to have sole access to the MySQL data files that it checks and modifies. If the MySQL server works with the files at the same time, and makes a modification to a file that myisamchk is in the middle of checking, myisamchk might incorrectly detect an error and try to fix it -- which in turn could trip up the MySQL server! Thus, to avoid making things worse instead of better, it's usually a good idea to shut down the MySQL server while you're working on the data files. Alternatively, shut down the server just long enough to make a copy of the files, and then do the work on the copies. When you're done, shut down the server again briefly to replace the files with the new ones (and perhaps apply any update logs that were made in the interim).

The MySQL data directory isn't too difficult to understand. It contains a subdirectory for each database, and each of these subdirectories contains the data files for the tables in the corresponding database. Each table is represented by three files, which have the same name as the table, but three different extensions. The tblName.frm file is the table definition, which keeps track of which columns are contained in the table, and their type. The tblName.MYD file contains all the table data. The tblName.MYI file contains any indexes for the table (for example, it might contain the lookup table that helps the table's primary key column speed up queries that are based on this table).

To check a table for errors, just run myisamchk (in the MySQL bin directory) and provide either the location of these files and the name of the table, or the name of the table index file:

```
% myisamchk /usr/local/mysql/var/dbName/tblName
% myisamchk /usr/local/mysql/var/dbName/tblName.MYI
```

Either of the above will perform a check of the specified table. To check all tables in the database, use a wildcard: