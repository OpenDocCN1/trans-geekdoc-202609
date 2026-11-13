```
# Table structure for table 'addresses'
#
create database store;
use store;
CREATE TABLE addresses (
 address_id int(11) NOT NULL auto_increment,
 user_id int(11) default NULL,
 place varchar(25) NOT NULL default '',
 addr_1 varchar(255) NOT NULL default '',
 addr_2 varchar(255) default NULL,
 city varchar(50) NOT NULL default '',
 state char(2) NOT NULL default '',
 ZIP varchar(5) NOT NULL default '',
 country varchar(5) default NULL,
 PRIMARY KEY  (address_id)
) TYPE=MyISAM;
```

```
#
# Dumping data for table 'addresses'
#
INSERT INTO addresses VALUES (5,3,'home','1845 Fair Oaks','Apt
6','San Francisco','CA','92147','USA');
INSERT INTO addresses VALUES (6,4,'home','30445 Haines St','Apt
8G','San Francisco','CA','92149','USA');
INSERT INTO addresses VALUES (7,5,'home','8 Oak
Rd',NULL,'Atlanta','GA','14119','USA');
```

It's a piece of cake to run all of these commands in a batch by directing this file into the command-line client.

```
shell> mysql -u root -pmy pass < store.sql
```

The SQL statements in this file were created with the mysqldump utility. As you can see from the .sql file, this utility exports both table-structure information (create table statements) and table data (insert statements). By dumping the entirety of databases and tables into files you will create a backup of your data and make your data transportable.

The mysqldump utility is very flexible and can take a variety of flags that will return the exact MySQL data you need in a variety of formats. You can see the full set of mysqldump options by going to your mysql/bin directory and running mysqldump --help. In this appendix we address only some of mysqldump's more commonly used options.