
Most of the privileges for regular users are relatively harmless in terms of system security. The ALTER privilege can be used to work around the privilege system by renaming tables, but it is widely needed by users. Security is always a trade-off between usability and safety. You should make your own decision when it comes to ALTER, but it is often granted to users.

In addition to the privileges listed in Table 9.1, the GRANT privilege is granted with GRANT OPTION other than in the privileges list.

Table 9.2 shows the privileges suitable for use by administrative users.

# Table 9.2 Privileges for Administrators

| Privilege | Description |
| --- | --- |
| CREATE TABLESPACE | Allows an administrator to create, alter, or drop tablespaces. |
| CREATE USER | Allows an administrator to create users (as seen previously). |
| CREATE TEMPORARY TABLES | Allows an administrator to use the keyword TEMPORARY in a CREATE statement. |
| FILE | Allows data to be read into tables from files and vice versa. |
| LOCK TABLES | Allows the explicit use of a LOCK TABLES statement. |
| PROCESS | Allows an administrator to view server processes belonging to all users. |
| RELOAD | Allows an administrator to reload grant tables and flush privileges, hosts, logs, and tables. |
| REPLICATION CLIENT | Allows use of SHOW STATUS on replication masters and slaves. Replication is explained in Chapter 12. |
| REPLICATION SLAVE | Allows replication slaves to connect to the master server. Replication is explained in Chapter 12. |
| SHOW DATABASES | Allows a list of all databases to be seen with a SHOW DATABASES statement. Without this privilege, users see only databases on which they have other privileges. |
| SHUTDOWN | Allows an administrator to shut down the MySQL server. |
| SUPER | Allows an administrator to kill threads belonging to any user. |

You are able to grant these privileges to nonadmin, but you should use extreme caution if you are doing so.

The FILE privilege is a special case. It is useful for users because loading data from files can save a lot of time re-entering data each time to get it into the database. However, file loading can be used to load any file that the MySQL server can see, including databases belonging to other users and, potentially, password files. Grant this privilege with caution or offer to load the data for the user.

Two special privileges also exist, and they are shown in Table 9.3.

# Table 9.3 Special Privileges

| Privilege | Description |
| --- | --- |
| ALL | Grants all the privileges listed in Tables 9.1 and 9.2. You can also write ALL PRIVILEGES instead of ALL. |
| USAGE | Grants no privileges. This privilege creates a user and allows him or her to log on, but it doesn't allow the user to do anything. Usually, you will add more privileges later. Using GRANT to create a user with USAGE privilege is equivalent to the CREATE USER statement. |

# The REVOKE Command

The opposite of GRANT is REVOKE. You use it to take privileges away from a user. It is similar to GRANT in syntax:

```
REVOKE privileges [{columns}]
ON item
FROM user_name
```

If you have given the WITH GRANT OPTION clause, you can revoke this (along with all other privileges) by adding

```
REVOKE ALL PRIVILEGES, GRANT OPTION
FROM user_name
```

# Examples Using GRANT and REVOKE

To set up an administrator, you can type

```
mysql> grant all
-> on *,
-> to 'fred' identified by mnb123
-> with grant option;
```

This command grants privileges on all databases to a user called fred, connecting from any host, with the password mnb123 and allows him or her to pass on these privileges.

Chances are you don't want this in your system, so go ahead and revoke him or her:

```
mysql> revoke all privileges, grant option
-> from 'fred';
```

Now you can set up a regular user with no privileges:

```
mysql> grant usage
-> on books.*
-> to 'sally'@'localhost' identified by magic123;
```

# Setting Up a User for the Web

After talking to Sally, you know a bit more about what she wants to do, you can give her the appropriate privileges:

```
mysql grant select, insert, update, delete, index, alter, create, drop
-> on books.*
-> to 'sally'@'localhost';
```

Note that you don't need to specify Sally's password to give her privileges.

If you decide that Sally has been up to something in the database, you might decide to reduce her privileges:

```
mysql revoke alter, create, drop
-> on books.*
-> from 'sally'@'localhost';
```

