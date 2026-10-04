
# Appendix E: PHP Function Reference

imap_header_decode (string str) array Decodes MIME header element in accordance with RFC 2047 and returns array of objects containing charset encoding and decoded text

![](img/245156cc770929860a3ede93c01f9981_515_0.png)

Use of the IMAP functions requires the IMAP libraries and PHP to be installed --with-imap. The functions will work with a POP3 server as.

| Function | Returns | Action |
| --- | --- | --- |
| ibase_connect(string database [, string username] [, string password] [, string charset] [, int dialect] [, string role]) | int | Opens a connection to an InterBase database and returns a connection identifier |
| ibase_connect(string database [, string username] [, string password] [, string charset] [, int dialect] [, string role]) | int | Opens a persistent connection to an InterBase database |
| ibase_close([int link_identifier]) | int | Closes an InterBase connection |
| ibase_commit([int link_identifier,] int trans_number) | int | Commits transaction |

# Table E-31 INTERBASE FUNCTIONS (Continued)

| Function | Returns | Action |
|---|---|---|
| ibase_rollback([int link_identifier,] int trans_number) | int | Rolls back transaction |
| ibase_query([int link_identifier.] string query [. int_bind])]) | int | Executes a query |
| ibase_prepare([int link_identifier.] string query) | int | Prepares a query for later execution |
| ibase_fetch_row(int [, int blob_flag]) | array | Fetches a row from the results of a query |
| ibase_fetch_object(int result [, int blob_flag]) | object | Fetches an object from the results of a query |
| ibase_free_result(int result) | int | Frees the memory used by a result |
| ibase_execute(int query [, int bind_args int ...]) | int | Executes a previously prepared query |
| ibase_free_query(int query) | int | Frees memory used by a query |
| ibase_timefmt(string format) | int | Sets the format of timestamp, date, and time columns returned from queries |
| ibase_num_fields(int result) | int | Gets the number of fields in result |
| ibase_field_info(int result, int field_number) | array | Gets information about a field |
| ibase_blob_add(int blob_id, string data) | int | Adds data into created blob |

PHP must be installed --with-ibase in order for these functions to work. Please check the current documentation on PHP interbase functions, because as of the time of this writing, this API was under a lot of flux.

![](img/245156cc770929860a3ede93c01f9981_516_0.png)

# Appendix E: PHP Function Reference

## Table E-32 MHASH FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| mhash_count() | int | Gets the number of available hashes |
| mhash_get_block_size(int hash) | int | Gets the block size of hash |
| mhash_get_hash_name(int hash) | string | Gets the name of hash |
| mhash(int hash, string data) | string | Computes hash function on data, using the hash in the first argument |

![](img/245156cc770929860a3ede93c01f9981_517_0.png)

Use of these functions requires the mhash library from http://mhash.sourceforge.net/. PHP must be compiled --with-mash.

The mSQL database is another open-source SQL database server. It is not actively maintained and has some limitations that make it a poor choice compared to MySQL, PostgreSQL, or Interbase. Note that msqp and MySQL have almost identical function sets.

## Table E-33 MSQL FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| msql_connect([string hostname[:port]], . string username [, string password]) | int | Opens a connection to an mSQL Server |
| msql_pconnect([string hostname[:port]], . string username [, string password]) | int | Opens a persistent connection to an mSQL Server |

# Table E-33 MSQL FUNCTIONS (Continued)

| Function | Returns | Action |
| --- | --- | --- |
| msql_close([int link_identifier]) | int | Closes an MSQL connection |
| msql_select_db(string database_name [, int link_identifier]) | int | Selects an MSQL database |
| msql_create_db(string database_name [, int link_identifier]) | int | Creates an MSQL database |
| msql_drop_db(string database_name [, int link_identifier]) | | Drops (deletes) an MSQL database |
| msql_query(string [, int link_identifier]) | int | Sends an SQL query to MSQL |
| msql_list_dbs([int link_identifier]) | int | Lists databases available on an MSQL server |
| msql_list_tables(int link_identifier) | int | Lists databases available on an MSQL server |
| msql_list_tables(string database_name [, int link_identifier]) | int | Lists tables available on an MSQL server |
| msql_error([int link_identifier]) | string | Returns the error message from the MSQL server |
| msql_result(int query [, mixed]) | int | Gets result data |
| msql_num_rows(int query) | int | Gets number of rows |
| msql_num_fields(int query) | int | Gets number of fields |
| msql_fetch_row(int query) | array | Returns a row as array |
| msql_fetch_object(int query [, int type]) | object | Fetches a row as object |
| msql_fetch_array(int query [, int type]) | array | Fetches a row as associative array |

# Appendix E: PHP Function Reference

| Function | Returns | Action |
| --- | --- | --- |
| msql_data_seek(int result, int offset) | int | Moves internal row pointer |
| msql_fetch_field(int result_id [, int offset]) | object | Gets information about a certain field in a query result |
| msql_field_seek(int query, int offset) | int | Sets result pointer to specific row |
| msql_field_name(int result_id, int offset) | string | Gets the name of the specified field |
| msql_field_table(int query, int offset) | string | Gets table name of specified field |
| msql_field_length(int result_id [, int offset]) | int | Gets the length of a MS-SQL field |
| msql_field_type(int query, int offset) | string | Gets the type of the specified field |
| msql_field_flags(int query, int offset) | string | Gets flags associated with the specified field |
| msql_free_result(int query) | int | Frees result |
| msql_affected_rows(int query) | int | Returns number of affected rows |

## TABLE-34 MSSQL FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| msql_connect([string hostname[:port]], string username [, string password]) | int | Establishes a connection to an mSQL server, returns a connection identifier |
| msql_pconnect([string hostname[:port]], string username [, string password]) | int | Establishes a persistent connection to an mSQL server |
| msql_close([int link_identifier]) | int | Closes a connection to a MSQL server |
| msql_select_db(string database_name [, int link_identifier]) | int | Selects an MSQL database |
| msql_query(string [, int link_identifier]) | int | Performs an SQL query on a MSQL server database |
| msql_free_result(string result_index) | int | Frees a MSQL result index |
| msql_get_last_message(void) | string | Gets the last message from the MSQL server |
| msql_num_rows(int msql_result_index) | int | Returns the number of rows fetched from the result ID |
| msql_num_fields(int msql_result_index) | int | Returns the number of fields fetched in the result ID |
| msql_fetch_row(int result_id) | array | Returns an array of the current row in the result set specified by result_id |
| msql_fetch_object(int result_id) | object | Gets an object of the current row in the result set specified by result_id |
| msql_fetch_array(int result_id) | array | Returns an associative array of the current row in the result set specified by result_id |
| msql_data_seek(int result_id, int offset) | int | Moves the internal row pointer of the MS-SQL result associated with the specified identifier to pointer to the specified row number |
