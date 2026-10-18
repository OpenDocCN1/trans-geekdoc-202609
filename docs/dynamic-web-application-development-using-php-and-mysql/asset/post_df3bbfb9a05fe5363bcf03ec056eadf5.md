
**FIGURE 14.18 Customers table screen**

![](img/b2471264f405d17994ef173e4b9cec92_435_0.png)

‘Create new table’ form, as shown in Figure 14.15. If you click on the name of the database table ‘Customers’ then you will be taken to the table edit screen as shown in Figure 14.18.

Now that you know how to create a table, move to the ‘Create new table’ form and create the Products table. Remember that there are five field types and they are:

| Field | Type |
|---|---|
| Id | int |
| Name | varchar (255) |
| Description | text |
| Quantity | int |
| Cost | float |

Also, remember that the Products Id, like the Customers Id, will need to have ‘auto_increment’ selected in the Extra column and the ‘Primary’ radio button also selected. The completed form is shown in Figure 14.19.

When the Save button is clicked, you should be taken to a screen indicating that the Products table has been correctly created, as shown in Figure 14.20.

You should also note that on the left of the screen a second table (`products`) has now been inserted below the previous `customers` one. Furthermore, the number 2 should now be next to the database name on the drop-down menu indicating that the database has two tables.

**FIGURE 14.19 Completed field information for the Products table**

![](img/b2471264f405d17994ef173e4b9cec92_436_0.png)

**FIGURE 14.20 Products table screen**

![](img/b2471264f405d17994ef173e4b9cec92_436_1.png)

We are making progress. The next step is to populate these tables with the data shown in Figure 14.2 and Figure 14.3.

## Adding data

To add data records to a table in phpMyAdmin, you first click on the table to which you wish to add records in the list on the left of the web page below the database name. If you click on customers, you should see a screen like that shown in Figure 14.18. To begin adding records, click the Insert tab near the middle top of the screen and you should see a screen similar to that in Figure 14.21.

The records we wish to insert into this table are shown in Figure 14.2. Our first record is:

Mrs Smith Lynne

You should type this data into the corresponding Value fields on the right of the top form. You can ignore the bottom form fields.

> **NOTE** Do NOT enter a value for ID. When we created the table, we selected the auto-increment setting which means that this value will be created automatically for us.

**FIGURE 14.21 Insert customer records screen**

![](img/b2471264f405d17994ef173e4b9cec92_437_0.png)

**FIGURE 14.22 Completed customer records screen**

![](img/b2471264f405d17994ef173e4b9cec92_438_0.png)

Because we have a number of records to insert, click the ‘Insert another new row’ button at the bottom of the screen. Your screen should look like that shown in Figure 14.22 just before you click the Go button.

After clicking the Go button, you should be taken to a screen which informs you that the row has been correctly inserted and presents you with a new form to insert the next row record. Insert all the records shown in Figure 14.2 into the table.

When you have finished, click the products table link on the left of the screen under the database name. Then select the Insert tab and insert all of the record rows for the Products table as shown in Figure 14.3.

> **NOTE** Remember not to insert the ID values for the records as these will be inserted automatically.

## Viewing records

We can view the records we have entered to ensure that they are correct by clicking the icon to the left of the table names, as shown in Figure 14.23.

**FIGURE 14.25 Editing a record screen**

![](img/b2471264f405d17994ef173e4b9cec92_440_0.png)

This customer has now decided that she wishes to be known by her full name, ‘Elizabeth’, and so we need to correct the record. After clicking the pencil icon, we are taken to a screen like that shown in Figure 14.25.

In the values column of the form, delete the name ‘Liz’ and replace it with ‘Elizabeth’. Clicking the Go button will return you to the previous screen.

> **NOTE** Check that all of the other records are correct in both the Customers and the Products tables and make any changes required before progressing to the next stage.

## Backing up a database

While our MySQL database will remain perfectly okay for the moment, it is a good idea to make a copy of the database for security reasons. This will allow us to restore our database if anything goes wrong and also it will allow us to install the database on another MySQL database management system on another computer without the need to enter in all the data tables and records which we have done so far.

To make a database backup we first need to click on the database name on the left of the screen. The screen should now display the information shown in Figure 14.26.

**FIGURE 14.26 Database information screen**

![](img/b2471264f405d17994ef173e4b9cec92_441_0.png)

**FIGURE 14.27 Export database screen**

