

OpenLink software, the maintainer of iODBC, provides free and non-expiring downloads of drivers for most platforms. Select the appropriate driver for your platform at http://www.openlinksw.com/ and install it in your test environment. OpenLink also provides free support if you require assistance.

The DSN setup under Linux will occur in the .odbc.ini file, typically installed in the bin/ directory of your driver, although you can put it anywhere. .odbc.ini is a text file with a set of parameters corresponding to the database and driver connection parameters. This list will typically contain Host, Driver, Database, UserName, Password, and ServerType, and may contain other directives specific to driver tuning parameters, for example FetchBufferSize.

The DSN parameters should all be fairly self-explanatory. Driver should point to the actual driver binary, and ServerType should be set to a value recognizable by your driver according to its documentation, for example "SQL Server 2000".

The last, and very important bit of connecting from *nix is your environment variables. You will need to know the values for LD_LIBRARY_PATH as mentioned in the iODBC installation section, as well as ODBCINI and ODBCINSTINI. ODBCINI should point to your .odbc.ini file, and ODBCINSTINI should point to your driver manager setup file, otherwise known as .odbcinst.ini, typically located in the bin/ directory of your ODBC installation.

odbc test is a sample application that ships with iODBC; it can be used to verify the successful configuration of your ODBC DSN before using it with PHP. Ensure that the three environment variables mentioned above are all set:

```
export ODBCINI="/path/to/your/odbc.ini"
```

You may verify that the environment variable is set with an echo command:

```
echo ODBCINI
```

Once you have verified that all your environment variables are set, run the odbc test application, in the .odbc sdk/examples/ directory of your iODBC installation, and pass it a "?" to see the configured DSNs:

```
./odbc test
```

This program shows an interactive SQL processor
Enter ODBC connect string (? shows list): ?

| DSN | Description |
|-----|-------------|
| OpenLink | OpenLink Generic ODBC Driver |

Enter ODBC connect string (? shows list):

If no DSNs show up, and you are sure you have configured DSNs in .odbc.ini, then you must not have set the ODBCINI environment variable properly. Check it is pointing at the correct .odbc.ini file with your echo command.

If you do show a DSN, you may select it with the syntax "DSN=DSN_NAME". A successful connection at this point will bring you to a query prompt:

```
SQL>
```

## Using MS Access

The prerequisites for connecting with MS Access under Windows are identical to those for SQL Server; ensure you have a working MS Access database. Also check for an installed MS driver for Access and create a system DSN.

Under Linux the connection prerequisites are also the same, although the DSN setup is a bit tricky. The main difference between Access connections from Linux and SQL Server connections from Linux is that there is no Access driver available. To effect this connection you will need to use the OpenLink multi-tier ODBC driver. Download it from the OpenLink site, selecting your client (Linux), server (Windows), and database (MS Access) appropriately. This will provide you with an installed "ODBC Agent" on Windows, which can bind to an existing DSN instead of directly to a database.

To enable that binding, you will need to set up two DSNs:

- Set up and test your DSN under Windows as if it were a local connection, using the MS driver for Access
- Set up your DSN under Linux in odbc.ini, but this time pass some altered values in as parameters of the DSN:
  - Hostname = [IP address of Windows server]
  - ServerType = ODBC
  - Database = [the name of the DSN you created in the first step above]
  - All other parameters as expected (UserName, Password, and so on)

You should also be able to test this local Linux DSN with odbctest as per the SQL Server example above.

## Making the Connection

Regardless of platform, database, and ODBC driver, ODBC connections from PHP will look pretty much the same. That's the beauty of ODBC.

The one minor difference is that *nix based platforms will require you to set environment variables. I find it easiest to create a separate file for this, and require it in all my scripts that will use ODBC.

Let's create the file specifying the environment variables necessary for *nix based PHP platforms (which is unnecessary if these are already set). Open your text editor and create a file called db_env.php with the following contents. Edit your values as appropriate:

