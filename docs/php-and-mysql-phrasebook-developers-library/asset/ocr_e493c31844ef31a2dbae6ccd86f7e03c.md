PostgreSQL has a growing fan base. Some even say this is because with version 8.0 finally came a native Windows version. However, most production systems that use PostgreSQL are hosted on Linux or UNIX, nevertheless.

After you install the database, you can use Web-based administration software such as phpPgAdmin (http://sourceforge.net/projects/phpgadmin) or other tools such as the graphical user interface (GUI) application pgAdmin (www.pgadmin.org/) to administer the database. Alternatively, you can use the command-line tool. To allow PHP to access the PostgreSQL installation, Windows users must load the extension with the entry extension (php_pgsql.dll) in php.ini; UNIX/Linux users configure PHP with the switch --with-pgsql=/path/to/pgsql.

Then, pg_connect() connects to the data source. You have to provide a connection string that contains all important data, including host, port, name of the database, and user credentials.

# Sending SQL to PostgreSQL

# pg_query()

```
<?php
if ($db = @pg_connect('host=localhost port=5432
dbname=phrasebook user=postgres password=abc123'))
{
    pg_query($db, sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        pg_escape_string($_POST['quote']),
        pg_escape_string($_POST['author']),
        intval($_POST['year'])));
}
```