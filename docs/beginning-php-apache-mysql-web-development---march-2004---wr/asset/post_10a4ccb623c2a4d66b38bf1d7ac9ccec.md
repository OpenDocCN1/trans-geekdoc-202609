
## Appendix C

## Mathematical Functions

These functions allow you to perform mathematical calculations on your data while still in the PHP code.

| Function | Description |
| --- | --- |
| abs (number) | Calculates the absolute value of a number. |
| acos (argument) | Calculates the arc cosine in radians. |
| asin (argument) | Calculates the arc sine in radians. |
| atan (argument) | Calculates the arc tangent in radians. |
| atan2 (x, y) | Calculates the arc tangent of x and y. |
| base_convert (number, startbase, embedbase) | Converts a number based on the named parameters. |
| bindec (binary_string) | Converts a binary string to a decimal, opposite of decbin. |
| ceil (number) | Rounds fractions to next integer. |
| cos (argument) | Calculates the cosine in radians. |
| decbin (number) | Converts a decimal to a binary string, opposite of decbin. |
| dehex (number) | Converts a decimal to hexadecimal, opposite of hexdec. |
| decoct (number) | Converts a decimal to octal, opposite of octdec. |
| deg2rad (number) | Calculates degrees to radian, opposite of rad2deg. |
| exp (argument) | Calculates e to the powered number. |
| floor (number) | Rounds fractions down to next lowest integer. |
| getrandmax () | Calculates the maximum random value from the rand function. |
| hexdec (hex_string) | Converts hexadecimal to decimal, opposite of dechex. |
| lcg_value () | Calculates a pseudo random number between 0 and 1. |
| log (argument) | Calculates the natural log. |
| log10 (argument) | Calculates the base 10 log. |
| max (num1, num2, ... ) | Calculates the maximum of listed values. |
| min (num1, num2, ... ) | Calculates the minimum of listed values. |
| mt_getrandmax () | Calculates the maximum random value from the mt_rand function. |
| mt_rand ([min, max]) | Generates a Mersenne Twister random value. |
| mt_srand (seed) | Seeds the Mersenne Twister random generator. |
| Function | Description |
| --- | --- |
| number_format(number, dec_places, dec_point, thousands) | Formats the number based on the named parameters. |
| octdec(octal_string) | Converts octal to decimal, opposite of decoct. |
| pi() | Returns pi. |
| pow(number, exp) | Calculates named number to the power of exponent. |
| rad2deg(number) | Converts radians to decimal, opposite of deg2rad. |
| rand([min, max]) | Generates a random integer based on named parameters if applicable. |
| round(number, [precision]) | Rounds the named number to the nearest integer. |
| sin(argument) | Calculates the sine in radians. |
| sqrt(argument) | Calculates the square root. |
| srand() | Seeds the random number generator. |
| tan(argument) | Calculates the tangent in radians. |

## Miscellaneous Functions

The table that follows lists useful functions that don't fit anywhere else.

| Function | Description |
| --- | --- |
| connection_aborted() | Verifies whether or not the client connection has been aborted. |
| connection_status() | Verifies the client connection status. |
| connection_timeout() | Verifies whether or not the script has timed out. |
| constant(name) | Returns the value of the named constant. |
| define(name, value, case_insensitive) | Defines a constant based on the named parameters. |
| defined(name) | Verifies whether or not a named constant exists. |
| die(message) | Displays the message and ends execution of the script. |
| eval(string) | Evaluates the named string as PHP code. |
| exit() | Ends execution of the script. |

Table continued on following page

## Appendix C

| Function | Description |
|---||---|
| get_browser([user agent]) | Returns information about the user's browser. |
| highlight_file(filename) | Displays a highlighted version of the named file. |
| highlight_string(str) | Displays a highlighted version of the named string. |
| ignore_user_abort({setting}) | Allows a script to continue executing if the user alerts a connection. |
| iptcparse(iptblock) | Parses the IPTC block into an array. |
| leak(bytes) | Leaks the named amount of memory. |
| pack(format, arg1, arg2... ) | Packs the named arguments into a binary string. |
| show_source(filename) | Displays a highlighted version of source code of named file. |
| sleep(seconds) | Pauses execution of the script for named number of seconds |
| uniqid(prefix, lcg) | Assigns a unique ID based on the current time and named prefix. |
| unpack(format, data) | Opposite of pack, unpacks binary data into an array. |
| usleep(microseconds) | Pauses execution of the script for named number of microseconds. |

