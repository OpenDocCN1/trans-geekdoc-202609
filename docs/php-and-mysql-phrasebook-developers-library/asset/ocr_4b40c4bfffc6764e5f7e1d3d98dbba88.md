This section again uses the quotes table, which also includes an identity column; however, this is a bit more complicated to implement with Oracle. Refer to the script quotes.oracle.sql in the download archive for more information.

To send SQL to Oracle, two steps are required. First, a call to oci_parse() parses a SQL string and returns a resource that can then be executed using oci_execute(). The second parameter of oci_execute() is quite important. Several constants are allowed, but most of the time, OCI_DEFAULT is used. Despite the name, that's not the time, OCI_DEFAULT value, but means "no auto-commit." In contrast, OCI_COMMIT_ON_SUCCESS commits the pending transaction when no error has occurred. And this is, indeed, the default value.

Unfortunately, there is no such thing as oci_escape_string() to escape special characters for use in a SQL statement. Therefore, prepared statements are a must—but are also very easy to implement. For this, the SQL statement must contain placeholders that start with a colon:

```
$sql = 'INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)';
```

Then, these placeholders have to be filled with values. For this, oci_bind_by_name() must be used:

```
oci_bind_by_name($stmt, ':quote', $_POST['quote']);
```

The preceding code sends some form data to the database. No need to worry about special characters because oci_bind_by_name() takes care of that.