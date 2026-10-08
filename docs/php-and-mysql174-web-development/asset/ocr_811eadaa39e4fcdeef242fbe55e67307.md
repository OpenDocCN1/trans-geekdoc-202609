# Advanced MySQL
Administration

In this chapter, we cover some more advanced MySQL topics, including advanced privileges,
security, and optimization.

Key topics covered in this chapter include

+   - Understanding the privilege system in detail
- Making your MySQL database secure
- Getting more information about databases
- Speeding things up with indexes
- Optimizing your database
- Backing up and recovering
- Implementing replication

# Understanding the Privilege System in Detail

Chapter 9, “Creating Your Web Database,” described the process of setting up users and
granting them. You saw how to do this with the GRANT command. If you're going to
administer a MySQL database, understanding exactly what GRANT does and how it works is
useful.

When you issue a GRANT statement, it affects tables in the special database called mysql.
Privilege information is stored in seven tables in this database. Given this fact, granting
privileges on databases, you should be cautious about granting access to the mysql database.

You can look at what's in the mysql database by logging in as an administrator and typing
USE mysql;

If you do this, you can then view the tables in this database as usual by typing