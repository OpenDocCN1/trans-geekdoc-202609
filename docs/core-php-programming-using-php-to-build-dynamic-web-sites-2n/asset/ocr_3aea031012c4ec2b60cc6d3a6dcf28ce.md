# Core PHP Programming

```
//close connection
ocilogoff($Connection);
?>
```

# integer ocifetchstatement(integer statement, reference data)

ocifetchstatement fills an array with all the result data in the data argument and returns the number of rows. data array is indexed by the names of the columns. Each element is an array itself which is indexed by integers starting with zero. Each element in this subarray corresponds to a row.

```
?
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
if ($Rows = ocifetchstatement($Statement, &&$Data)) {
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
```

IT-SC book 425