## MySQL Functions

The following table lists the PHP functions that can be used with your MySQL server for added functionality in your PHP script.

| Function | Description |
|---||---|
| mysql_affected_rows([link_id]) | Returns the number of rows of records affected by the previous command. |
| mysql_change_user(user, pass[, database, link_id]) | Changes the user for the active database connection. |
| mysql_close([link_id]) | Closes the active connection. |
| mysql_connect([hostname]:[port] [/path/to/socket], username, password) | Opens the connection to the server based on the named parameters. Similar to mysql_pconnect. |
| mysql_create_db(database, [link_id]) | Creates a database. |
| mysql_data_seek(result_id, row_number) | Moves to the named row of the results. |
| mysql_db_name(result, row, [field]) | Gets data for result. |
| mysql_db_query(database, query[, link_id]) | Executes the named query on the named database and returns results. |

| Function | Description |
|---||---|
| mysql_drop_db(database[, link_id]) | Erases the named database. |
| mysql_errno([link_id]) | Displays the error number. |
| mysql_error([link_id]) | Displays the error message. |
| mysql_escape_string(string) | Escapes a string to be used in the query. |
| mysql_fetch_array(result) | Obtains the array from the result. |
| mysql_fetch_field(result[, offset]) | Fetches the field from the result. |
| mysql_fetch_object(result[, type]) | Obtains the object from the result. |
| mysql_fetch_row(result) | Obtains the row from the result. |
| mysql_field_flags(result) | Displays the flag of the field. |
| mysql_field_len(result) | Returns the length of the field. |
| mysql_field_name(result, index) | Returns the name of the field. |
| mysql_field_seek(result, offset) | Moves to the named row of the results. |
| mysql_field_type(result) | Displays the type of the field. |
| mysql_free_result(result) | Frees any memory used by the result. |
| mysql_get_client_info() | Returns the client information. |
| mysql_get_host_info([link_id]) | Returns information about the host. |
| mysql_get_proto_info([link_id]) | Returns the protocol. |
| mysql_get_server_info([link_id]) | Returns information about the server. |
| mysql_info([link_id]) | Gets information about the previous query. |
| mysql_insert_id([link_id]) | Returns the ID value of the most inserted auto_increment. |
| mysql_list_dbs([link_id]) | Lists the databases on the MySQL server. |

Table continued on following page

## Appendix C

| Function | Description |
| --- | --- |
| mysql_list_fields(database, table[, link_id]) | Lists the fields in the database and table. |
| mysql_list_processes([link_id]) | Lists the processes. |
| mysql_list_tables(database) | Lists the tables in the database. |
| mysql_num_fields(result) | Shows the number of fields in the result. |
| mysql_num_rows(result) | Shows the number of rows in the result. |
| mysql_pconnect(...) | Opens a persistent connection to the server. |
| mysql_ping([link_id]) | Pings the server connection to verify it is working. |
| mysql_query(query[, link_id]) | Executes the query. |
| mysql_real_escape_string(string[, link_id]) | Escapes a string to be used in the query. |
| mysql_result(result, row, field]) | Gets the data located in the named field/row. |
| mysql_select_db(database[, link_id]) | Selects the database and makes it current. |
| mysql_stat([link_id]) | Gets current system status. |
| mysql_thread_id([link_id]) | Returns current connection thread. |
| mysql_tablename(result, index) | Returns the table from which the result was obtained. |
| mysql_unbuffered_query(query[, link_id]) | Queries the MySQL server without fetching and buffering the results. |

## Network Functions

The functions in the table follows can be used to communicate with your network directly from PHP.

| Function | Description |
| --- | --- |
| checkdnsr(host[, type]) | Equal to dns_check_record, searches for DNS records based on the named parameters. |
| closelog() | Closes connection to the system log, opposite of openlog. |
