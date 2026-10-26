# DB_result::tableInfo

◆ `mixed tableInfo( mixed $mode = null )`

The **tableInfo()** method returns database structure metadata about the result object. One usage example was given in the discussion of **DB_common::tableInfo()** on page 102.

The example shown in Code Listing 58 is a more general purpose example showing the way that the **tableInfo()** metadata can be used in real applications.

```
```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );

    function dbResultToTable( $oDBResult )
    {
        $numCols = $oDBResult->numCols();

        $aMetaData = $oDBResult->tableInfo();
        print( '<table border="1">' );

        // print header row
        print( '<tr>' );
        for ( $iIndex = 0; $iIndex < $numCols; $iIndex++ )
        {
            print( '<td>' . $aMetaData[$iIndex]['name'] . '</td>' );
        }
        print( '</tr>' );

        // now print all data rows
        while ( $oData = $oDBResult->fetchRow() )
        {
            print( '<tr>' );
            for ( $iIndex = 0; $iIndex < $numCols; $iIndex++ )
            {
                print( '<td>' . $oData[$iIndex] . '</td>' );
            }
            print( '</tr>' );
        }

        print( '</table>' );
    }

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
```
```