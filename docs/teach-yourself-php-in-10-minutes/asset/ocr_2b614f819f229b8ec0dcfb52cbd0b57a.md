You are expecting $_POST["value"] to contain an integer value to update the value of column coll. However, a malicious user could enter a semicolon in the form input field, followed by any SQL statement he or she wants to execute.

For instance, suppose the following is the value of $_POST["value"] :

```
0; INSERT INTO admin_users (username, password)
VALUES ('me', 'mypassword');
```

The SQL executed would then look like the following (the statements are shown here on separate lines for clarity):

```
UPDATE mytable SET coll = 0;
INSERT INTO admin_users (username, password)
VALUES ('me', 'mypassword');
WHERE col2 = 'somevalue';
```

This is clearly a bad situation! The first statement updates the value of coll for all rows in mytable . This will be an inconvenience, but the second statement creates a more serious problemthe user has been able to execute an INSERT statement that creates a new administrator login. The third statement is rubbish, but by the time the SQL parser reaches that statement and throws an error, the damage has been done. This type of attack is known as SQL injection .

Of course, for SQL injection to be a serious threat, the user must understand a little about your database structure. In this example, the attacker is aware that you have a table called admin_users , that it contains fields named username and password , and that the password is stored unencrypted.

A visitor to your website would not generally know such information about a database you built yourself. However, if your website includes open-source componentsperhaps you have used a freeware discussion board programthe table definitions for at least some of your database are accessible to users.

Furthermore, if your script produces output whenever a query fails, this could reveal important details about your database structure. On a production website, you should consider setting display_errors to off and using log_errors to write warnings and error messages to a file instead.