> TIP
> 
> Using sqlite_fetch_all() reads the whole resultset into memory at once. So, if you do not have much data, this is the best-performing method. If you have more data, an iterative approach using sqlite_fetch_array() and sqlite_fetch_object() might be better.

# Connecting to PostgreSQL

# @pg_connect()

PostgreSQL has a growing fanbase. Some even say this is because the new version 8.0 finally comes in a native Windows version. However, most productive systems that use PostgreSQL are hosted on Linux or UNIX, nevertheless.

After installing the database, web-based administration software such as phpPgAdmin (http://sourceforge.net/projects/phppgadmin) or other tools such as the graphical user interface (GUI) application pgAdmin (http://www.pgadmin.org/) can be used to administer the database. Alternatively, the command-line tool can be used. To allow PHP to access the PostgreSQL installation, Windows users must load the extension with the entry extension(php_pgsql.dll) in php.ini; UNIX/Linux users configure PHP with the switch --with-pgsql=/path/to/pgsql.

Then, pg_connect() connects to the data source. You have to provide a connection string that contains all important data, including host, port, name of the database, and user credentials.