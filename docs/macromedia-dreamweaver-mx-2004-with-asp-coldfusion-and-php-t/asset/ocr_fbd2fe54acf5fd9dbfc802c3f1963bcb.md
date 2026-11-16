![](bbox=[0.058, 0.066, 0.706, 0.446])

One of the benefits of phpMyAdmin is that it lets users generate tables using SQL stored in an external text file. You can use this feature to install the newland_tours database on a remote server running phpMyAdmin. Before you can do so, you'll need to copy the newland_tours.sql file from the Lesson08/Start folder on the CD to your computer. Open the file and delete the following two lines of code:

```
CREATE DATABASE newland_tours;
USE newland_tours;
```

The new first line of code should begin DROP TABLE IF EXISTS.

The reason for this change is that you create the database directly in phpMyAdmin, so these two lines of code would be redundant.

Once the file is prepared, you can install the database using phpMyAdmin. To begin, log in and create a new database called newland_tours. Follow the link to open this database in phpMyAdmin, if necessary. Click the SQL tab, and near the bottom of the page, click the Choose File button to browse to the newland_tours.sql file included in the Lesson08/Start folder on the CD. Proceed to run the file and the database will be populated.

> **NOTE** Those developing with local copies of MySQL may be interested to know that phpMyAdmin can be downloaded for free, at the following URL: http://www.phpmyadmin.net/