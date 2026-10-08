# Core PHP Programming

Excel workbooks. A good place to start learning about ODBC is Microsoft's page at <http://www.microsoft.com/data/odbc/>.

Microsoft has offered free ODBC drivers for some time, but only for their operating systems. ODBC drivers for UNIX are harder to come. Most database manufacturers offer drivers, and there are third parties, like Intersol, that optimized drivers for both Windows and UNIX platforms.

Most of the database with native support in PHP can also be accessed via ODBC. There are numerous databases that can be accessed viaODBC by PHP. Two that others have tried are Solid and Empress.

Stig Bakken, Andreas Karajannis and Frank Kromann have contributed to the creation of the ODBC extension.

# boolean_autocommit(integer connection, boolean on)

The odc_autocommit function sets whether queries are automatically committed when executed. The connection argument is an integer returned by the ods_connect or odc_pconnect functions. This function has to be used intelligently, as not all ODBC drivers support commits and rollbacks.

```
<?
$Connection = ODBC_connect("store", "sa", "sa");

// turn off autocommit
odbc_autocommit($Connection, FALSE);
?>
```

# boolean_binmode(integer result, integer mode)

Use odc_binmode set the binary columns return data for a result set. When binary data are returned by the driver, each byte is represented by hexadecimal codes. By default, PHP will convert these codes into raw binary data. If you have to use the odc_longreadlen set the maximum length of long data to anything other than zero, then the modes in Table 13.8 apply. If the maximum read length is zero, the data are converted to raw binary data.

```
<?
// get a GIF from a database and send it to browser

// connect to database
$Connection = odc_connect("store", "admin", "secret");

// execute query
$Query = "SELECT picture";
```