```php
<?php
putenv("ODBCINI=/home/openlink/bin/odbc.ini");
putenv("ODBCINSTINI=/home/openlink/bin/odbcinst.ini");
putenv("LD_LIBRARY_PATH=/usr/local/src/odbcsdk/lib");
?>
```

Then, create a file called direct_exec.php to test your connection:

```php
<?php
require("db_env.php");

$dsn = "Northwind"; // this is a valid DSN in odbc.ini, tested in odbctest
$user = "sa"; // a UserName in the DSN will override this.
$password = ""; //a Password in the DSN will override this.
$table = "Orders"; //a standard table in the Northwind schema

$sql = "SELECT * FROM $table";

if ($conn_id = odbc_connect($dsn, $user, $password)) {
    echo("connected to DSN: $dsn <br>");
    if ($result = odbc_exec($conn_id, $sql)) {
        echo("executing '$sql' <br>");
        echo("Results: ");
        odbc_result_all($result);
        echo("freeing result <br>");
        odbc_free_result($result);
    } else {
        echo("cannot execute '$sql' ");
        odbc_error();
    }
    echo("closing connection $conn_id <br>");
    odbc_close($conn_id);
} else {
    echo("cannot connect to DSN: $dsn ");
}
?>
```

You will want to edit the values for your specific tables and DSNs.

The example above would be for Linux. To use the same file to test the ODBC connection on Windows, don't bother creating the db_env.php file and comment out the require line:

```
//require ("db_env.php");
```

Here's an alternative example, using odbc_prepare() and odbc_execute(). You will remember from the function overview that odbc_prepare() is used to set up a SQL statement for later execution. First, let's prepare:

```php
<?php
require("db_env.php"); //necessary *nix environment variables

$dsn = "Northwind"; // this is a valid DSN in odbc.ini, tested in odbctest
$user = "sa"; // a UserName in the DSN will override this.
$password = ""; //a Password in the DSN will override this.

//This is the SQL statement that will be precompiled in the database.
$sql = "SELECT * FROM Orders WHERE OrderID = ?";

//Displaying verification of database connection; not really
//necessary but great for debugging!

if ($conn_id = odbc_connect($dsn, $user, $password)) {
echo("connected to DSN: $dsn <br>");

//Check if the result came back true for the statement preparation
if ($result = odbc_prepare($conn_id, $sql))
echo("Statement prepared<br>");
```

Now that the SQL statement is prepared in the database, we can pass parameters in an array. These are substituted for the "?" in the SQL statement:

```php
$bound_param = array(10248, 10249);
if (odbc_execute($result, $bound_param)) {
 echo("executing &nbsp; $sql<br>");
 if ($num_fields = odbc_num_fields($result) > 0) {
 odbc_result_all($result);
 } else {
 echo("no fields returned.");
 odbc_error();
 }
 }
echo("closing connection $conn_id <br>");
odbc_close($conn_id);
} else {
echo("cannot connect to DSN: $dsn ");
}
?>
```

Subsequent statements may be executed by running additional odbc_execute() statements.

## Database Abstraction

Beyond the conceptual database abstraction of ODBC, there have been several approaches taken in PHP to further shield the PHP developer from the vagaries of different databases. As we saw in the previous chapters, it's entirely possible to roll your own database abstraction layer. While a thorough treatment of the existing approaches is out of the scope of this book, it's fitting to mention the PHP level approaches that already exist.

## Unified ODBC

This is a series of functions in PHP that mimic ODBC conceptually. It's important to note that unless you are actually using an ODBC DSN and driver, that you are not using the ODBC API. What the Unified ODBC functions do is borrow the semantics of the ODBC functions and wrap the native database calls in the ODBC function names. Databases supported via this method include Adabas, DB2, Solid, and Sybase.

Configuring PHP support (under *nix) for a specific database using Unified ODBC requires specifying that specific database in your PHP configure. For example, the configure option for DB2 is --with-ibm-db2=path/to/db2/install/directory. This requires the DB2 client to be installed, as the Unified ODBC functions require the database specific clients to be installed, unlike ODBC.

