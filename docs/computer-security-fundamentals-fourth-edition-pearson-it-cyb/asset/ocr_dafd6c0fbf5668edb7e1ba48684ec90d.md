SQL script injection might be the most popular type of attack on websites. In recent years, more websites have taken steps to ameliorate the dangers of these attacks, but unfortunately, many websites are still susceptible. An SQL script injection attack involves passing Structured Query Language (SQL) commands to a web application and getting the website to execute them.

Before we can discuss SQL injection further, we must talk about SQL and relational databases. Relational databases are based on relations between various tables. The structure includes tables, primary and foreign keys, and relations:

+   - Each row represents a single entity.
+   - Each column represents a single attribute.
+   - Each record is identified by a unique number called a *primary key*.
+   - Tables are related by foreign keys. A *foreign key* is a primary key in another table.

You can see an example of these relations in [Figure 6.7](#).

![](bbox=[0.144, 0.318, 0.649, 0.5])

**Figure 6.7** Database relations.

All relational databases use SQL, which includes commands such as `SELECT`, `UPDATE`, `DELETE`, `INSERT`, and `WHERE`. At least the basic queries are very easy to understand and interpret.

Most basic SQL injection works like this: Many websites/applications have a page where a user enters a username and password. That username and password will have to be checked against some database to see if they are valid. Regardless of the type of database (Oracle, SQL Server, MySQL), all databases speak SQL. SQL looks and functions a great deal like English. For example, to check a username and password, you might want to query the database to see if there is any entry in the users table that matches the username and password that was entered. If there is such an entry, you have a match. The SQL statement to ask this might look something like this:

[Click here to view code image](#)

```
```sql
'SELECT * FROM tblUsers WHERE USERNAME = 'jdoe' AND PASSWORD = 'letmein
```
```

The problem with this query is that, although it is valid SQL, it hard codes the username and password. For a real website, you would have to take whatever the user entered into the username field and password field and check that. This can be easily done (regardless of what programming or scripting language the website is programmed in). It would look something like this:

[Click here to view code image](#)

```
```sql
'SELECT * FROM tblUsers WHERE USERNAME = "' + txtUsername.Text + '" AND PASSWORD =
'txtPassword.Text + ""'
```
```

If you enter username 'jdoe' and password 'letmein', this code produces the following SQL command:

[Click here to view code image](#)