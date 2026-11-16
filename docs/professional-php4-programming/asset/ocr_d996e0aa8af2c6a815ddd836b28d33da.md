This function opens a persistent connection. The main difference between this and odbc_connect() is that connections opened with the same connection parameters will use an existing connection instead of opening a new one. This can aid in performance as it doesn't require the overhead of reopening the connection. Another behavior difference from odbc_connect() is that the connection will not automatically be closed when the script exits. Also, odbc_pconnect() does not work when PHP is installed as a CGI module, instead it acts like odbc_connect().

# Dealing with Meta Data

Meta data is, simply, data about data. In the context of PHP database programming, we use meta data to get information about the state of the database, how tables and rows have been constructed, and any error conditions that may exist. This information can be exceptionally useful: it not only helps you debug your applications, but it allows you to write applications where you are manipulating the state of the database on the fly.

# odbc_error() and odbc_errormsg()

```
string odbc_error([int connection_id])
string odbc_errormsg([int connection_id])
```

odbc_error() is defined in the manual as returning the ODBC error code, a sometimes obscure reference to the error condition. In practice, both odbc_error() and odbc_errormsg() often return the same information, including the ODBC error state and the error message. The connection_id parameter is optional, and if omitted the function returns the last error state of any connection. An empty string will be returned if there is no active error condition.

# odbc_field_name()

```
string odbc_field_name(int result_id, int field_number)
```

This function takes a column (field) number, and returns the field name at that location (field numbering starts at 1):

```
$fieldname = odbc_field_name($result_id, $field_number);
```

# odbc_field_num()

```
int odbc_field_num(int result_id, string field_name)
```

This is the opposite to odbc_field_name(), instead taking a column name and returning the number (field numbering starts at 1):

```
$fieldnum = odbc_field_num($result_id, 'myfield');
```

# odbc_field_type()

```
string odbc_field_type(int result_id, int field_number)
```

This function takes a column number and returns the data type of the column (field numbering starts at 1):

```
$data_type = odbc_field_type($result_id, $field_number);
```