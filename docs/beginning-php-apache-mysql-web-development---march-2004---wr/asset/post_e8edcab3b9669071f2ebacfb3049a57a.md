
# Appendix E

# Connecting to the Database

Before you can connect to the database, you need four things:

- Database name
- Host Server name
- Username
- Password

Connect to the database using the following command (in PHP):

```php
$connection = mysql_connect('servername', 'username', 'password');
```

You then need to select the appropriate database by using the following command (in PHP):

```php
<?php
$database = mysql_select_db('databasename', $connection)
or die((couldn't find the database));
?>
```

# Accessing the Database

MySQL commands are inserted within your PHP code to access the database in this way:

```php
<?php
$query = mysql_query('UPDATE field1 FROM tableName WHERE condition1')
or die("Couldn't find the table");
$result = mysql_fetch_array($query);
//your information has now been updated
?>
```

# Retrieving Data from the Database

You can access the data stored in our tables with the following statement (you can use * to retrieve fields):

```
SELECT field1, field2 FROM tableName
```

# Condition Clauses

Use the following conditions in conjunction with this statement:

```
SELECT * FROM tableName WHERE
```

# MySQL Quick Reference

Conditions (use % wildcard):

```
field = value
field > value
field < value
field >= value
field <= value
field != value
field BETWEEN value AND value2
field LIKE value
field NOT LIKE value
field IN (value1, value2, value3, etc)
field NOT IN (value1, value2, value3, etc)
```

# Selecting from Multiple Tables

You can retrieve information from two or more tables at once by using the following statements:

```
SELECT table1.field, table2.field FROM table1, table2 WHERE
table1.field = table2.field;
```

or

```
SELECT tablefield, table2field FROM table LEFT JOIN table 2;
```

# Sorting the Results

You can sort the results of the SELECT query by using the following clause at the end of the statement:

```
SELECT * FROM tableName WHERE field1=value ORDER BY field2 ASC|DESC
```

# Limiting the Results

If you would like to limit the results returned from our query, you can modify your SELECT statement like this:

```php
SELECT * FROM tableName WHERE field1=value
ORDER BY field2 ASC
LIMIT offset, number_of_rows_to_be_returned
```

# Comparison of Text Editors

There are many software programs out there that you can use to enter all your code. Some have better options than others, we've put together a chart to help you compare apples with apples. This chart lists the editors alphabetically and compares common text editor features, such as syn-tax highlighting.

Many of these editors provide similar features, so your decision really depends on your budget, needs, and how comfortable you are with each user interface.

You can read more about features not listed here, as many of these editors provide other unique benefits. We encourage you to visit the following Web sites to download these programs and get more information:

- AnyEdit: www.anyedit.org
- Dreamweaver MX 2004: www.macromedia.com
- EditPlus: www.editplus.com
- HTML-Kit: www.chami.com/html-kit/
- jEdit: www.jedit.org
- Notepad: www.microsoft.com
- PHPEd: www.nuspphere.com
- PHPEdit: www.phpedit.net
- SourceEdit: www.sourceedit.com
- TextPad: www.textpad.com
- UltraEdit-32: www.ultraedit.com
- WordPad: www.microsoft.com

# Appendix F

| Editor | Highlighted Syntax | Spell Checker | Built-in FTP Access | Block Mode | Line Editing | Word Numbers | Auto-Wrap | Completion PHP Code | WYSIWYG | Web Design Editor | Search and Replace | Price |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| AnyEdit | | | ✓ | | | | | | | | ✓ | Free |
| Dreamweaver MX 2004 | ✓ | ✓ | | | | | | | ✓ | ✓ | $399 |
| EditPlus | ✓ | | ✓ | | | | ✓ | | | | | $30 |
| HTML-Kit | ✓ | ✓ | | | | | ✓ | | | | | Free |
| Edit | ✓ | | | | ✓ | | | | | | | | Free |
| Notepad | | | | | | | | | | | | | Free |
| PHPEdit | | | ✓ | | | | | ✓ | | | ✓ | $299 |
| PHPEditor | | | | | | | | | | | | | | $79 |
| SourceEdit | ✓ | | ✓ | | | | | | | | | | $27 |
| TextPad | ✓ | ✓ | | | | | | | | | | | Free |
| UltraEdit-32 | ✓ | ✓ | | | ✓ | | | | | | | | $35 |
| WordPad | | | | | | | ✓ | | | | | | Free |

# Choosing a Third-Party Host

Keep in mind that you're unlikely to have every combination with host, so it's important that you know enough about hosts to make a well-thought decision before jumping into. At that end, let's get into a little more detail about each of those topics.

# ## Supported Languages

First of all, we will talk about the supported languages. Obviously, because you bought this book, we're assuming you are looking into PHP, but there are other languages you may need to use. There may be times when another language, such as JavaScript, is better suited for a task. For example, if you want live streaming or video on your site, you are likely to use Java because PHP needs a request from the server. There may also be times when you need to use another programming language to accomplish some of the least option of using a Perl script, rather than spending the time and money to redevelop the application in PHP.

# ## Supported Databases

Again, because this book is geared toward MySQL, you will probably need a host that supports MySQL. However, there are many other databases you can use with PHP. Here are some of the databases that PHP can work with:

- MySQL
- PostgreSQL
- MS SQL Server
- MS Access
- Sybase

Depending on your situation, you may want to choose a host that has more than one of these databases set up by default. Larger companies, for example, are MSSQL as their database, usually because they are using ASP (Active Server Pages from Microsoft) for their programming. You should need to convert any type to PHP, you will be glad to know that PHP can connect and work nicely with MSSQL as well. Also, keep in mind that you don't have to continue using the other databases; you can port the data over to MySQL using PHP to ease the troubles of manual conversion.
