If your MySQL installation is on Linux/UNIX or Mac OS X, your primary concern should be the owner of the MySQL daemon—it should not be root. Running the daemon as a non-root user such as mysql or data - base limits the ability of malicious individuals to gain access to the server and overwrite files.

> NOTE: You can verify the owner of the process using the ps (process status) command on your Linux/UNIX or Mac OS X system.

If you see that MySQL is running as root on your system, immediately contact your Internet service provider and complain. If you are the server administrator, you should start the MySQL process as a non-root user or specify the preferred username in the startup command line:

```
mysqld --user=non_root_user_name
```

For example, if you want to run MySQL as user mysql, use this command:

```
mysqld --user=mysql
```

However, the recommended method for starting MySQL is through the mysqld_safe startup script in the bin directory of your MySQL installation:

```
# bin/mysqld_safe --user=mysql &
```

# Securing Your MySQL Connection

You can connect to the MySQL monitor or other MySQL applications in several different ways, each of which has its own security risks. If your MySQL installation is on your own workstation, you have less to worry about than users who have to use a network connection to reach their server.

If MySQL is installed on your workstation, your biggest security concern is leaving your workstation unattended with your MySQL monitor or MySQL GUI administration tool up and running. In this type of situation, anyone can walk over and delete data, insert bogus data, or shut down the server. Use a screensaver or lock screen mechanism with a password if you must leave your workstation unattended in a public area.

If MySQL is installed on a server outside your network, the security of the connection should be of some concern. As with any transmission of data over the Internet, data can be intercepted. If the transmission is unencrypted, the person who intercepted the data can piece it together and use the information. Suppose that the unencrypted transmission is your MySQL login information—a rogue individual now has access to your database, masquerading as you.