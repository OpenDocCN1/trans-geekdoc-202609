
Improving performance involves using IP addresses because it eliminates the need to perform an internal DNS lookup. This can be user configured with the --skip-name-resolve my.cnf or mysqld startup option because it tells MySQL to not perform DNS lookups.

> Using a host of '%' is not recommended because it provides global access from any accessible server that can see the MySQL server. For a publicly accessible server, this provides opportunity for a brute force password attack on your server.

You can optionally create a user. It is possible to grant permissions to a user that does not exist and this results in the user being created by default.

When you refer to a user for subsequent commands, a user represents a given username, password and host.

## GRANT

You use the GRANT command to give permissions to a specific user. The grant command is broken down into four components:

- privilege(s)
- database objects
- user
- WITH GRANT OPTION

Some example GRANT commands include:

```
GRANT SELECT, INSERT, UPDATE, DELETE ON db.* TO appuser@192.168.100.%;
GRANT SELECT ON db.* TO appreadonly@192.168.100.%;
GRANT CREATE, CREATE VIEW, DROP ON db.* TO appdba@localhost;
```

The SHOW GRANTS command can be run to provide a GRANT compatible syntax for permissions for specified users. You can also query the mysql.user table for specific details.

## REVOKE

The REVOKE command, as the name indicates, removes privileges given by the GRANT command. For example:

```
REVOKE DELETE ON db.* FROM appuser@192.168.100.%;
```

As you can see, it is possible to provide a subset of granted permissions.

## DROP USER

You can remove a user and all permissions with the DROP USER command.

> It is possible to manipulate the MySQL security model manually via normal DDL commands against the mysql meta data schema. While this is possible, it is strongly recommended you refrain from this historical process and use the GRANT and REVOKE commands.

Now that you understand how to manage permissions, the rest of this section discusses the MySQL security recommendations.

## The Security Backdoor

You need to restrict shutdown and restart permissions on the mysql server because the mysql server can be started with the --skip-grants option. This option not only bypasses all security, it lets you change existing security. There is no way to remove this functionality from the mysql server.

## Change Default ‘root’ User

MySQL provides a feature over other commercial database products because you can replace the default supplied super user ‘root’ with any user you define. The advantage here is to reduce any brute force password attempts on a publicly accessible MySQL server. You have two ways to achieve this, the correct GRANT way, and the hack mysql security way.

For example, if you want to replace the ‘root’ user with a ‘dba’ user, you would use the following SQL statements:

```
$ mysql -uroot -p
CREATE USER dba@localhost IDENTIFIED BY 'somepass';
GRANT ALL on *.* TO dba@localhost WITH GRANT OPTION;
```

```
$ mysql -udba -p
SHOW GRANTS;
```

| Grants for dba@localhost |
|---|
| GRANT ALL PRIVILEGES ON *.* TO 'dba'@'localhost' IDENTIFIED BY PASSWORD '*13883BDDBE566ECECC0501CDE9B293303116521A' WITH GRANT OPTION |

```
DROP USER root@localhost;
SELECT host, user,password
FROM mysql.user
WHERE super_priv='Y' OR grant_priv='Y';
```

| host | user | password |
|---|---|---|
| localhost | dba | *13883BDDBE566ECECC0501CDE9B293303116521A |

The incorrect way is as follows.

```
$ mysql -uroot -p
mysql> (before "UPDATE") UPDATE mysql.user SET user='dba' WHERE user='root';
mysql> (before "FLUSH") FLUSH PRIVILEGES;
```

## Using Privileges Appropriately

The lazy approach is to grant the ALL privilege for a single application user. Permissions should always be restricted to the purpose of the user only. There should also be multiple users for the different roles, further allowing for greater security. By default, application users would fall into at least two categories:

- Those operations that require permissions to read and write application data
- Those operations that require read only permissions to application data

You should only grant the SELECT, INSERT, UPDATE, DELETE privileges when needed. Only add additional privileges when needed, for example EXECUTE for stored routines, or CREATE VIEW for dba's.

## Defining User Host Permissions

The lazy approach is to grant user permissions to a '%' host. Ideally hosts should be restricted to specific IP address or submask, e.g. 192.168.100.1 or 192.168.100.%. You may use DNS names or IP addresses; however, MySQL can elect to ignore DNS entries based on configuration options.

A DBA account with SUPER privileges should be restricted to a host string of 'localhost' especially when WITH GRANT OPTION is also specified. This requires a DBA to physically connect to the database server first and provides a separate level of security that you can manage better via OS specific user security such as LDAP, yellow pages or RSA tokens, for example.

> Be careful when you add multiple permissions to varying host strings when using wildcards. There is an order of precedence and adding more restrictive global permissions may override other permissions. Refer to the MySQL Reference Manual for specific details at http://dev.mysql.com/doc/refman/5.1/en/privilege-system.html.

## Ideal Application Security

What is an ideal permission model for your application? Ideally you should have the following:

- A dba user for database administration operations only. This includes operations such as creating users, schemas and permissions for daemon administration. This user is restricted to the host of 'localhost'.
- An app_dba user for a different level of DBA administration that only has permission on the respective application schemas to create and drop objects. Ideally this is restricted to the host of 'localhost'.
- An app_rw user that has `INSERT`, `UPDATE`, `DELETE`, `SELECT` privileges to the respective application schemas.
- An app_readonly user that has `SELECT` privileges to the respective application schemas.

> You need to realize that MySQL security is checked for every executed SQL statement. Having a complex privilege model increases the overhead of validation for every SQL statement. While security is important, you should use a moderated approach as detailed in this chapter.

## Additional Database Security

In addition to MySQL user security there are other practical approaches to hardening your MySQL environment and the data recorded.

- When the application server accessing the database resides on the same server as your database, disable access externally with the `--skip-networking` option.
- MySQL by default will bind to all IP addresses of the server and accept connections on the specified port, the default of 3306. You can restrict MySQL to a specified IP address with the `--bind-address` option. This can also enable you to run multiple versions of MySQL on the same default port of 3306 on the same server with the use of multiple IP addresses.
- You can configure MySQL to operate with SSL keys; however, this only provides encryption of the communication between the client and the server.
- The use of `sql_mode=NO_AUTO_CREATE_USER` to ensure that users must always have passwords.
- The use of Referential Integrity, e.g. Foreign Keys.
- The use of check constraints such as `NOT NULL`, `UNSIGNED` and `ENUM`.
- Don't store passwords in clear text in the database.

## Auditing

MySQL provides no means of system auditing. This is a significant shortcoming in important security environments such as financial and banking.

Your only option is to enable binary logging. This provides the only audit trail option of SQL commands possible with a standard mysql installation that logs all DML and DDL by default. It is possible to configure the binary log to ignore operations on a per schema and table basis which negates its complete view of all operations.
