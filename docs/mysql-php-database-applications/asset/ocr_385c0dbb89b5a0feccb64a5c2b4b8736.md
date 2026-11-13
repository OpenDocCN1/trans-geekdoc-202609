# make_page_title()

This function cleans up a string to make it suitable for use as the value of an HTML <TITLE> tag, removing any HTML tags and replacing all HTML entities with their literal-character equivalents by using get_html_translation_table (HTML_ENTITIES).

```
string make_page_title ([string title])
```

# money()

This function formats the sole argument as a standard U.S. dollar value, rounding any decimal value to two decimal places for cents and prepending a dollar sign to the returned string. Commas serve as thousands separators. However, remember that you can run into rounding errors with numbers of type float. This is only an issue in complex applications, though.

```
string money ([mixed value])
```

# states()

This function returns an associative array, the key being the two-letter abbreviation of the states, the value being the state name.

```
array states(void)
```

# From functions/database/

These are common functions that help you work with MySQL databases.

# db_connect()

This function creates a database connection using the PEAR DB class. It accepts a variable list of parameters. The most common one used in the examples in this book is application, which is used as an index into values retrieved from an .ini file (typically stored outside the document root of the Web server).

```
void db_connect ()
```

# db_fetch_record()

This function selects values from the MySQL table specified by the first argument. If the optional second and third arguments are not empty, the select gets the row from that table in which the column named in the second argument has the value given by the third argument. The second and third arguments can also be arrays, in which case the query builds its where clause using the values of the second array of arguments as the table-column names and the corresponding values of the third array of arguments as the required values for those table columns.

```
db_fetch_record(string table [,string key [,string value]])
```