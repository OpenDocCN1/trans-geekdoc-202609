If, for instance, you want to create a user called john with a password of 99hjcl5, with SELECT and INSERT privileges on all tables in the database called myDb, and you want this user to be able to connect from any host, use this command:

```
GRANT SELECT, INSERT
ON myDB.*
TO john@"%"
IDENTIFIED BY "99hjcl5";
```

Note the use of two wildcards: * and %. These wildcards replace values. In this example, * replaces the entire list of tables and % replaces a list of all hosts in the known world—a very long list indeed.

Here's another example of adding a user with the GRANT command, this time to add a user called jane with a password of 45sdg11, with ALL privileges on a table called employees in the database called myCompany. This new user can connect only from a specific host:

```
GRANT ALL
ON myCompany.employees
TO jane@janescomputer.company.com
IDENTIFIED BY "45sdg11";
```

If you know that janescomputer.company.com has an IP address of 63.124.45.2, you can substitute that address in the hostname portion of the command, as follows:

```
GRANT ALL
ON myCompany.employees
TO jane@"63.124.45.2"
IDENTIFIED BY "45sdg11";
```

One note about adding users: Always use a password and make sure that the password is a good one!

If you use the GRANT command to add users, the changes take immediate effect. To make absolutely sure of this, you can issue the FLUSH PRIVILEGES command in the MySQL monitor to reload the privilege tables.

# # Removing Privileges

Removing privileges is as simple as adding them; instead of the GRANT command, you use REVOKE. The REVOKE command syntax is as follows:

```
REVOKE privileges
ON databasename.tablename
FROM username@hostname;
```