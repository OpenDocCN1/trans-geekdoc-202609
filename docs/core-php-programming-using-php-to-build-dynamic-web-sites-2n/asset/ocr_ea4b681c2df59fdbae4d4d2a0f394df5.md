# Core PHP Programming

```
<?
//connect to database
$db = dbase_open("customer.dbbf", 2);

//get some information about database
$numRecords = dbase_numrecords($db);
$numFields = dbase_numfields($db);

// get every record
for($index=1; $index=$numRecords; $index++)
{
    //get a record
    $record = dbase_get_record($db, $index);

    print("<H3>Record $index</H3>\n");

    //loop over fields
    for($index=0; $index=$numFields; $index++)
{
        print("<B>Field $index2</B>");
        print($record[$index2]);
        print("<BR>\n");
    }

    //print deletion status
    print("<B>Deleted:/B> ");
    print($record["deleted"]);
    print("<BR>\n");
}

//close connection
dbase_close($db);
?
```

# array dbase_get_record_with_names(integer database, integer record)

This function behaves like dbase_get_record, except instead of being indexed integers, fields are indexed by their names.

```
<?
//connect to database
$db = dbase_open("customer.dbbf", 2);

// get every record
for($index=1; $index=dbase_numrecords($db); $index++)
{
    $record = dbase_get_record_with_names($db, $index);
    print("<H3>Record $index</H3>\n");
}
```