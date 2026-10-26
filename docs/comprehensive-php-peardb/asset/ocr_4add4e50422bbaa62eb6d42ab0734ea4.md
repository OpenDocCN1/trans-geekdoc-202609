```
$sSQL = 'select id, first_name, last_name from Employees limit 3';
$oRows = $oDB->query( $sSQL, 'Employee' );
if ( !DB::isError( $oRows ) )
{
    while ( $aData = $oRows->fetchRow() )
    {
        print( '<pre>' );
        print_r( $aData );
        print( '</pre>' );
    }
    $oDB->disconnect();
}
?>
```

# Code Listing 24: DB_common::setFetchMode – DB_FETCHMODE_OBJECT using object_class parameter

```
employee Object
(
    [first_name] => Blake
    [last_name] => Schwendiman
    [id] => 1
    [full_name] => Blake Schwendiman
)
employee Object
(
    [first_name] => Jeffrey
    [last_name] => Cox
    [id] => 2
    [full_name] => Jeffrey Cox
)
employee Object
(
    [first_name] => Kate
    [last_name] => McNulty
    [id] => 3
    [full_name] => Kate McNulty
)
```

# Output 11: Output when setFetchMode is DB_FETCHMODE_OBJECT and object_class is set

While the example shown in Code Listing 24 is obviously a simple contrived example, it illustrates the fundamental power of using DB_FETCHMODE_OBJECT. The constructor of the object_class could perform any additional work required to instantiate an object representing the