And later, when she doesn't need to use the database any more, you can revoke privileges altogether:

```
mysql revoke all
-> on books.*
-> from 'sally'@'localhost';
```

# Setting Up a User for the Web

You need to set up a user for your PHP scripts to connect to MySQL. Again, you can apply the privilege of least principle: What should the scripts be able to do?

In most cases, they only need to run SELECT, INSERT, DELETE, and UPDATE queries. You can set up these privileges as follows:

```
mysql grant select, insert, delete, update
-> on books.*
-> to 'bookoram' identified by 'bookoram123';
```

Obviously, reason you should choose a better password than the one shown here.

If you use a web hosting service, you generally get access to user-type privileges on a database the service creates for you. It typically gives you (setting up tables and so on) for web script connections (querying the database). Using the same username and password for both is marginally less secure. You can set up a user with this level of privilege as follows:

```
mysql grant select, insert, update, delete, index, alter, create, drop
-> on books.*
-> to 'bookoram' identified by 'bookoram123';
```

Go ahead and set up this second version of the user because you will need to use it in the next section.

Note that in this case, we didn't specify a hostname. You can add this here if you like. The value you add depends on your PHP code is running. If it's the same machine you can add 'localhost', if it's a different machine then you'll want to add the correct hostname or IP.

You can log out of the MySQL monitor by typing quit. You should log back as your web user to test that everything is working correctly. If the GRANT statement you ran executed, but you are denied access

# Using the Right Database

The first step you need to take when log in is to specify which database. You can do this by typing

```
mysql> use dbname;
```

where dbname is the name of your database. Alternatively, you can avoid the use by specifying the database when you log in, as follows:

```
mysql -D dbname ...
```

When you type this command, MySQL should give you a response such as

```
Database changed
```

If you don't select a database before starting, MySQL will give you an error as

```
ERROR 1046 (3D00): No Database Selected
```

# Creating Database Tables

The next step in setting up the database is to actually create the tables. You can do this with the SQL command CREATE TABLE. The general form of a CREATE TABLE statement is

```
CREATE TABLE tableName(columns)
```

# Note

You may be aware that MySQL offers more than one table type or storage engine. We discuss the table types in Chapter 13. At present, all the tables in the database use the default storage engine, which is InnoDB as of MySQL 5.5.

You should replace the tableName placeholder with the name of the table you want to create and the columns placeholder with a comma-separated list of the columns in your table. Each column will have a name followed by a data type.

Here’s the Book-O-Rama schema:

```
Customers(CustomerID, Name, Address, City)
```

```
Orders(OrderID, CustomerID, Amount, Date)
```

```
Books(ISBN, Author, Title, Price)
```

```
Order_Items(OrderID, ISBN, Quantity)
```

```
Book_Reviews(ISBN, Review)
```

Listing 9.1 shows the SQL to create these tables, assuming you have already created the database books. You can find this SQL in the file chapter9/bookorama.sql.

You can run an existing SQL file through MySQL by typing

```
> mysql -h host -u bookoram -D books -p < bookorama.sql
```

(Remember to replace host with the name of your host and to specify the full path to the bookorama.sql file)

Using file redirection is handy for this task it means that you can edit your SQL in the text editor of your choice before executing it.

# Listing 9.1 bookorama.sql—SQL to Create Tables for Book-O-Rama

```sql
CREATE TABLE Customers
(CustomerID INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
Name CHAR(50) NOT NULL,
Address CHAR(100) not null,
City CHAR(30) not null
);

CREATE TABLE Orders
(OrderID INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
CustomerID INT UNSIGNED NOT NULL,
Amount FLOAT(6,2),
Date DATE NOT NULL
);

CREATE TABLE Books
(ISBN VARCHAR(20),
Author VARCHAR(100),
Title VARCHAR(255),
Price FLOAT(6,2));

CREATE TABLE Order_Items
(OrderID INT UNSIGNED,
ISBN VARCHAR(20),
Quantity INT);

CREATE TABLE Book_Reviews
(ISBN VARCHAR(20),
Review TEXT);
```
