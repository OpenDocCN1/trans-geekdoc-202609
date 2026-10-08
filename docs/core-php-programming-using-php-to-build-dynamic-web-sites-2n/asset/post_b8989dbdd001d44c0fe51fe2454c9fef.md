
# Core PHP Programming

## array ocierror(integer identifier)

If an error has occurred, the ocierror function returns an associative array that describes it. If no error has occurred, FALSE is returned. the identifier argument may be either a statement identifier or a connection identifier. The returned array will have two elements, code and message. You may also call ocierror with no argument to get information about a failed login. See ocifetch for an example of use.

## boolean ociexute(integer statement, integer mode)

Use ociexute to execute a statement. The mode argument is optional. It controls whether the statement will be committed after execution. By default, OCI_COMMIT_ON_SUCCESS is used. If you do not wish to commit the transaction immediately, use OCI_DEFAULT. See ocifetch for an example of use.

## boolean ocifetch(integer statement)

The ocifetch prepares the next row of data to be read with ociresult. When no rows remain, FALSE is returned.

```php
<?
//connect to database
$Connection = ocilogon("scott", "tiger");
//assemble query
$Query = "SELECT ";
$Query .= "FROM emp";
//parse query
$Statement = ocparse($Connection, $Query);
//execute query
ociexute($Statement);
//check that the query executed succesfully
if($Error = ocierror($Statement))
{
    print($Error["code"] . ": " . $Error["message"] . "<BR\n");
    exit;
}
//start HTML table
print("<TABLE\n");
//builder headers from column information
print("<TR\n");
for($i=1; $i <= ocincols($Statement); $i++)

print("<TH>");
print("a line like <THENAME VARCHAR2(10)</TH>");
print(ocicolumnname($Statement, $i) . " ");
print(ocicolumntype($Statement, $i));
print(" " . ocicolumnsize($Statement, $i) . ")");

print("<TR>\n");

//fetch row
while(ocifetch($Statement))
{
    print("<TR\n");

    //loop over each column
    for($i=1; $i <= ocicolumns($Statement); $i++)
    {
        print("a line like <TD>SMITH</TD>");
        print("<TD>");
        if(ocicolumnnull($Statement, $i))
        {
            print("(null)");
        }
        else
        {
            print(ocicresult($Statement, $i));
        }
        print("/TD>\n");
    }

    print("<TR>\n");
}

//close table
print("<table>\n");

//free statement
ocifreestatement($Statement);

//close connection
ocilogoff($Connection);

?>
```

## boolean ocifetchinto(integer statement, reference data, integer mode)

Use ocifetchinto to get the next row of data from an executed statement and place it in an array. The data argument will contain an array that by default be indexed by integers starting with 1. The option argument controls how the array is indexed. You may add the constants listed in Table 13.10 to get the features you desire.

| Constant | Description |
|---|---|
| OCI_ASSOC | Return columns indexed by name |
| OCI_NUM | Return columns indexed by number |
| OCI_RETURN_NULLS | Create elements for null columns |
| OCI_RETURN_LOBS | Return values of LOBs instead of descriptors |

```php
// connect to database
$Connection = ocilog("scott", "tiger");

// assemble query
$Query = "SELECT * ";
$Query .= "FROM emp";

// parse query
$Statement = ociparse($Connection, $Query);

// execute query
ociexecute($Statement);

// check that the query executed succesfully
if($Error = ocierror($Statement))
{
    print($Error["code"] . ": " . $Error["message"]);
    print("<BR\n");
    exit();
}

// start HTML table
print("<TABLE\n");

// fetch each row
while(ocifetchinto($Statement, $Data, 
OCI_NUM + OCI_RETURN_NULLS + OCI_RETURN_LOBS))
{
    print("<TR\n");

    // loop over each column
    while (list($key, $value) = each($Data))
    {
        print("<TD>SMITH</TD>\n");
        print("<TD>$value</TD>\n");
    }

    print("</TR\n");
}

// close table
print("</TABLE\n");

// free the statement
ocifreestatement($Statement);

//close connection
ocilogoff($Connection);
?>
```

## integer ocifetchstatement(integer statement, reference data)

ocifetchstatement fills an array with all the result data in the data argument and returns the number of rows. data array is indexed by the names of the columns. Each element is an array itself which is indexed by integers starting with zero. Each element in this subarray corresponds to a row.

```php
<?
//connect to database
$Connection = ocilogon("scott", "tiger");

//assemble query
$Query = "SELECT * ";
$Query .= " FROM emp";

//parse query
$Statement = ociparse($Connection, $Query);

//execute query
ocieecute($Statement);

print("<TABLE\n");

//fetch all rows into array
if ($Rows = ocifetchstatement($Statement, &$Data)) {
	while(list($key, $value) = each($Data)) {
		print("<TR\n");
		//name of column
		print("<TH>$key</TH\n");

		//print data
		for($i=0; $i < $Rows; $i++) {
			print("<TD>$value[$i]</TD\n");
		}
		print("</TR\n");
	}
	}

print("</TABLE\n");

//free the statement
ocifcfreestatement($Statement);

//close connection
ocicologoff($Connection);
?>
```

## boolean ocifreecursor(integer cursor)

Use ocifreecursor to free the memory associated with a cursor you created.

## boolean ocifestatement(integer statement)

Use ocfreestatement to free the memory associated with a statement. The statement argument is returned by ociparse.

## boolean ocidebug(on)

The ocidebug function controls whether debugging information is generated. The debug output will be sent to the browser. It is off by default.

## boolean ocilogoff(integer connection)

Use ocilogoff to close a connection.

## integer ocilogon(string user, string password, string sid)

The ocilogon function establishes a unique connection to an Oracle database. The identifier is used to create statements, cursors, and descriptors. The user and password arguments are required. The optional sid argument specifies the server, and if left out, the ORACLE_SID environment variable will be used.

## integer ocinewcursor(integer connection)

Use ocinewcursor to create a cursor. The cursor identifier that returned is similar to a statement identifier.

```php
//open connection
```

```
$Cursor = ocinewcursor($Connection);

//create statement that calls a stored procedure
$Query = "BEGIN "
$Query = "docalculation(:price); "
$Query = "END";
$Statement = ociparse($Connection, $Query);

//bind placeholder to cursor
ocibindbyname($Statement, "price", &$Cursor, -1, OCI_B_CURSOR);

//execute statement
ociexute($Statement);

//execute cursor
ociexute($Cursor);

//loop over results in cursor
while (ocifetchinto($Cursor, &$Results)) {
    print("$Results<BR>\n");
}

//free memory for cursor
ocifrecursor($Cursor);

//free memory for statement
ocifreestatement($Statement);

//close connection
ocilogoff($Connection);
```

## integer ocinumcols(integer statement)
