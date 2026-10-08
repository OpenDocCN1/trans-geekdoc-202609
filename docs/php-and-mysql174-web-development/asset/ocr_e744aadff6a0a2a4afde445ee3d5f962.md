# Getting More Information About Databases

privilege to terminate other connections, modify system variables, and control replication. The RELOAD privilege is used to reload grant tables.

The GRANT privilege should also be granted with caution because it allows users to share their privileges with others.

Finally, and perhaps non-obviously, grant the ALTER option with caution. Users may use it to rename a table and hence circumvent the system privilege.

Make sure that you set up users, you grant them access only from the hosts that they will be connecting from. Avoid using wildcards in hosts for similar reasons.

You can increase security by using IPs rather than domain names in your host table. This way, you avoid problems with compromised DNS. You can enforce this by starting the MySQL daemon (mysqld) with the --skip-name-resolve option, which means that all column values must be either addresses or localhost.

You should also prevent non-administrative users from having access to the mysqladmin program on your web server. This program runs from the command line, access to it is an issue of operating system privilege.

# Web Issues

Connecting your MySQL database to the web raises some special security issues.

It is a good idea to start by setting up a special user for the purpose of web connections from a particular web application. This way, you can give the user the minimum privilege necessary and not grant, for example, DROP, ALTER, or CREATE privileges to that user. You might grant SELECT on catalog tables and INSERT on order tables. Again, this is an illusion of how to use the principle of least privilege.

You should always check all data coming from a user. Even if your HTML form consists of select boxes and radio buttons, someone might alter the URL to create your script. Checking the size of the incoming data is also worth

If users are typing in passwords or confidential data to be stored in your database, remember that it will be transmitted from the browser to the server in plain text unless you use Secure Sockets Layer (SSL). We discuss SSL in more detail later in this book.

# Getting More Information About Databases

So far, we used SHOW DESCRIBE to find out what tables are in the database and what columns are in them. In the following sections, we briefly look at other ways they can be used and at the use of the EXPLAIN statement to get more information about how a SELECT operation is performed.