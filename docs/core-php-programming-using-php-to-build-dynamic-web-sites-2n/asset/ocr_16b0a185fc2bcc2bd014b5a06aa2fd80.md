# Core PHP Programming

# array ocierror(integer identifier)

If an error has occurred, the ocierror function returns an associative array that describes it. If no error has occurred, FALSE is returned. the identifier argument may be either a statement identifier or a connection identifier. The returned array will have two elements, code and message. You may also call ocierror with no argument to get information about a failed login. See ocifetch for an example of use.

# boolean ociexute(integer statement, integer mode)

Use ociexute to execute a statement. The mode argument is optional. It controls whether the statement will be committed after execution. By default, OCI_COMMIT_ON_SUCCESS is used. If you do not wish to commit the transaction immediately, use OCI_DEFAULT. See ocifetch for an example of use.

# boolean ocifetch(integer statement)

The ocifetch prepares the next row of data to be read with ociresult. When no rows remain, FALSE is returned.

```
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
for($i=1; $i = ocincols($Statement); $i++)

```

IT-SC book 422