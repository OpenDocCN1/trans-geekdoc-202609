# Comprehensive PHP PEAR::DB

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| odbc | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ |
| pgsql | ☑ | ☑ | ☐ | ☐ | ☑ | ☑ | ☑ |
| sqlite | ☑ | ☐ | ☑ | ☑ | ☐ | ☐ | ☐ |
| sybase | ☑ | ☑ | ☐ | ☐ | ☐ | ☐ | ☐ |
| dbase | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ |

**Table 7: Types supported in getSpecialQuery for each database back end.**

```
```php
<?php
    require_once ( 'DB.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( DB::isConnection( $oDB ) )
    {
        print( 'Tables:<ol>' );
        $result = $oDB->getListOf( 'tables' );
        if ( !DB::isError( $result ) )
        {
            foreach ( $result as $aValue )
                print( "<li>$aValue</li>" );
        }
        print( '</ol>' );

        print( 'Users:<ol>' );
        $result = $oDB->getListOf( 'users' );
        if ( !DB::isError( $result ) )
        {
            foreach ( $result as $aValue )
                print( "<li>$aValue</li>" );
        }
        print( '</ol>' );

        print( 'Databases:<ol>' );
        $result = $oDB->getListOf( 'databases' );
        if ( !DB::isError( $result ) )
        {
            foreach ( $result as $aValue )
                print( "<li>$aValue</li>" );
        }
        print( '</ol>' );

        $oDB->disconnect();
    }
?>
```
```