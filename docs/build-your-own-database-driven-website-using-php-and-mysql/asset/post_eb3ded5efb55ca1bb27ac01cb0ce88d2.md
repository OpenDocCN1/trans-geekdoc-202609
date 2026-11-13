
even number, while values of 0 or greater than 14 are changed to 14.

## D PHP Functions for Working with MySQL

PHP provides a vast library of built-in functions that let you perform all sorts of tasks without having to look to third party software vendors for a solution. The online reference to these functions provided by the PHP Official Website (http://www.php.net) is second to none. Obtaining detailed information about a function is as simple as opening your browser and typing: http://www.php.net/function_name

Due to the convenience of this facility, we have judged that a complete PHP function reference is beyond the scope of this book. All the same, this appendix contains a reference to those PHP functions specifically designed to interact with MySQL databases, so that if you use this book as your primary reference while building a database-driven Website, you won't have to look elsewhere for the information you need.

This list of functions and their definitions are current as of PHP 4.0.5.

### mysql_affected_rows

```
mysql_affected_rows([link_id])
```

Returns the number of affected rows in the previous MySQL INSERT, UPDATE, DELETE, or REPLACE operation performed with the specified link_id. If the link is not specified, then the last-opened link is assumed. Returns -1 if the previous operation failed.

### mysql_close

```
mysql_close ([link_id])
```

Close current or specified (link_id) MySQL connection. If the link is a persistent link opened by mysql_pconnect() (see page 229), this function call is ignored. Since non-persistent connections are closed automatically by PHP at the end of a script, this function is usually not needed.

Returns true on success, false on failure.

### mysql_connect

```
mysql_connect([hostname [:port] [:/path/to/socket] [,username [,password]]])
```

Opens a connection to a MySQL server and returns a connection ID (which evaluates to true) that may be used in other MySQL-related functions. The following default values are assumed if they are not specified:

- hostname:port = "localhost:3306"
- username = server process name
- password = ""

If the connection attempt is unsuccessful, an error message will be displayed by default and the function will return false. To bypass display of the error message (e.g. to display your own by checking the return value), put '@' at the start of the function name (i.e. @mysql_connect(...)).

### mysql_create_db

```
mysql_create_db(db_name [,link_id])
```

Creates a new MySQL database with the specified name, using the default or specified (link_id) MySQL connection. Returns true on success, or false on error. mysql_createdb() may also be used, but is deprecated.

### mysql_data_seek

```
mysql_data_seek(result_id, row_number)
```

Moves the internal result pointer of the result set identified by result_id to row number row_number, so that the next call to a mysql_fetch_* function will retrieve the specified row. Returns true on success, and false on failure. The first row in a result set is number 0.

### mysql_db_name

mysql_db_name(result_id, row_number)

result_id should refer to a result set produced by a call to mysql_list_dbs(), and will retrieve the name of the database listed on the row specified by row_number. The first row in a result set is row 0. mysql_dbname() may also be used, but is deprecated.

### mysql_db_query

mysql_db_query(db_name, sql_query [, link_id])

Selects the MySQL database identified by db_name as if with mysql_select_db(), and then executes the specified MySQL query (sql_query). If the MySQL connection identifier (link_id) is not specified, PHP will use the currently active connection. If no such connection exists, PHP will attempt to open a connection by implicitly calling mysql_connect() with default parameters.

If the query fails, an error message to that effect will be displayed unless '@' is added to the beginning of the function name, and the function will return false instead of a result identifier (which evaluates to true). If the error occurred due to an error in the SQL query, the error number and message can be obtained using mysql_errno() and mysql_error() respectively.

mysql() may also be used, but is deprecated.

### mysql_drop_db

mysql_drop_db(db_name [, link_id])

Drops (deletes) the specified database and all the tables it contains, using the default or specified (link_id) MySQL connection. Returns true on success or false on failure. mysql_dropdb() may also be used, but is deprecated.

### mysql_errno

mysql_errno([link_id])

Returns the numerical value of the error message from the last MySQL operation on the default or specified (link_id) MySQL connection.

### mysql_error

```
mysql_error([link_id])
```

Returns the text of the error message from the last MySQL operation on the default or specified (link_id) MySQL connection.

### mysql_escape_string

```
mysql_escape_string(string)
```

Returns an escaped version of a string (with backslashes before special characters such as quotes) for use in a MySQL query.

### mysql_fetch_array

```
mysql_fetch_array(result_id [, array_type])
```

Fetches the next row of a MySQL result set, and then advances the internal row pointer of the result set to the next row. Returns the row as an associative array, a numeric array, or both, depending on the value of array_type.

When array_type is not specified, or set to MYSQL_BOTH, each field in the row will be given a numerical index ($row[0]) as well as a string index ($row['col_name']) in the returned array. MYSQL_NUM causes only numerical indices to be assigned, while MYSQL_ASSOC assigns only string indices.

Returns false if there are no rows left in the specified result set.

### mysql_fetch_assoc

```
mysql_fetch_assoc(result_id)
```

Fetch a result row as an associative array. Identical to mysql_fetch_array() called with the MYSQL_ASSOC parameter.

### mysql_fetch_field

```
mysql_fetch_field(result_id [,field_position])
```

Returns an object that contains information about a particular column in the supplied result set (result_id). If the field_position (the first column is position 0) is not specified, then repeated calls to mysql_fetch_field() will retrieve each of the columns one at a time, from left to right. Assuming the result of this function is stored in $field, then the properties of the retrieved field are accessible as shown in Table 4.

### Table 4 - Object fields for mysql_fetch_field

| Object property | Information contained |
|---|---|
| $field->name | Column name |
| $field->table | Name of table the column belongs to |
| $field->max_length | Maximum length of the column |
| $field->not_null | 1 if the column is set NOT NULL |
| $field->primary_key | 1 if the column is set PRIMARY KEY |
| $field->unique_key | 1 if the column is set UNIQUE |
| $field->multiple_key | 1 if the column is a non-unique key |
| $field->numeric | 1 if the column is numeric |
| $field->blob | 1 if the column is a BLOB |
| $field->type | The data type of the column |
| $field->unsigned | 1 if the column is UNSIGNED |
| $field->zerofill | 1 if the column is set ZEROFILL |

### mysql_fetch_lengths

```
mysql_fetch_lengths(result_id)
```

Returns an array containing the lengths of each of the fields in the last-fetched row of the specified result set.

### mysql_fetch_object

```
mysql_fetch_object(result_id [,result_type])
```

Returns the next result row from result_id in the form of an object, and advances the internal row pointer of the result set to the next row. result_type may be set to MYSQL_NUM, MYSQL_ASSOC, or MYSQL_BOTH (the default) to retrieve the fields as numerical properties ($row->0 for the first field in the row), named properties ($row->user for the value of the user field in the result set), or both, respectively.

### mysql_fetch_row

```
mysql_fetch_row(result_id)
```

Fetch a result row as numerical array. Identical to mysql_fetch_array() called with the MYSQL_NUM parameter.

### mysql_field_flags

```
mysql_field_flags(result_id, field_position)
```

Returns a string containing the flags associated with the specified field (field_position) in the specified result set (result_id). The flags are separated by spaces in the returned string. Possible flags are: not_null, primary_key, unique_key, multiple_key, blob, unsigned, zerofill, binary, enum, auto_increment, and timestamp. mysql_fieldflags() may also be used, but is deprecated.

### mysql_field_name

```
mysql_field_name(result_id, field_position)
```

Returns the name of the specified field (field_position) in a result set (result_id). mysql_fieldname() may also be used, but is deprecated.
