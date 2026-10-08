# Core PHP Programming

The ora_getcolumn function returns the value of the column for the current row. Columns are indexed starting with zero. Long columns are limited to 64K. See ora_exec for an example of use.

# boolean ora_logoff(integer connection)

Use ora_logoff to disconnect from the database server. See ora_exec for an example of use.

# integer ora_logon(string user, string password)

The ora_logon function begins a connection with an Oracle database server. A connection identifier is returned. See ora_exec for an example of use. As at the beginning of this section, you must define environment variables that specify the server in order to make a successful connection.

# integer ora_numcols(integer cursor)

The ora_numcols function returns the number of columns for a query that has been executed. See ora_exec for an example of use.

# integer ora_numrows(integer cursor)

The ora_numrows function returns the number of rows in the result set for an executed query. See ora_exec for an example of use.

# integer ora_open(integer connection)

The ora_open function opens a cursor for the given connection. See ora_exec for an example of use.

# boolean ora_parse(integer cursor, string query)

The ora_parse function parses a query and reads it for execution. See ora_exec for an example of use.

# integer ora_plogon(string user, string password)

The ora_plogon function returns a connection identifier. A persistent connection will be created. It will last as long as the server process. Later calls to ora_logon or ora_plogon will find persistent connections and use them instead of creating new ones. Connections created with ora_plogon should not be used with ora_logoff.

# boolean ora_rollback(integer connection)