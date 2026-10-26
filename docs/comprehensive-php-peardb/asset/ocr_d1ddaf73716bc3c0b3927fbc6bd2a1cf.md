The example uses MySQL as the database backend, but could conceivably be any PHP-supported database.

For the examples, a simple four-table database will be used to illustrate a small employee and department data set. The four tables are *Employees*, *Paychecks*, *EmployeesToDepartments*, and *Departments*. The MySQL queries to create and populate the tables are shown below in Code Listing 1.

```
```sql
#
# Table structure for table `Departments`
#

CREATE TABLE `Departments` (
  `id` int(11) NOT NULL default '0',
  `name` varchar(50) NOT NULL default '',
  PRIMARY KEY (`id`)
) TYPE=MyISAM;

#
# Dumping data for table `Departments`
#

INSERT INTO `Departments` VALUES (1, 'Web Development');
INSERT INTO `Departments` VALUES (2, 'QA');

# --------------------------------------------------------
#
# Table structure for table `Employees`
#

CREATE TABLE `Employees` (
  `id` int(11) NOT NULL default '0',
  `last_name` varchar(50) NOT NULL default '',
  `first_name` varchar(50) NOT NULL default '',
  `phone_ext` varchar(5) NOT NULL default '',
  `mgr_id` int(11) NOT NULL default '0',
  `dept_id` int(11) NOT NULL default '0',
  PRIMARY KEY (`id`),
  KEY `mgr_id` (`mgr_id`),
  KEY `dept_id` (`dept_id`)
) TYPE=InnoDB;

#
# Dumping data for table `Employees`
#

INSERT INTO `Employees` VALUES (1, 'Schwendiman', 'Blake', '204', 2, 1);
```
```