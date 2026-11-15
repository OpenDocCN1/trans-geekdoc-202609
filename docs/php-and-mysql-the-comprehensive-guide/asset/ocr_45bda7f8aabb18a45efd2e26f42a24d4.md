# Chapter 19
MySQL

PHP and MySQL: This is currently the most common combination of programming language and database on the World Wide Web. It is not only for historical reasons that most web applications still rely on the MySQL database server, which now belongs to Oracle.

MySQL is considered the default database for PHP; some even think that PHP works particularly well with MySQL (which is debatable) or that PHP only supports MySQL (which is completely wrong, as the next five chapters will show). As a result, there are numerous books on the market called _PHP and MySQL_ or something similar—including this one. And indeed, MySQL is the database that is used together with PHP in the vast majority of cases. But in this book we want to go further than many others and therefore present all relevant databases and their control via PHP.

Earlier PHP versions also supported MySQL with their own extension, _mysql_. However, one of the highlights of PHP version 5 was a completely new MySQL extension, _mysqli_. The _i_ stood for _improved_ or, as cynics like to point out, for _incompatible_ or _incomplete_—although the latter explanation is not correct. Both extensions can run in parallel, but they have different function names. The old MySQL extension offers functions with the name `mysql_*()`, while the new extension offers `mysqli_*()`. In most cases, the functions have the same names. Simply because the old MySQL extension has already been removed in PHP 7, in this chapter we will only deal with the newer, better, and faster extension for MySQL, _mysqli_.

Incidentally, MySQL has since been bought by Oracle. Some developers feared that Oracle would no longer take care of the database as the company already has its own database system (see also Chapter 22). For this reason, a fork was made from the MySQL source code. This fork is called _MariaDB_. It is therefore possible that there is still movement in the database market.

# 19.1 Preparations

First, you need to install MySQL. The source code and binary packages are available for download at www.mysql.com/downloads; at https://dev.mysql.com/downloads/mysql, for example, you will find the _community edition_ of the database server, which is