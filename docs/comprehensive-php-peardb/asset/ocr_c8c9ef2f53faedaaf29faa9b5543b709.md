```
```text
[2] => Schwendiman

Array
(
    [0] => 2
    [1] => Jeffrey
    [2] => Cox
)

Array
(
    [0] => 3
    [1] => Kate
    [2] => McNulty
)
```
```

# Output 8: Output when setFetchMode is DB_FETCHMODE_ORDERED

As can be seen from the printed information in Output 8, each call to DB_result::fetchRow() with the fetchmode set to DB_FETCHMODE_ORDERED results in an indexed array in which the indexes represent column numbers in the result dataset. The columns are ordered in the same way as the original SELECT query.

The code in Code Listing 22 and the output in Output 9 illustrate the effects of using the DB_FETCHMODE_ASSOC fetchmode.

```
```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        false );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $sSQL = 'select id, first_name, last_name from
        Employees limit 3';
        $oRows = $oDB->query( $sSQL );

        if ( !DB::isError( $oRows ) )
        {
            while ( $aData = $oRows->fetchRow() )
            {
                print( '<pre>' );
                print_r( $aData );
```
```