# # odbc_field_len() and odbc_field_precision()

```
int odbc_field_len(int result_id, int field_number)
string odbc_field_precision(int result_id, int field_number)
```

These functions are synonymous; both take a column number and return the length, or precision, of that column (field numbering starts at 1):

```
$length = odbc_field_len($result_id, $field_number);
```

Precision refers to the length of the datatype defined for that column, for example VARCHAR(255) has a precision of 255.

# # odbc_tables()

```
int odbc_tables(int connection_id [, string qualifier [, string owner [, string name [, string types]]]])
```

This function takes a connection id and returns a result identifier containing the tables corresponding to the parameters passed, including catalog (qualifier), owner, and name.

The resultset has the following columns:

+   - [ ] TABLE_QUALIFIER
+   - [ ] TABLE_OWNER
+   - [ ] TABLE_NAME
+   - [ ] TABLE_TYPE
+   - [ ] REMARKS

The resultset is ordered by TABLE_TYPE, TABLE_QUALIFIER, TABLE_OWNER, and TABLE_NAME.

The owner and name arguments may be passed in with wildcards: "%" for multiple characters and "_" to match a single character.

# # odbc_columns()

```
int odbc_columns(int connection_id [, string qualifier [, string owner [, string table_name [, string column_name]]]])
```

Like odbc_tables(), this function takes a connection id and returns a result identifier containing the columns corresponding to the parameters passed.

The resultset has the following columns:

+   - [ ] TABLE_QUALIFIER
+   - [ ] TABLE_OWNER
+   - [ ] TABLE_NAME