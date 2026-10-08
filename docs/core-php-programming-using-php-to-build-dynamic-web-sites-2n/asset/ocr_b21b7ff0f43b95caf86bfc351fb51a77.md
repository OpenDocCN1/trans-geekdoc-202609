# Core PHP Programming

The ifx_fieldtypes function returns an array describing the type for eachcolumn in the result set. Possible values are SQLBODY, SQLBYTES, SQLCHAR, SQLDATE, SQLDECIMAL, SQLTIME, SQLFLOAT, SQLINT, SQLINT8, SQLINTERVAL, SQLLVARCHAR, SQLMONEY, SQLNCHAR, SQLVARCHAR, SQLSERIAL, SQLSERIAL8, SQLMFLOAT, SQLMININT, SQLTEXT, SQLUDTFIXED, SQLVARCHAR. The returned array is indexed by the names of the columns.

# boolean ifx_free_blob(integer blob)

The ifx_free_blob function deletes the specified blob from the database.

# boolean ifx_free_char(integer character)

The ifx_free_char function deletes a character object from the database.

# boolean ifx_free_result(integer result)

The ifx_free_result function frees memory associated with a result set. See ifx_pconnect for an example of use.

# string ifx_get_blob(integer blob)

The ifx_get_blob function returns the contents of a blob.

# string ifx_get_char(integer character)

The ifx_get_char function returns the contents of a character object.

# array ifx_getqlca(integer result)

The ifx_getqlca returns an array of the values in the sqlerd struct from the underlying Inform API.

# integer ifx_htmltbl_result(integer result, string options)

The ifx_htmltbl_result function prints an HTML table containing all the rows in the result set. The optional options argument will be placed inside the table tag. See ifx_pconnect for an example of use.

# boolean ifx_nullformat(integer mode)

When mode is 0, ifx_nullformat will cause all null columns to be returned as empty strings. If mode is 1, they are returned as NULL, a four-character string.

# integer ifx_num_fields(integer result)