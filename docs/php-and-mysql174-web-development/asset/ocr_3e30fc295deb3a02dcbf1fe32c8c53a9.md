# 604 Appendix A Installing Apache, PHP, and MySQL

![](bbox=[0.118, 0.103, 0.731, 0.431])

Figure A.2  Prompted for a MySQL root password

After setting the password, you will be asked to confirm it, and the installation process will continue.

When you install MySQL, it automatically creates three databases. One is the mysql table, which controls users, hosts, and DB permissions in the actual server. The others are information_schema and performance_schema, which store additional metadata about the MySQL server. You can check your database via the command line like this:

```
# mysql -u root -p
Enter password:
mysql> show databases;
```

| Database |
| information_schema |
| mysql |
| performance_schema |

3 rows in set (0.00 sec)

Type quit or \q to quit the MySQL client.

The default MySQL configuration allows any user access to the system without providing a username or password. This is obviously undesirable, which is why the installation process takes you through the step of setting a password for the root user