![](img/b2471264f405d17994ef173e4b9cec92_441_1.png)

**FIGURE 14.28 Save database to file**

![](img/b2471264f405d17994ef173e4b9cec92_442_0.png)

Next, we need to select the Export tab near the middle top of the screen. The screen should now look like Figure 14.27.

To back up your database to a file simply click the ‘Save as file’ checkbox and then click the Go button. A pop up dialogue box as shown in Figure 14.28 will appear allowing you to save the database to a local file.

Click the button and a file with the same name as your database and the extension .sql will be produced.

| NOTE | This is an SQL dump file of your database. It is not really a backup of the database but a file from which the database can be recreated on any MySQL system. |
|------|------|

If you open the database .sql file in a text editor, you will see that its contents look like this:

```
-- phpMyAdmin SQL Dump
-- version 2.6.1-p13
-- http://www.phpmyadmin.net
--
-- Host: localhost
-- Generation Time: Nov 12, 2005 at 03:05 PM
-- Server version: 4.1.10
-- PHP Version: 5.0.4
--
-- Database: `glassesrus`
--
-- --------------------------------------------------------
--
-- Table structure for table `customers`
--
CREATE TABLE `customers` (
  `Id` int(11) NOT NULL auto_increment,
  `Title` varchar(10) NOT NULL default '',
  `Surname` varchar(100) NOT NULL default '',
  `Firstname` varchar(100) NOT NULL default '',
  PRIMARY KEY (`Id`)
) ENGINE = InnoDB DEFAULT CHARSET = latin1 AUTO_INCREMENT = 13 ;
--
-- Dumping data for table `customers`
--
INSERT INTO `customers` VALUES (1, 'Mrs', 'Smith', 'Lynne');
INSERT INTO `customers` VALUES (2, 'Miss', 'Jones', 'Ann');
INSERT INTO `customers` VALUES (3, 'Mr', 'Brown', 'Simon');
INSERT INTO `customers` VALUES (4, 'Mr', 'Smith', 'David');
INSERT INTO `customers` VALUES (5, 'Mr', 'Bell', 'Peter');
INSERT INTO `customers` VALUES (6, 'Ms', 'Hall', 'Elizabeth');
INSERT INTO `customers` VALUES (7, 'Mr', 'Smith', 'Kevin');
INSERT INTO `customers` VALUES (8, 'Mr', 'Jones', 'Jack');
INSERT INTO `customers` VALUES (9, 'Mr', 'Green', 'William');
INSERT INTO `customers` VALUES (10, 'Mrs', 'Smith', 'Lynne');
INSERT INTO `customers` VALUES (11, 'Mr', 'Bell', 'Simon');
INSERT INTO `customers` VALUES (12, 'Mr', 'Brown', 'Ian');
-- --------------------------------------------------------
--
-- Table structure for table `products`
--
CREATE TABLE `products` (
  `Id` int(11) NOT NULL auto_increment,
  `Name` varchar(255) NOT NULL default '',
  `Description` text NOT NULL,
  `Quantity` int(11) NOT NULL default '0',
  `Cost` float NOT NULL default '0',
```

**FIGURE 14.29 Deleting database tables**

![](img/b2471264f405d17994ef173e4b9cec92_445_0.png)

**FIGURE 14.30 Deleting tables confirmation screen**

![](img/b2471264f405d17994ef173e4b9cec92_445_1.png)

## 14.5 Extending our database

### Our design

It's time now to consider our database design. Currently we have two tables: Customers and Products. We can illustrate them graphically using a database design notation as shown in Figure 14.33.

I have used a tool called MySQL Workbench to draw my database design. The tool is available from http://dev.mysql.com/downloads/gui-tools/5.0.html. It is currently only in an Alpha release which means that it is not designed for commercial projects. However, the tool does provide a good insight into the next generation of database design tools.

How to use the MySQL Workbench is outside the scope of this tutorial but what we can clearly see is that we have two database tables which are independent of each other at the moment. We are using the tool only to illustrate the new tables we are going to create and the relationships between them. We shall show how to create the tables in phpMyAdmin shortly.

Currently, this database design isn't of much use to us so we need to improve its design. What we are going to do is to create a new table called Purchases. This table is going to hold the details of the purchases made by each customer. Its data fields and types are going

**FIGURE 14.33 Current database design in MySQL Workbench**

![](img/b2471264f405d17994ef173e4b9cec92_447_0.png)
